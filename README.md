<p align="center"><img src="icons/logo-512.png" alt="WASH Report logo" width="160"></p>

# WASH Report Converter

A browser-only tool that turns your daily WASH Excel file into a complete, formula-driven management report workbook (`WASH_Report_YYYY-MM-DD.xlsx`).

Nothing is uploaded anywhere: the file is read and the report is built entirely in your browser, with no libraries and no server.

## What you get

The generated Excel file contains:

- **Daily Wash Running** and **Daily ReWork Running** reports (running ERPs only)
- **ERP_Status**: master list per Buyer + ERP with Running / Closed status and triggers (READY TO CLOSE, STALLED, CHECK)
- **Closed Orders**, **Reject Summary**, **Wash Monthly Report**, **Vendor Statement**
- **Monthly**, **By Buyer**, **By Process**, **By Floor & Line**, **By Vendor**, **Buyer x Month**, **RW Accountability**
- **Wash_Data** and **ReWork_Data** (all cleaned records) and a **Guide** sheet

## How to use

1. Open the page (see *Run it* below).
2. Choose your daily WASH `.xlsx` file. It needs sheets named like `Wash Send & Rcv Staus (Old)`, `(Running)` and `Re-Work Report`.
3. Optional: choose yesterday's `WASH_Report_….xlsx` so your Running / Closed decisions carry over.
4. Press **Convert**, then **Download report (.xlsx)**.
5. Open the file in Excel 2019 / Microsoft 365 and click **Enable Editing**.

## Run it

**Locally:** open `index.html` in a modern browser (Chrome, Edge, Firefox, Safari). If your browser blocks anything, serve the folder instead:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

**GitHub Pages:** push this repo to GitHub, then in *Settings → Pages* set the source to **GitHub Actions**. The included workflow (`.github/workflows/pages.yml`) publishes the site on every push to `main`.

## Project structure

```
index.html              page markup
css/style.css           styles (light and dark mode)
js/engine-reader.js     zip + xlsx reader, data cleaning and collection
js/engine-report.js     workbook model, all report sheets, xlsx writer
js/app.js               page logic: file pickers, preview, download
icons/                  logo, favicons, apple-touch-icon, 192/512 and maskable icons
manifest.webmanifest    installable-app (PWA) manifest
favicon.ico             browser tab icon
.github/workflows/      GitHub Pages deployment
```

## Requirements

A browser that supports `DecompressionStream` / `CompressionStream` (current Chrome, Edge, Safari and Firefox).

## License

MIT, see [LICENSE](LICENSE).
