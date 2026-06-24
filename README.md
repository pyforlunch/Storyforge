# StoryForge — Jira Stories from Meeting transcripts

> Turn meeting transcripts into Jira-ready user stories, action items, and bugs in seconds.

![StoryForge](https://img.shields.io/badge/version-1.0-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue)

---

## Overview

**StoryForge** is a browser-based single-page application that:

- Accepts raw meeting transcript text (paste or `.txt` file upload)
- Uses **Claude AI** to extract and classify requirements as **User Stories**, **Action Items**, or **Bugs**
- Generates User Stories in the standard agile format: *As a [persona], I want to [action] so that [end result]*
- Produces **Gherkin acceptance criteria** (Given / When / Then) where derivable
- Exports a fully-formed **Jira-compatible CSV** file (73 columns matching the Jira import schema) ready to import directly

---

## Live Demo

**GitHub Pages URL:** `https://<your-username>.github.io/ai-user-story-meetings-tool/`

No login, no server. Works fully in-browser.

---

## Features

| Feature | Description |
|---|---|
| Transcript Input | Paste text or upload `.txt` / `.text` files |
| AI Extraction | Claude Sonnet 4 classifies stories, tasks, and bugs |
| Demo Mode | Works without API key using realistic mock data |
| Inline Editing | Edit any story's summary or acceptance criteria before export |
| Delete Issues | Remove individual issues before exporting |
| CSV Export | Full 73-column Jira import CSV (`jira_stories_export.csv`) |
| Configurable | Set your own project key (e.g. SE, PROJ) and starting issue number |

---

## Project Structure

```
ai-user-story-meetings-tool/
├── index.html              # Single-page application entry point
├── src/
│   ├── app.js              # Core application logic & UI
│   ├── api.js              # Anthropic API integration
│   ├── mockData.js         # Demo mode mock data
│   ├── csvExporter.js      # Jira CSV generation (73 columns)
│   └── styles.css          # Full application styles
├── assets/
│   └── Jira_sample.csv     # Jira CSV column reference template
├── .env.example            # Example environment variables
├── .gitignore              # Git ignore rules
└── README.md               # This file
```

---

## Setup & Usage

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/ai-user-story-meetings-tool.git
cd ai-user-story-meetings-tool
```

### 2. Run locally

No build step required. Simply open `index.html` in your browser:

```bash
# macOS
open index.html

# Windows
start index.html

# Or use a local server (recommended for file: protocol compatibility)
npx serve .
# then visit http://localhost:3000
```

### 3. Use the app

1. **Page 1 – Input:** Paste your meeting transcript (up to ~15,000 characters) or upload a `.txt` file. Set your project key and starting issue number.
2. Click **"Extract Stories"** — demo mode loads instantly with mock data.
3. **Page 2 – Results:** Review, edit, or delete generated issues across three columns (User Stories, Action Items, Bugs).
4. Enter your **Anthropic API key** in the export panel to enable live AI extraction and CSV download.
5. Click **"Download CSV"** — the file `jira_stories_export.csv` is downloaded and ready to import into Jira.

---

## Anthropic API Key

To use live AI extraction:

1. Get your key at [console.anthropic.com](https://console.anthropic.com)
2. The key starts with `sk-ant-...`
3. Enter it in the export panel on Page 2

> **Security:** Your API key is never stored, logged, or committed. It is used only for the single API call in your browser session.

---

## Deploying to GitHub Pages

1. Push the repository to GitHub
2. Go to **Settings → Pages**
3. Set source to **Deploy from branch → main → / (root)**
4. Your app will be live at `https://<username>.github.io/ai-user-story-meetings-tool/`

---

## Jira CSV Import

1. In Jira, go to your project → **Project settings → Import**
2. Choose **CSV**
3. Upload `jira_stories_export.csv`
4. Map columns (the file header matches Jira's field names exactly)
5. Stories appear under your project with auto-incremented issue keys

---

## Environment Variables (Optional)

```bash
# .env.example
ANTHROPIC_API_KEY=sk-ant-your-key-here
```

For local development you can set `ANTHROPIC_API_KEY` in your environment; the app reads it if present. For GitHub Pages, the key is entered at runtime via the UI.

---

## Tech Stack

- **Vanilla HTML / CSS / JavaScript** — no build tools, no frameworks
- **Anthropic Messages API** — `claude-sonnet-4-20250514`
- **Google Fonts** — Syne (display), DM Sans (body), DM Mono (code)

---

## License

MIT © 2026
