# AltGen — AI-Powered Alt Text Generator

> Generate contextual, SEO-friendly alt text for product images using Claude AI — built for SEO executives, no coding required.

![AltGen UI](docs/preview.png)

---

## ✨ Features

- **Drag & drop CSV upload** — just drop your file, no technical steps
- **Live progress dashboard** — watch each alt text generate in real time with ETA
- **Image thumbnails** — visually verify accuracy as results come in
- **Smart column detection** — auto-fixes swapped `image_url` / `page_url` columns
- **Customisable settings** — word length, tone, and request delay
- **One-click copy** — copy individual alt texts or all at once
- **Download results CSV** — ready to paste into your CMS
- **API key saved in browser** — enter once, it remembers

---

## 🚀 Quick Start

### Option A — Web App (No coding, recommended for SEO teams)

1. **Download** [`index.html`](index.html)
2. **Open** it in Chrome or any modern browser
3. **Enter** your [Anthropic API key](https://console.anthropic.com) → click **Save**
4. **Upload** your CSV (needs `image_url` and `page_url` columns)
5. **Click** ▶ Generate Alt Text
6. **Download** the results CSV when done

> ✅ Works 100% offline — only the Anthropic API call requires internet.

---

### Option B — Google Colab (For bulk jobs or scheduled automation)

1. Open [`Alt_Text_Generator.ipynb`](Alt_Text_Generator.ipynb) in [Google Colab](https://colab.research.google.com)
2. Add your API key via the 🔑 **Secrets** panel (name it `ANTHROPIC_API_KEY`)
3. Run cells top to bottom
4. Download the completed CSV from the last cell

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/altgen/blob/main/Alt_Text_Generator.ipynb)

---

## 📋 CSV Format

Your input CSV must have these two columns (column names are flexible):

| image_url | page_url |
|-----------|----------|
| `https://example.com/images/product.jpg` | `https://example.com/stainless-steel-pipes/` |
| `https://example.com/images/flange.webp` | `https://example.com/flanges/nickel-alloy-flanges/` |

> 💡 Column order doesn't matter. The tool auto-detects which column contains image URLs.

A sample file is available at [`sample/sample_input.csv`](sample/sample_input.csv).

---

## 🔑 Getting Your Anthropic API Key

1. Go to [console.anthropic.com](https://console.anthropic.com) and sign up / log in
2. Click **API Keys** in the left sidebar
3. Click **Create Key** → give it a name → copy it immediately (starts with `sk-ant-...`)
4. Paste it into the app

> 💰 Cost: Processing ~40 images costs only a few cents using Claude Sonnet.  
> You can set a spend limit under **Plans & Billing** in the console.

---

## ⚙️ Settings

| Setting | Options | Default | Description |
|---------|---------|---------|-------------|
| Word Length | Short (8–12) / Medium (10–15) / Long (12–18) | Medium | Target length of generated alt text |
| Tone | Professional / E-commerce / Technical / Conversational | Professional | Writing style matched to your niche |
| Delay (ms) | 300–5000 | 800 | Pause between API calls to respect rate limits |

---

## 📁 Project Structure

```
altgen/
├── index.html               # Web app (open directly in browser)
├── Alt_Text_Generator.ipynb # Google Colab notebook
├── sample/
│   └── sample_input.csv     # Example CSV to test with
├── docs/
│   └── preview.png          # UI screenshot for README
└── README.md
```

---

## 🧠 How Alt Text is Generated

For each row, the tool:

1. **Fetches the image** from the provided URL
2. **Extracts page context** from the page URL slug (e.g. `stainless-steel-flanges`)
3. **Sends both** to Claude claude-sonnet-4-20250514 with strict alt text rules:
   - Describes visible product details (material, shape, finish, orientation)
   - Integrates page niche naturally — no keyword stuffing
   - No repeated words
   - Never starts with "Image of" or "Photo of"
   - Sentence case only

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Vanilla HTML / CSS / JS (zero dependencies) |
| AI Model | Claude claude-sonnet-4-20250514 via Anthropic API |
| Colab Runtime | Python 3 + `anthropic` SDK |
| Hosting | GitHub Pages (static, no server needed) |

---

## 🌐 Deploy on GitHub Pages

To host the web app publicly for your team:

1. Fork this repo
2. Go to **Settings → Pages**
3. Set Source to `main` branch → `/ (root)`
4. Your app will be live at `https://YOUR_USERNAME.github.io/altgen/`

> Each user enters their own API key — it is stored only in their browser's local storage and never sent to any server other than Anthropic.

---

## 🔒 Privacy & Security

- **API keys** are stored in your browser's `localStorage` only — never logged or transmitted to any third party
- **Images** are sent directly from your browser to the Anthropic API — no intermediate server
- **CSV data** never leaves your browser except for the image URLs sent to Anthropic

---

## 🤝 Contributing

Pull requests are welcome! To contribute:

```bash
git clone https://github.com/YOUR_USERNAME/altgen.git
cd altgen
# Open index.html in your browser to test
```

Please open an issue first for major changes.

---

## 📄 License

MIT — free to use, modify, and distribute.

---

## 💬 Support

- Open an [issue](../../issues) for bugs or feature requests
- For API questions, see [Anthropic's documentation](https://docs.anthropic.com)
