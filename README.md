# שומר (Shomer) — Hebrew APK landing page

Static, single-file Hebrew (RTL) landing page for the **Screen Guard APK**
Hebrew distribution. The brand name "שומר" is a proposal — the README that
shipped with the original zip (`README-HE.txt`) explains how to rename it.

## What's here

- `index.html` — the whole page; CSS and JS are inlined, no backend, no PHP,
  no database.
- `assets/shomer-logo.svg` — the logo, also used as the favicon. Replace this
  file to rebrand without touching the code.
- `assets/rav-kook.jpg` — the cover-screen image (Rabbi Kook, 1924, Library of
  Congress, public domain), same source the app uses.

The page uses the Modesty Cyan Prism palette (navy `#193B51`, cyan `#44D7EB`,
Screen Guard coral `#FF8F89`). Fonts (Heebo + IBM Plex Mono) load from Google
Fonts, so the client needs internet; self-host the fonts for full offline use.

## Before it goes live

In `index.html`:

1. **Download links** — search for `data-dl`. There are three cards
   (religious / family / kids) with `href="#"`. Replace each `#` with the real
   APK path. Until then the buttons show a "link will be connected" message.
2. **Brand name** — "שומר" appears in the title, topbar, tabs and footer. The
   logo is a separate SVG, so it can be swapped independently.
3. **Main-site link** — appears twice (download section + footer), currently
   `https://modesty.cia.org.il`. Update if the domain changes.

## Deployment (subdomain)

This is a **static site** — point the subdomain's document root at this
directory (or upload `index.html` + `assets/` to it). No server config, no DB,
no code changes needed. Example:

```
shomer.<your-project-domain>  ->  docroot = landing/shomer/
```

After upload, hard-refresh / purge the CDN for `/` and `/assets/*`.

## Source

Staged from `D:\Downloads\Web\shomer-landing-v5.zip` (deliverable, 18 Nov 2026).
The phone simulation on the page is CSS-only, with a demo button that shows or
hides the cover screen — no external image dependencies beyond the bundled
asset. The Hebrew cover screen is reproduced 1:1 from the app's
`overlay_cover.xml` + religious `brand.json` + real Hebrew strings.
