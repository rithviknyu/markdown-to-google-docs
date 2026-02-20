# Markdown → Google Docs (Colab)

A small Python/Colab project that converts markdown meeting notes into a **well-formatted Google Doc** using the **Google Docs API**.

## Features implemented
- Creates a new Google Doc programmatically (Docs API)
- Heading mapping:
  - Main title: **Heading 1**
  - Section headers: **Heading 2**
  - Sub-section headers: **Heading 3**
- Nested bullet hierarchy (indentation based on markdown indentation)
- Markdown checkboxes (`- [ ]`, `- [x]`) converted to Google Docs checkboxes
- `@mentions` styled distinctly (bold + colored)
- Footer lines (after `---`) styled distinctly (italic + smaller + gray)

## Repo layout (suggested)
```
.
├── README.md
├── notebook
│   └── markdown_to_gdocs_colab.ipynb
└── src
    └── markdown_to_gdocs.py
```

## Requirements / dependencies
- Python 3.10+ (Colab works)
- `google-api-python-client`
- `google-auth-httplib2`
- `google-auth-oauthlib`

## Run in Google Colab
1. Open `notebook/markdown_to_gdocs_colab.ipynb` in Colab
2. Run the install cell (optional)
3. Run authentication cell (`auth.authenticate_user()`), complete the Google sign-in prompt
4. Run the final cell — it prints a Google Docs URL

## Local dev (optional)
This project is designed for Colab. If you run locally, you'll need OAuth credentials (Desktop app) and an OAuth flow; Colab auth is simplest for the assessment.

## Notes on the Docs API
- Formatting is applied via `documents().batchUpdate()` requests:
  - `insertText`
  - `updateParagraphStyle`
  - `createParagraphBullets`
  - `updateTextStyle`

