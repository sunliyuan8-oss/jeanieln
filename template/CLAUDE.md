# Listing-Site Template

This folder is a **template** for building a new luxury-property listing site
in the same editorial style as the Jeanie Lane site (`../index.html`).

It is NOT a separate codebase — there's no parallel `template/index.html` to
keep in sync. Instead, this folder holds:

- `CLAUDE.md` (this file) — instructions for spinning up a new site
- `schema.json` — the data model: every variable the site needs

To create a new listing site, **copy `../index.html` to the new project**, then
do find-and-replace on the variables defined in `schema.json`.

## How to use this template

When a user says "make a listing site for [property]", do this:

### Step 1: Collect the data
Ask the user (or extract from any files they uploaded) for the values defined
in `schema.json`. The big ones are:

- **Address** (street, city, state, ZIP, county jurisdiction)
- **Land facts** (acreage, zoning, water source, road access, permit status)
- **Home facts** (sqft, BR/BA per unit, architectural style, year built)
- **Income data** (if STR): months operating, gross revenue, ADR, channel mix,
  monthly revenue array, peak months
- **Distinctive features** (4 strong selling points with one photo each — e.g.
  "Library Rotunda", "Game Pavilion", "Vineyard")
- **Possibilities pillars** (3 buyer-thesis pillars — e.g. "Host anything",
  "Park everything", "Disappear from the world")
- **Three ways to own this** (3 thesis cards — e.g. Investor / Multi-gen / Venue)
- **Location POIs** (8 nearby places with distances in minutes)
- **Contact** (1–2 listing agents with name / email / phone)
- **Photos** (real photos only, never stock; 25–35 images covering exterior,
  interiors, outdoor, optional events)

### Step 2: Customize the site

1. Copy `../index.html` to the new project root.
2. Replace all placeholder strings (see `schema.json` for the full list).
3. Replace `assets/photos/*.jpg` with the new property's photos.
4. Adjust the color palette in the `:root` block if the new property has a
   different visual personality (e.g. a beach house might be cooler blues vs.
   warm cream — but only deviate when there's a real reason).

### Step 3: Deploy

For the user's own properties, deploy to GitHub Pages via the same flow as
`../CLAUDE.md` describes. For other people's properties, suggest Cloudflare
Pages or Vercel — connect their own GitHub.

## Design system (reusable, do not change without reason)

### Type
- **Fraunces** (display serif, 300/400/500/600 weights, italic too)
- **Inter** (UI sans, 300–700)
- Hero H1: `clamp(44px, 5.4vw, 88px)` Fraunces 300
- Section H2: `clamp(38px, 5vw, 64px)` Fraunces 300
- Editorial lede: `clamp(24px, 2.4vw, 32px)` Fraunces 300 with drop-cap
- Body: 16px Inter / line-height 1.7
- Big stat numbers: 34–48px Fraunces 300 with small `<sup>$</sup>`
- Eyebrow / kicker: 11–12px Inter 500–600 uppercase `.18–.22em` letter-spacing

### Color tokens
```css
--ink:        #1f1a14   /* primary text, dark band backgrounds */
--ink-soft:   #3d362d   /* secondary text */
--paper:      #f5efe2   /* base background — warm cream */
--paper-warm: #ebe1cc   /* deeper warm background for thesis section */
--terra:      #a4502a   /* primary accent (terracotta) */
--terra-deep: #7a3318   /* dark accent, used on numbers, links, drop caps */
--olive:      #525a2c   /* "Direct" channel color */
--gold:       #b48a3c   /* gold accents on dark bands */
--line:       rgba(31,26,20,.14)
--rule:       rgba(31,26,20,.08)
```
Gold for hero/CTA over dark photos: `#e8c98f`.

### Section structure (in order)
1. **Sticky nav** — brand left, links center, CTA button right
2. **Hero** — full-bleed photo, title in upper-left sky (negative-space safe), meta below
3. **Stat strip** — 5-column dark band of headline numbers
4. **Section 01 The Property** — editorial waterfall: 3-col section-label → lede with drop-cap → 4-col fact strip → 2-col prose flow → 4-card highlights row
5. **Section 02 Inside the residence** — 12-col masonry gallery, click-to-lightbox
6. **Section 03 Possibilities** — dark band, 3 pillar columns (photo above + text below, no overlay)
7. **Section 04 Income** — 4 big numbers + monthly revenue stacked bar chart (paid solid + upcoming dashed) + channel mix donut + performance snapshot
8. **Section 05 Where it sits** — image hero split + 2-col POI list (no decorative maps; use real-property imagery)
9. **Section 06 Three ways to own this** — 3-card thesis grid on `--paper-warm`
10. **CTA** — full-bleed photo backdrop, two buttons, dual contact card below
11. **Footer** — dark band, brand left, contact center, listing info right

### Writing tone
- **Editorial-luxury**. Sotheby's / Compass / The Modern House register.
- **Specific over abstract**. "Marble floors with radiant heat" not "luxurious finishes".
- **Short declarative sentences** can stand alone as paragraphs in listing prose.
- **No AI clichés** ("Imagine...", "Welcome to...", "Step inside..." used sparingly
  if at all).
- **Never invent**. If you don't know the fact, ask the user, don't fabricate.

### Photo principles
- All real, supplied by user/seller.
- Hero photo: full-bleed daytime exterior; make sure upper-left quadrant is
  "negative space" (sky or trees) so title text doesn't compete with architecture.
- Use one strong photo per highlight card / possibility pillar — don't repeat
  images across sections.
- Gallery is the place for variety: 10 photos in a 12-col masonry.

## Anti-patterns (don't do these — they were tried and rejected)

- ❌ Overlaying large title text on top of the building in the hero photo.
- ❌ "12 acres of usable land" or any other invented stat — always verify.
- ❌ Generic photos from image_search for property visuals.
- ❌ Hand-drawn whimsical maps as part of a luxury layout (too casual).
- ❌ Right-column feature-list paired with long-form left-column prose (creates
  a tall whitespace gap on the right — use full-width fact strip instead).
- ❌ Text-overlaid photos in the "Possibilities" pillars — photos should be
  clean, with text in a sibling block below.
- ❌ Wedding / events as primary positioning — it's an upside layer, not the
  headline (unless the property is purpose-built as a venue).
