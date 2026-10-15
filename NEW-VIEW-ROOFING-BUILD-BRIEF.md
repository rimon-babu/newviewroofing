# New View Roofing — Website Redesign Build Brief

> **For:** Claude Code
> **Project:** `newview-roofing-redesign`
> **Prepared by:** Websiteo Plus (W+)
> **Date:** 13 October 2026
> **Source site:** https://newviewroofing.com/

---

## 0. How to use this file

This is the single source of truth for the build. Read it top to bottom before writing any code.

- **Sections 1–2** are business context and the sales pitch. Not code, but they explain *why* every design decision below exists. Do not skip them.
- **Sections 3–5** are the design system, page structure and file tree. Build exactly to these.
- **Section 6** is the image brief. Generate nothing — reference the filenames and render labelled placeholders where files do not yet exist.
- **Sections 7–9** are the cinematic showcase video pipeline (capture, audio, assembly).
- **Section 10** is the build order. Follow it.
- **Section 11** is future scope — do not build, but note it in `docs/proposal.md`.

**Hard rules for this project:**

1. Use the **real content** from the source site. Do not invent testimonials, statistics, service claims, certifications or review text.
2. Do not fabricate certification badges, the client logo, or faces for real named reviewers. Reference the real asset paths and use placeholders.
3. No frameworks. Static HTML + CSS + vanilla JS. The site must open and run from `index.html` with no build step.
4. Mobile-first. Accessibility and performance are requirements, not polish.
5. Match the design tokens in §3 exactly — no approximating or eyeballing values.

---

## 1. Business & Website Audit

### 1.1 The business

| Field | Value |
|---|---|
| Name | New View Roofing |
| Positioning | Veteran-owned, family-operated roofing contractor |
| Market | Dallas–Fort Worth Metroplex, TX |
| Experience | 25+ years roofing and home remodeling |
| Certification | GAF Master Elite® — top 3% of roofing companies in the US |
| Reviews | 4.9 stars, 650+ Google reviews |
| Phone | (469) 716-5859 |
| Email | info@newviewroofing.com |
| Corporate office | 4722 Gaston Ave, Dallas, TX 75246 |
| Hours | 8:00 AM – 7:00 PM |
| Payment | All major credit cards, cash, check, money orders, cashier's check |
| Financing | Hearth — 0% APR up to 18 months (promotional period) |
| Current vendor | MarketCrest |

**Services:** Residential Roofing · Commercial Roofing · Roof Repair · Roofing Maintenance Plans · Gutters · Decks · Fencing · Siding · Roof Coating · Roof Damage Assessments · Windows

**Social:**

- Instagram — https://www.instagram.com/newviewroofing/
- Facebook — https://www.facebook.com/newviewroof/
- YouTube — https://www.youtube.com/@newviewroofing
- Email — mailto:info@newviewroofing.com
- Phone — tel:+14697165859
- Directions — https://www.google.com/maps/search/?api=1&query=4722+Gaston+Ave+Dallas+TX+75246

### 1.2 The core problem

They are buying traffic on Facebook ads and sending it to a 2016-era WordPress template that leaks trust at exactly the moment a homeowner decides whether to hand over their biggest asset.

**The product is fine. The storefront is not.**

### 1.3 What is actually broken

**Credibility killers — fix these first, this is where the money is**

1. **"Our Projects" section is empty.** On the live homepage that entire block renders blank with a lone "View All" button. A roofing company showing zero project proof on the homepage is the single worst thing on the site.
2. **Testimonials are duplicated.** The same two reviews (Benjamin K., Mir A.) repeat four times in the carousel. It reads as fabricated. They have 650+ real reviews at 4.9 and are showing two on a loop.
3. **Review images named `unnamed (25)`, `unnamed (27)`.** Template leakage, zero alt text, bad for SEO and screen readers.
4. **`Money-check-alt` prints as raw text** in the header and footer icon rows — an unstyled Font Awesome class name is visible to users. Looks unmaintained.
5. **650+ reviews / 4.9 rating is a ~90px badge in the header.** Their strongest single asset, buried.

**Conversion architecture**

6. **No CTA hierarchy.** The header carries a call link, a Hearth financing banner, a Google reviews badge, social icons and a "New View Reviews" link — plus the hero form, plus "Learn More", plus "FREE INSPECTION". Everything shouts, nothing converts.
7. **Hero form asks 5 fields cold**, sits in a cramped gold box over a busy photo, has poor contrast, and gives no indication of what happens next.
8. **FAQ is a wall of 25 blue buttons.** No accordion, no grouping, no inline answers. Pure cognitive overload, and the FAQ schema value is not being captured properly.
9. **Services are 12 flat blue buttons.** No imagery, no outcome language, no differentiation between a $400 repair and a $28k replacement.
10. **No storm / emergency path.** In DFW, hail is the number one purchase trigger. There is a nav item, but no urgent above-the-fold lane for "my roof is leaking right now."
11. **Insurance claim help is buried** on the inspection page as a bullet list. For roofing, "we handle your insurance claim" is the single biggest conversion lever and deserves a full homepage section.
12. **Financing is a flat banner image** in the header and sidebar instead of a real section with a payment figure.
13. **No sticky mobile call bar.** Mobile ad traffic has to scroll hunting for the number.

**Technical / SEO**

14. **Service area list mixes Cleveland OH, Stillwater OK and Austin into a DFW list.** Dilutes local relevance and confuses the reader about where they actually operate.
15. **Instagram embed + Google Map iframe + carousel plugins on the homepage.** Heavy third-party JS, almost certainly damaging LCP and INP on mobile. *Run https://pagespeed.web.dev/ against https://newviewroofing.com/ and screenshot the mobile score before the pitch — that is the opening slide.*
16. **Accessibility overlay widget** (floating blue icon). These are a known legal liability, not a fix. Real remediation beats the widget.
17. **All-caps headings and gold-on-white text** — contrast failures and reduced readability.
18. **No dedicated ad landing page.** Facebook ad traffic lands on a general homepage. Message match is zero. This alone is likely costing 30–50% of their ad ROI.

---

## 2. Pitch Angle

Do not sell design. Sell cost-per-acquired-job.

> "You're paying for Facebook traffic. Every visitor hits a page with an empty projects section, two reviews on repeat, and a 25-button FAQ wall. You have 650 five-star reviews and GAF Master Elite top-3% status — the site shows almost none of it. We're not changing your business. We're making the website finally say what you already are."

**Numbers to put on screen:**

- At a given monthly ad spend and a ~2% conversion rate, moving to 4% halves cost per lead without touching ad budget.
- One extra roof replacement per month at DFW average ticket pays for the entire redesign in month one.
- Ask them for: current monthly ad spend, leads per month, average job value, close rate. Build the ROI table live on the call. That is the close.

**Pitch deck order — five slides, six minutes:**

1. PageSpeed mobile screenshot
2. The empty Projects section screenshot
3. The duplicate testimonials screenshot
4. The cinematic motion loop video of the redesign
5. The ROI table

**Honesty note for the proposal:** state plainly that demo images are AI-generated concepts and the production build uses their real job photos and real certification badges. Saying this unprompted makes you the professional in the room.

---

## 3. Design System

### 3.1 Direction

Minimal, premium, architectural. Not minimal-as-in-empty — minimal as in **one idea per screen**, enormous whitespace, a single accent colour, real photography carrying the emotion, and type doing the hierarchy instead of boxes and borders.

Reference feel: Linear-grade restraint crossed with architectural photography and the quiet confidence of a high-end Dallas custom-home builder. Not a lead-gen funnel.

### 3.2 Tokens — `assets/css/tokens.css`

```css
:root{
  /* ---- Colour — refined from their existing brand ---- */
  --ink:        #0B1A33;   /* deep navy — headlines, dark sections */
  --navy:       #16305C;   /* brand blue, refined */
  --navy-soft:  #233F6E;
  --gold:       #C08A3E;   /* refined from their #D6A85B — passes contrast */
  --gold-light: #E3C48E;
  --bone:       #F7F5F1;   /* page background — NOT pure white */
  --white:      #FFFFFF;
  --slate:      #5A6679;   /* body text on light */
  --line:       #E6E2DB;   /* 1px hairlines — no drop shadows */
  --signal:     #B3321E;   /* storm / emergency only — max 2 uses per page */

  /* ---- Type ---- */
  --font-display: "Archivo", system-ui, -apple-system, sans-serif;
  --font-body:    "Inter", system-ui, -apple-system, sans-serif;

  /* ---- Space — 8pt grid ---- */
  --section-y: clamp(80px, 10vw, 160px);
  --container: 1280px;
  --content:   1120px;
  --gutter:    24px;

  /* ---- Radius ---- */
  --radius-sm: 4px;
  --radius:    8px;
  --radius-lg: 16px;

  /* ---- Motion ---- */
  --ease: cubic-bezier(0.22, 1, 0.36, 1);
  --dur:  420ms;
}
```

### 3.3 Typography rules

- **Display:** Archivo, weight 600/700, `letter-spacing: -0.02em`.
- **Body:** Inter, weight 400/500, 18px base, `line-height: 1.65`, max measure `68ch`.
- **Fluid display scale** via `clamp()`: 72 / 56 / 40 / 28 / 20 px.
- **Tabular numerals** (`font-variant-numeric: tabular-nums`) on all stats and phone numbers.
- **All-caps only** for 11px eyebrow labels at `letter-spacing: 0.12em`.
- **Max two type weights per section.**
- Self-host both fonts as `woff2` in `assets/fonts/`, subset to latin, `font-display: swap`.

### 3.4 Component rules

- **No drop shadows** anywhere except the sticky header once scrolled.
- **No gradients** except one subtle vignette on the hero.
- **Borders:** 1px solid `--line`. Nothing heavier.
- **Buttons:** primary solid `--ink`; secondary solid `--gold`; tertiary ghost with 1px `--line` border.
- **Cards:** no shadow, no border radius above `--radius`, separated by whitespace and hairlines only.
- **Focus rings:** 2px `--gold` outline with 2px offset, always visible, never removed.

---

## 4. Page Structure

### 4.1 `index.html` — 14 sections

| # | Section | Content spec |
|---|---|---|
| 01 | **Sticky header** | Logo, 6-item nav, "(469) 716-5859" + "Free Inspection" button. Slim. No financing banner, no social icons, no reviews badge up top. Shadow appears on scroll only. |
| 02 | **Hero** | Full-bleed roofline photo with vignette. H1: *"Dallas–Fort Worth's veteran-owned roofing experts."* Sub: full-scale residential, commercial & industrial roofing services. Dual CTA: **Get a free inspection** / **Call (469) 716-5859**. Thin proof strip beneath: ★4.9 · 650+ Google reviews · GAF Master Elite · Veteran-Owned · 25+ Years. |
| 03 | **Trust band** | Four stat blocks, hairline-separated, with count-up animation: `25+` Years Experience · `Top 3%` GAF Master Elite · `4.9★` / 650+ Reviews · `Veteran-Owned` & Family-Operated. Real badge logos below (GAF, BBB A+, NTRCA, Angi Super Service, Living Best Of) — **use their actual badge files, never generate trademarks.** |
| 04 | **Services** | Four large image cards: Residential · Commercial · Roof Repair · Storm Damage Repair. Below, a quiet text row of the rest: Gutters, Decks, Fencing, Siding, Roof Coating, Roof Damage Assessments, Windows, Roofing Maintenance Plans → *View All Services*. |
| 05 | **Storm & insurance** | **New section.** Dark `--ink` background. Headline: *"Hail hit. We handle the claim."* Their real 11-step process condensed to 5 steps, sourced from the free-inspection page copy. CTA: **Start my claim inspection**. |
| 06 | **Process timeline** | Five steps, horizontal on desktop, stacked on mobile, from their actual copy: Request → Inspection within 24h → Plan & recommendations → Scheduling & install → Walkthrough + warranty papers. |
| 07 | **Proof** | Before/After drag slider (3 pairs) + 6-image project grid. **This replaces the currently empty block — it is the most important fix on the page.** |
| 08 | **About / Values** | Real team photo + the "Welcome to New View Roofing" copy verbatim. Then four values as text-only with hairline separators, using their exact wording: Fairness, Accountability, Quality, Service. |
| 09 | **Financing** | *"0% APR for up to 18 months through Hearth."* One worked payment example. CTA: **See options**. Footnote: 0% interest for promotional period only. |
| 10 | **Service areas** | Stylized DFW map (SVG, built in code) + city chips: Allen, Arlington, Carrollton, Dallas, Flower Mound, Frisco, Fort Worth, Garland, Grand Prairie, Grapevine, Irving, Lewisville, Little Elm, McKinney, Plano, Richardson, Southlake, The Colony. **Recommendation: drop Cleveland OH / Stillwater OK / Austin from the DFW list, or give them a separate "Also serving" line.** |
| 11 | **Reviews** | Wall of 6+ real Google reviews — Todd Fariss, Nicole Beck, Matthew Carter, Benjamin K., Mir A., plus more pulled from their live Google profile. **Initials avatars rendered in CSS, never stock or generated faces.** Link out to the full Google profile. |
| 12 | **FAQ** | Their 25 real questions grouped into 5 accordions: *Before You Start · Inspections & Damage · Insurance & Cost · Materials & Systems · Working With Us*. Valid `FAQPage` JSON-LD. |
| 13 | **Final CTA** | Two-step form. Step 1: name + phone + zip. Step 2: address + city + message. Microcopy: *"We respond within 24 hours. No obligation, no pressure."* |
| 14 | **Footer** | Logo, veteran-owned blurb, (469) 716-5859, 4722 Gaston Ave Dallas TX 75246, info@newviewroofing.com, Get Directions, service list, social icons, Privacy Policy, Sitemap, © 2026. |
| — | **Mobile sticky bar** | Call · Text · Free Inspection. Fixed, always visible below 768px. |

### 4.2 `free-inspection.html` — dedicated ad landing page

This is the page their Facebook ads should point at. Message match is the entire point.

Structure: hero form (above fold, 5 fields) → "What To Expect When Working With New View Roofing After A Free Roof Inspection" (their verbatim 11-step list) → 3 inspection FAQs (Why / When / Can I get a quote) → reviews → office details card (address, tel, hours, payment methods) → footer.

Keep their exact copy including the insurance-claim language. Do not rewrite the insurance wording — it has been carefully hedged for compliance.

---

## 5. File Structure

```
newview-roofing-redesign/
├── index.html
├── free-inspection.html
├── README.md
├── package.json
│
├── assets/
│   ├── css/
│   │   ├── tokens.css              # all CSS variables from §3.2
│   │   ├── base.css                # reset, typography, container, utilities
│   │   ├── components.css          # buttons, cards, forms, accordion, slider
│   │   ├── sections.css            # sections 01–14
│   │   └── motion.css              # scroll reveals + reduced-motion guards
│   │
│   ├── js/
│   │   ├── main.js                 # init / module wiring
│   │   ├── nav.js                  # sticky header, mobile drawer
│   │   ├── reveal.js               # IntersectionObserver scroll reveals
│   │   ├── before-after.js         # drag slider (mouse + touch + keyboard)
│   │   ├── accordion.js            # FAQ, aria-expanded
│   │   ├── form-steps.js           # 2-step form, validation, success state
│   │   ├── counters.js             # stat count-up
│   │   └── lenis-smooth.js         # optional smooth scroll — VIDEO CAPTURE ONLY
│   │
│   ├── img/
│   │   ├── hero/
│   │   ├── services/
│   │   ├── process/
│   │   ├── projects/
│   │   ├── storm/
│   │   ├── team/
│   │   ├── badges/                 # REAL client badge files — never generated
│   │   ├── textures/
│   │   ├── map/
│   │   ├── og/
│   │   └── favicon/
│   │
│   ├── icons/                      # inline SVG sprite: phone, star, shield, arrow, chevron
│   ├── fonts/                      # self-hosted Archivo + Inter woff2 subsets
│   ├── video/
│   │   ├── hero-loop.mp4
│   │   ├── hero-loop.webm
│   │   └── hero-loop-poster.jpg
│   └── audio/                      # generated by generate_audio.py — see §8
│
├── motion/
│   ├── storyboard.md               # shot list, timings, copy overlays
│   ├── hyperframes/
│   │   ├── prompts/                # one .txt per B-roll shot
│   │   └── renders/                # Hyperframes MP4 output
│   ├── capture/
│   │   ├── capture.mjs             # Playwright scripted scroll → PNG frames
│   │   ├── scenes.json             # scroll positions, holds, easing per scene
│   │   └── frames/
│   ├── audio/
│   │   ├── generate_audio.py       # numpy/scipy SFX + pad generator
│   │   └── stems/
│   ├── build/
│   │   ├── assemble.sh             # ffmpeg: frames → video → mix → loop verify
│   │   └── subtitles.srt
│   └── out/
│       ├── newview-showcase-loop.mp4      # 1920×1080, 58s, seamless loop
│       ├── newview-showcase-9x16.mp4      # vertical cut for Reels/Stories
│       └── newview-showcase-poster.jpg
│
├── scripts/
│   ├── optimize-images.mjs         # sharp → webp/avif + responsive srcset
│   ├── rename-assets.mjs           # enforce naming convention
│   └── build-sprite.mjs            # SVG sprite builder
│
└── docs/
    ├── audit.md                    # §1 of this brief
    ├── proposal.md                 # client-facing pitch (§1 + §2 + §11)
    └── content-map.md              # every string from the old site → new location
```

### 5.1 Asset naming convention

`{section}-{subject}-{variant}-{width}.{ext}`

Examples: `hero-roofline-dusk-2880.jpg` · `svc-residential-ranch-1600.webp` · `proj-plano-after-1600.webp`

Enforce with `scripts/rename-assets.mjs`.

---

## 6. Image Brief

### 6.1 Rules before generating anything

**Never AI-generate:**

- The New View Roofing logo
- GAF Master Elite, BBB A+, NTRCA, Angi Super Service, Living Best Of badges
- The Hearth financing card
- Google logos or review-platform marks
- Faces for real named reviewers

Use the client's actual files, or CSS-rendered initials avatars. Fabricating certification marks or review faces will sink the pitch if anyone notices.

**Real project photos beat everything.** The AI images are concept placeholders for the demo. The production build swaps in the client's real job photos. Say this in the proposal — it is a trust point, not a weakness.

**Geography consistency:** DFW housing means red/brown brick, light limestone accents, dark architectural asphalt shingle, St. Augustine lawns, live oaks and crepe myrtles, and a big flat Texas sky. Keep every exterior consistent with this or the images will not read as local.

### 6.2 Global style suffix — append to every prompt

```
Shot on a 35mm full-frame camera, 35–50mm prime, f/2.8, natural light,
editorial architectural photography, muted warm-neutral grade, soft contrast,
subtle film grain, no text, no logos, no watermarks, no signage,
no visible brand marks, photorealistic, ultra detailed, 8k.
```

### 6.3 Global negative prompt — use on every generation

```
text, letters, watermark, logo, brand name, signage, cartoon, illustration,
3d render, cgi, oversaturated, hdr halo, fisheye, distorted architecture,
extra limbs, deformed hands, blurry faces, lens flare overload, snow, mountains,
palm trees, european architecture
```

---

### 6.4 HERO — `assets/img/hero/`

**01 — `hero-roofline-dusk-2880.jpg`** · 2880×1620 · 16:9

> Low wide angle looking up at the roofline of an upscale North Dallas two-story brick home, dark charcoal architectural asphalt shingles crisply defined, clean straight ridge line and gable, warm golden-hour light raking across the shingle texture from the left, huge soft Texas sky with thin high clouds in the upper two thirds, a single mature live oak softly out of focus at the right edge, serene and still, generous negative space in the sky for headline text.

**02 — `hero-roofline-mobile-1400.jpg`** · 1400×1800 · 4:5

> Vertical composition of the same upscale Dallas brick home at golden hour, camera low and close so the roofline cuts diagonally across the frame, tall column of warm sky above with clouds, shallow depth of field, strong vertical negative space at the top for a headline.

**03 — `hero-ambient-loop-poster-1920.jpg`** · 1920×1080 · poster frame for the optional hero video

> Static wide of a Dallas suburban rooftop at blue hour, lights warm inside the windows below, soft dusk gradient sky from amber at the horizon to deep navy overhead, calm, cinematic, very subtle.

---

### 6.5 SERVICES — `assets/img/services/`

**04 — `svc-residential-ranch-1600.jpg`** · 1600×1200 · 4:3

> Three-quarter exterior view of a well-kept single-story Texas ranch home with red brick and light limestone accents, brand-new dark charcoal architectural shingle roof, clean soffit and fascia, manicured St. Augustine lawn, soft late-afternoon light, calm residential street, no people.

**05 — `svc-commercial-flatroof-1600.jpg`** · 1600×1200 · 4:3

> Elevated view across a large white TPO flat commercial roof on a low-rise Dallas warehouse, clean seams running toward the horizon, rooftop HVAC units in the mid-distance, crisp geometric lines, bright overcast diffused light, industrial but orderly and premium.

**06 — `svc-roof-repair-1600.jpg`** · 1600×1200 · 4:3

> Close-up over-the-shoulder of a roofing professional in a navy work shirt and tan gloves lifting a damaged shingle tab on a residential roof, hands and shingle in sharp focus, roof plane falling away softly behind, warm morning light, face not visible, documentary feel.

**07 — `svc-storm-damage-1600.jpg`** · 1600×1200 · 4:3

> A residential asphalt shingle roof after a hailstorm, scattered circular hail bruises and granule loss visible across the shingles, a few small hailstones resting in the valley, flat grey post-storm light with a break of sun at the edge, serious documentary tone, no people.

**08 — `svc-gutters-1600.jpg`** · 1600×1200 · 4:3

> Tight detail of a newly installed seamless aluminium gutter and downspout along the eave of a brick Texas home, clean straight line of the gutter running to the corner, crisp shadow underneath, soft morning light, shallow depth of field on the brick behind.

**09 — `svc-siding-1600.jpg`** · 1600×1200 · 4:3

> Detail of freshly installed fiber-cement lap siding in warm greige on a residential exterior, perfectly aligned horizontal courses, raking afternoon light showing the subtle wood texture, a trimmed window edge at the right of frame.

**10 — `svc-windows-1600.jpg`** · 1600×1200 · 4:3

> Exterior detail of a new black-framed double-hung window set into red brick on a Texas home, crisp caulk lines and trim, warm reflection of trees and sky in the glass, soft golden-hour light.

**11 — `svc-decks-1600.jpg`** · 1600×1200 · 4:3

> A newly built covered backyard deck on a Texas home, warm stained wood planks and clean post work, shade structure casting soft linear shadows, green lawn beyond, late-afternoon light, inviting and uncluttered, no people.

**12 — `svc-fencing-1600.jpg`** · 1600×1200 · 4:3

> A long run of new cedar board-on-board privacy fence along a Texas backyard, vertical boards warm and uniform, soft shadow from a nearby tree falling across them, green lawn in the foreground, golden-hour side light.

**13 — `svc-roof-coating-1600.jpg`** · 1600×1200 · 4:3

> Wide view of a freshly applied bright white reflective roof coating on a flat commercial roof, the clean coated surface meeting a crisp parapet edge, strong Texas sun, high-key and minimal, almost abstract.

**14 — `svc-maintenance-1600.jpg`** · 1600×1200 · 4:3

> A roofing technician in navy uniform kneeling on a residential roof with a clipboard and small tool kit, inspecting a flashing detail around a vent pipe, calm and methodical, soft overcast light, face turned away, documentary.

---

### 6.6 PROCESS — `assets/img/process/`

**15 — `process-01-inspection-1400.jpg`** · 1400×1050

> A roofing inspector standing on a residential roof holding a tablet, looking down at a section of shingles, early morning light with long soft shadows across the roof plane, suburban Dallas rooftops receding in the background, calm professional tone, face not clearly visible.

**16 — `process-02-estimate-1400.jpg`** · 1400×1050

> Over-the-shoulder view of a tablet screen being held in front of a home exterior, generic blank light-grey interface on the screen with no readable text, a gloved hand pointing toward the roofline beyond, shallow depth of field, warm daylight.

**17 — `process-03-install-1400.jpg`** · 1400×1050

> A roofing crew in matching navy shirts and tan hard hats working across a residential roof deck, laying underlayment and shingle courses, organized stacks of bundles, clean worksite, bright mid-morning sun, wide documentary framing, faces not prominent.

**18 — `process-04-walkthrough-1400.jpg`** · 1400×1050

> A homeowner and a project manager standing on a driveway in front of a finished home, both looking up toward the new roof, warm late-afternoon backlight, relaxed and satisfied body language, shot from behind at a respectful distance so faces are not identifiable.

---

### 6.7 PROOF / PROJECTS — `assets/img/projects/`

> **Workflow for before/after pairs:** generate the **after** image first, then feed it back as an image reference with the **before** prompt so the house, angle and landscaping match exactly. The pair must look like the same property.

**19 — `proj-plano-before-1600.jpg`** · 1600×1067

> Three-quarter exterior of a two-story red-brick Plano home with an aging, weathered dark grey asphalt shingle roof showing uneven colour, granule loss, a few lifted shingles and a faded ridge, overcast flat light, tidy lawn, no people.

**20 — `proj-plano-after-1600.jpg`** · 1600×1067

> The exact same two-story red-brick Plano home from the identical camera position and angle, now with a brand-new dark charcoal architectural shingle roof, uniform colour, crisp ridge cap and clean valleys, warm golden-hour light, identical landscaping and sky composition.

**21 — `proj-frisco-before-1600.jpg`** · 1600×1067

> Three-quarter exterior of a single-story light-stone-and-brick Frisco home with a tired brown shingle roof, patchy discolouration and a sagging section near the eave, flat grey light.

**22 — `proj-frisco-after-1600.jpg`** · 1600×1067

> The exact same single-story Frisco home from the identical camera position, now with a new weathered-wood toned architectural shingle roof, perfectly uniform courses, new drip edge and gutters, warm afternoon light, identical landscaping.

**23 — `proj-commercial-before-1600.jpg`** · 1600×1067

> Elevated view of an aging flat commercial roof on a low-rise Dallas building, stained and weathered membrane, visible seams and ponding marks, overcast light.

**24 — `proj-commercial-after-1600.jpg`** · 1600×1067

> The exact same flat commercial roof from the identical elevated camera position, now with a brand-new bright white TPO membrane, clean welded seams, tidy flashing around the HVAC curbs, bright clear sky.

**25 — `proj-grid-01-1200.jpg`** · 1200×900

> New charcoal architectural shingle roof on a Dallas two-story brick home, shot from the front lawn at golden hour, strong clean roofline, crepe myrtle softly blurred in the foreground.

**26 — `proj-grid-02-1200.jpg`** · 1200×900

> Detail of a perfectly executed roof valley on a new residential roof, two shingle planes meeting in a clean line, crisp shadow, morning light, almost abstract geometry.

**27 — `proj-grid-03-1200.jpg`** · 1200×900

> Standing-seam metal roof on a modern Texas farmhouse-style home, dark matte finish, crisp vertical seams catching the late sun, clean white board-and-batten below.

**28 — `proj-grid-04-1200.jpg`** · 1200×900

> New ridge vent and ridge cap running along the peak of a residential roof against a big open Texas sky with soft clouds, low angle, late afternoon.

---

### 6.8 STORM & INSURANCE — `assets/img/storm/`

**29 — `storm-hail-damage-macro-1600.jpg`** · 1600×1067

> Extreme close-up of hail-bruised asphalt shingle, circular impact marks with exposed black mat where granules were knocked away, a US quarter resting beside one impact for scale, raking light revealing the depressions, forensic documentary clarity.

**30 — `storm-dfw-sky-2400.jpg`** · 2400×1350 · section background

> A dramatic Texas supercell storm front rolling over flat suburban rooftops on the horizon, towering shelf cloud in deep blue-grey, a band of warm light along the bottom edge, wide cinematic composition, rooftops small and dark in the lower fifth of the frame, huge sky.

**31 — `storm-aftermath-street-1600.jpg`** · 1600×1067

> A quiet suburban Dallas street immediately after a hailstorm, wet pavement reflecting a breaking sky, scattered leaves and small hailstones on the lawn, a few homes with tarps on roof sections in the distance, soft post-storm light, calm and documentary, no people.

---

### 6.9 TEXTURES, MAP, SOCIAL — `textures/`, `map/`, `og/`, `team/`

**32 — `tex-shingle-macro-2000.jpg`** · 2000×2000 · section background at 6% opacity

> Extreme macro of charcoal architectural asphalt shingle granules filling the entire frame, fine mineral texture, even soft lighting, near-monochrome, flat and seamless, no edges or horizon.

**33 — `tex-paper-grain-2000.png`** · 2000×2000 · overlay at 3–4%

> Seamless subtle off-white paper grain texture, very fine fibre detail, perfectly even lighting, no shadows, no pattern repetition, flat scan.

**34 — `og-share-1200x630.jpg`** · 1200×630

> Clean wide hero crop of an upscale Dallas brick home with a new charcoal roof at golden hour, lots of clear sky space on the left third for an overlaid logo and headline, minimal and premium.

**35 — `team-group-1600.jpg`** — *use the client's real team photo.* Placeholder only if quality forces it:

> A group of roofing professionals in matching navy polos standing in front of a brick building exterior, warm natural light, relaxed and confident, shot wide so faces are small and not identifiable.

**36 — `map-dfw-base.svg`** — **build this in SVG with code, do not generate.**

Minimal flat DFW metroplex map: `--bone` landmass, `--line` highways, city dots in `--gold`, labels in Inter 12px `--slate`. No satellite imagery, no Google tiles.

**Favicon set** — generate from the client's real logo file at 16, 32, 48, 180 (apple-touch), 192, 512 plus `site.webmanifest`. Do not AI-generate the mark.

### 6.10 Asset count

| Type | Count |
|---|---|
| AI-generated images | **34** |
| SVG built in code | 1 (DFW map) |
| Real client assets required | ~8 — logo, 5 badge files, Hearth card, team photo |

---

## 7. Cinematic Motion Loop — Storyboard

**Target:** 1920×1080, 24fps (cinematic cadence), **58 seconds, seamlessly looping.**
**Secondary:** 9:16 vertical cut at 30s for Reels and Stories.

**Grade:** warm neutral; lift blacks to `#0B1A33` rather than pure black; slight halation on highlights; 2% film grain; subtle 1.5:1 letterbox.

**Two layers combined:**

- **A-roll** — a real scripted scroll-through of the built HTML site, captured frame-perfect with Playwright. This is what sells: the client sees *their actual new site* moving.
- **B-roll** — Hyperframes AI shots used as the opener, one transition, and the closer.

### 7.1 Shot list

| # | Time | Source | Shot |
|---|---|---|---|
| 01 | 0.0–4.0 | Hyperframes | Slow push-in on a Dallas roofline at dawn, mist burning off, sun cresting the ridge. Title card fades in: **NEW VIEW ROOFING** / *Dallas–Fort Worth*. |
| 02 | 4.0–9.0 | Capture | Hero section resolves from 1.06× scale + 4px blur to sharp. Headline words rise in sequence, 60ms stagger. Hold. |
| 03 | 9.0–13.0 | Capture | Eased scroll to the trust band. Stats count up: 25+ · Top 3% · 4.9★ · 650+. Hairlines draw in left-to-right. |
| 04 | 13.0–18.0 | Capture | Services grid. Cards enter with 24px rise + fade, 80ms stagger. Cursor glides over the Residential card, image scales to 1.04×. |
| 05 | 18.0–21.0 | Hyperframes | Hard cut to the storm sky, fast push toward the shelf cloud. Low sub-impact hit. Sets up the storm section. |
| 06 | 21.0–27.0 | Capture | Storm & insurance section on `--ink`. The 5-step claim process reveals step by step, connecting line drawing between them. |
| 07 | 27.0–33.0 | Capture | **Before/After slider.** Handle drags itself 85% → 15% → 50%, revealing the new roof. *This is the emotional peak — give it room.* |
| 08 | 33.0–38.0 | Capture | Project grid builds in a masonry cascade, then a slow 1.03× push on the whole grid. |
| 09 | 38.0–43.0 | Capture | Reviews wall. Cards fade up in a staggered wave, star rows animating fill left-to-right. |
| 10 | 43.0–47.0 | Capture | FAQ accordion: one item opens, answer height-animates, chevron rotates. Fast and light — shows interactivity. |
| 11 | 47.0–52.0 | Capture | Final CTA form. Step 1 fields fill with ghost-typed text, button presses, Step 2 slides in, success checkmark draws. |
| 12 | 52.0–55.0 | Capture | Smooth pull back to a zoomed-out full-page view of the entire homepage. |
| 13 | 55.0–58.0 | Hyperframes | Match-cut back to the **exact opening frame** of shot 01. Logo + (469) 716-5859 fade out as it returns. |

**Loop seam requirement:** shot 13's final frame must be pixel-identical to shot 01's first frame. Render both from the same Hyperframes generation and reverse the tail. `assemble.sh` must verify this programmatically and fail loudly if the frames differ.

### 7.2 Hyperframes prompts

**`motion/hyperframes/prompts/shot-01-dawn-push.txt`**

```
Cinematic slow dolly push-in toward the roofline of an upscale Dallas two-story
brick home at dawn. Thin mist drifting low across the shingles. The sun just
cresting the ridge line, warm rim light growing across the roof plane. Big soft
Texas sky. Camera moves forward very slowly and steadily, no shake. 35mm, f/2.8,
shallow depth. Warm neutral grade, lifted blacks, subtle film grain.
4 seconds, 24fps, no text, no logos, no people.
```

**`motion/hyperframes/prompts/shot-05-storm-push.txt`**

```
Fast cinematic push toward a towering Texas supercell shelf cloud rolling over
flat suburban rooftops on the horizon. Deep blue-grey cloud structure with a
thin band of warm light along the bottom. Clouds churning in time-lapse motion.
Camera accelerates forward then decelerates hard. Dramatic, serious, no rain
on lens. 24mm wide. 3 seconds, 24fps, no text, no logos, no people.
```

**`motion/hyperframes/prompts/shot-13-dawn-return.txt`**

```
Cinematic slow dolly pull-back from an upscale Dallas two-story brick home
roofline at dawn, mist drifting, warm sun low on the ridge. Camera retreats
slowly and steadily to a wide establishing frame. Identical location, light and
composition to a forward push-in of the same scene so the two can be cut
together seamlessly. 3 seconds, 24fps, no text, no logos, no people.
```

**`motion/hyperframes/prompts/shot-xx-texture-insert.txt`** — optional 1.5s inserts between sections

```
Extreme macro slow drift across charcoal asphalt shingle granules, raking warm
light moving slowly left to right revealing the mineral texture. Near-abstract,
shallow focus, calm. 2 seconds, 24fps, no text, no logos.
```

---

## 8. Audio — `motion/audio/generate_audio.py`

Pure Python with `numpy` + `scipy.io.wavfile`. 48kHz / 24-bit stereo. No external samples, no licensing exposure.

### 8.1 Stems to generate

| File | Length | Method |
|---|---|---|
| `pad_ambient_cmin_60s.wav` | 60s loop | Four detuned saw oscillators on C2/G2/Eb3/Bb3, slow LFO on a 2-pole lowpass (0.05Hz), long reverb via convolution with a synthesized exponential-decay impulse. −22 LUFS. The emotional bed. |
| `sub_pulse_60s.wav` | 60s loop | Sine at 55Hz with a slow 8-bar swell envelope, gentle saturation. Felt, not heard. |
| `riser_4s.wav` | 4s | Filtered white noise with exponentially rising highpass 200Hz→8kHz + pitch-rising sine sweep. Leads into shot 05. |
| `impact_sub.wav` | 1.2s | 60Hz sine with fast pitch-drop envelope + short noise transient, heavy lowpass. Fires on the storm cut at 18.0s. |
| `whoosh_short.wav` | 0.6s | Bandpass-swept pink noise, panned L→R. Section transitions. |
| `whoosh_long.wav` | 1.4s | Same, slower sweep, wider stereo. Big scroll moves. |
| `ui_tick.wav` | 60ms | 2kHz sine burst, 5ms attack, 50ms exponential decay, −3dB. Count-up digits and card reveals. |
| `ui_click_soft.wav` | 90ms | Short filtered noise burst + 800Hz body. Button presses in shot 11. |
| `slider_drag.wav` | 2.5s | Low-amplitude filtered noise, amplitude tied to the slider position curve. Before/after reveal. |
| `success_chime.wav` | 1.8s | Three sine partials (C5, E5, G5), staggered 40ms onsets, 1.5s decay, light reverb. Form success. |
| `amb_suburban_loop.wav` | 30s loop | Layered pink noise shaped to a distant-traffic spectrum + sparse synthesized bird chirps (FM sine bursts at randomized intervals). −34 LUFS, barely present. The "busy" ambience. |
| `amb_rain_light_loop.wav` | 20s loop | Bandpassed white noise with randomized amplitude modulation + occasional low rumble. Under the storm section only. |

### 8.2 Mix targets

- Final master: **−14 LUFS integrated**, true peak **−1.0 dBTP**
- Pad: −22 · SFX peaks: −10 · Sub: −18
- Everything ducks 3dB under the impact hit at 18.0s

### 8.3 Silent-viewing requirement

Most people watch LinkedIn and Facebook video with sound off. Export a muted version too, and burn in subtitles from `motion/build/subtitles.srt`. **The video must work silently.**

---

## 9. Video Assembly Pipeline

### 9.1 `motion/capture/capture.mjs` — Playwright

1. Launch Chromium at 1920×1080, DPR 2, `prefers-reduced-motion: no-preference`.
2. Disable native smooth scroll. Drive `window.scrollTo()` manually from `scenes.json` with eased interpolation so the scroll is frame-deterministic.
3. Step the page one frame at a time (1/24s). Trigger scripted interactions — cursor moves, slider drag, accordion open, form fill — via injected JS at exact frame indices.
4. Screenshot each frame to `motion/capture/frames/frame_%05d.png`.

### 9.2 `motion/build/assemble.sh` — ffmpeg

```bash
# 1. frames -> A-roll
ffmpeg -framerate 24 -i frames/frame_%05d.png \
       -c:v libx264 -crf 14 -pix_fmt yuv420p aroll.mp4

# 2. concat with Hyperframes B-roll per the storyboard EDL
# 3. grade: curves + film grain + 1.5:1 letterbox
# 4. mix audio stems -> master.wav (loudnorm I=-14 TP=-1.0)
# 5. mux video + audio
# 6. VERIFY first frame == last frame (loop seam) — fail the build if not
# 7. export 9:16 crop + poster frame + muted subtitled variant
```

---

## 10. Build Requirements & Order

### 10.1 Requirements

**Responsive**
- Mobile-first. Breakpoints: 480 / 768 / 1024 / 1280.
- Sticky mobile action bar below 768px: Call · Text · Free Inspection.

**Forms**
- Two-step inspection form, inline validation, clear success state.
- Honeypot field + time-trap spam protection.
- No backend — log the payload to console and show the success state.

**Schema**
- `FAQPage` JSON-LD for the 25 grouped questions.
- `LocalBusiness` / `RoofingContractor` with address, phone, hours, geo, `aggregateRating`.
- `BreadcrumbList`.

**Interaction**
- Before/After drag slider: mouse, touch, and keyboard (arrow keys) accessible.
- Scroll reveals via `IntersectionObserver`: 24px rise + fade, 80ms stagger.
- Stat count-up on the trust band, tabular numerals.
- **Every animation wrapped in a `prefers-reduced-motion` guard.**

**Accessibility — non-negotiable**
- Real semantic HTML (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`).
- Visible focus rings, skip-to-content link.
- Minimum 4.5:1 contrast on all text.
- `aria-expanded` on accordions, `aria-live` on form status.
- Alt text on every image.
- **No accessibility overlay widget.** Reframe its removal as a liability fix.

**Performance**
- `<img>` with explicit `width`/`height` to prevent CLS.
- `loading="lazy"` below the fold, `fetchpriority="high"` on the hero.
- `srcset` + AVIF/WebP generated by `scripts/optimize-images.mjs`.
- **Zero third-party scripts on first load.**
- Instagram embed and Google Map behind a click-to-load facade.

**Images**
- Use the exact filenames from §6. Where a file does not exist yet, reference the correct path and render a labelled placeholder block showing the filename and intended dimensions.

### 10.2 Build order — show each stage before moving on

1. `tokens.css` + `base.css` + fonts
2. Sticky header + mobile drawer
3. Hero
4. Trust band + badges
5. Services
6. Storm & insurance
7. Process timeline
8. Proof — before/after slider + project grid
9. About / Values
10. Financing
11. Service areas + SVG map
12. Reviews wall
13. FAQ accordions + schema
14. Final CTA form
15. Footer + mobile sticky bar
16. `free-inspection.html`
17. `scripts/optimize-images.mjs`
18. `motion/capture/capture.mjs` + `scenes.json`
19. `motion/audio/generate_audio.py`
20. `motion/build/assemble.sh`
21. `README.md` + `docs/`

---

## 11. Future Scope — Do Not Build, Note in `docs/proposal.md`

These turn a one-off redesign into a retainer, which is where the real money is.

- **A dedicated Facebook ad landing page per campaign** — storm damage / free inspection / financing. Message match alone typically moves conversion rate more than the entire homepage redesign.
- **Core Web Vitals remediation.** Pull the PageSpeed numbers before the call. The Instagram embed and map iframe are almost certainly the main offenders.
- **Google review automation.** They have 650+ reviews and display two. Pull live reviews via the Places API into a self-updating review wall.
- **Real project photography system.** Give the crew a 5-shot checklist — before wide, before detail, during, after wide, after detail — and a shared folder. Three months of that and the proof section builds itself. Sell this as a recurring service.
- **City landing pages** — Plano, Frisco, McKinney, Allen, Southlake, Arlington, Fort Worth. Each with local reviews and projects. Pure organic lead flow.
- **Click-to-text / SMS lead capture.** Roofing leads convert far better by text than by form.
- **Instant quote estimator.** Roof size from address + material choice → ballpark range. Enormous lead magnet in this vertical.
- **AI search visibility.** `llms.txt`, entity markup, FAQ structuring so they get cited when someone asks ChatGPT or Google AI "best roofer in Dallas." Nobody else is pitching them this.
- **Remove the accessibility overlay.** Position it as removing a legal liability, not deleting a feature.

---

## 12. Reference — Source Content Inventory

Everything below is verbatim from the current site. Use it. Do not rewrite the insurance language — it is deliberately hedged for compliance.

### 12.1 Positioning lines

- "WE PROVIDE FULL-SCALE RESIDENTIAL, COMMERCIAL AND INDUSTRIAL ROOFING SERVICES"
- "YOUR DALLAS-FORT WORTH ROOF REPLACEMENT EXPERTS"
- "A VETERAN-OWNED, FAMILY-OPERATED DALLAS ROOFING CONTRACTOR"
- "Learn More About Our Free Roof Inspections!"
- "FREE INSPECTION within 24 hours of submitting request"

### 12.2 About copy (verbatim)

> New View Roofing is a locally-owned and -operated business that offers a customer-focused team with over 25 years of roofing and home remodeling experience. We provide full-scale residential, commercial and industrial roofing services throughout the North Dallas-Fort Worth Metroplex.
>
> We strive to operate far beyond the normal expectations of what a roofing contractor provides. New View Roofing stands out with hassle-free services, a strong knowledge base, elevated business standards and exceptional customer care. What does that mean for you? It means we offer great customer service, we stand behind our work, we do what we say we are going to do, and we show up to appointments on time!

### 12.3 Values (verbatim)

- **Fairness** — "We believe fairness is as simple as do unto others. We strive to create win-win solutions for everyone."
- **Accountability** — "We take pride in using quality materials and demonstrating exceptional workmanship for all types of projects."
- **Quality** — "We take responsibility for our work and adapt to unforeseen challenges to deliver the best results across the board."
- **Service** — "We strive to exceed our customers' expectations by providing quality service and communication."

> **Note:** the Accountability and Quality descriptions appear swapped on the live site — the Accountability text describes quality materials and the Quality text describes taking responsibility. Flag this to the client; do not silently fix it.

### 12.4 Services intro (verbatim)

> As a Certified GAF Master Elite® Contractor, New View Roofing has met strict business standards and undergoes regular training and recertification to keep up-to-date with the industry's best practices. Master Elite status puts us in the top 3% of all roofing companies in the country! Working with a GAF Master Elite contractor means you will receive the best workmanship for your project. In addition to roofing, we also offer many other exterior services to repair storm damage.

### 12.5 The 11-step process (free-inspection page, verbatim — condense to 5 for the homepage)

1. In most cases, an estimate can be scheduled within 24 hours of receiving your request via phone or online.
2. A certified New View Roofing project manager will listen to your needs and do an exterior inspection of your property. If the work will involve storm damage repairs, he will inspect your exterior for storm-related damage.
3. The project manager will formulate a plan for repair and explain his recommendations.
4. If you decide to proceed with the work, he will review important aspects of the contract and help you select from the different styles and materials available. He will answer any questions you have.
5. If you choose to file an insurance claim, your project manager can help explain the process and provide documentation related to the observed roof damage. He may be available during the adjuster's visit to help document observed roof conditions and answer questions about the project scope.
6. Once you receive paperwork related to an insurance claim, your project manager will review the paperwork and identify any items that may require clarification or further discussion and provide an agreement of the work to be completed.
7. New View Roofing will review all line items on the Insurance Statement of Loss Paperwork. Throughout the process, we may submit supplemental documentation or invoices to the insurance company for review when additional covered damage is identified for repairs needed to complete the project in accordance with the approved scope of work.
8. Your project manager will coordinate with you to schedule your new installation or repair. Our office personnel will also let you know if weather or other factors affect the status of your job.
9. If the job involves an insurance claim, your project manager will coordinate the work in accordance with the approved project scope and applicable agreements.
10. On the installation date, our experienced roofing contractors will arrive on time to complete the work. We take pride in using quality materials and demonstrating exceptional workmanship for all types of projects.
11. When the job is complete, your project manager will review the work with you and answer any questions that you may have.

Closing line: "Upon receipt of payment, all warranty papers and receipts are sent along with our thanks for choosing New View Roofing as your roofing company!"

### 12.6 The 25 FAQ questions — group into 5 accordions

**Before You Start**
- Do I Need A New Roof?
- Tips on How to Choose a Roofing Contractor
- When is the Best Time of Year to Get a New Roof in DFW?
- Is a Permit Required for a Roof Replacement?
- 10 Questions to Ask Roofing Experts After a Roof Inspection

**Inspections & Damage**
- What to Expect From a Free Roof Inspection in Dallas
- How Do I Know If I Have Hail Damage?
- Common Roof Structure Issues
- Roof Structure Repair: What You Need to Know
- What Do I Do If My Roof Was Improperly Installed?
- How do I Find Out When A Roof Was Replaced On A Specific House?

**Insurance & Cost**
- Will Insurance Cover a 20-Year-Old Roof?
- Understanding Roof Insurance Coverage for a Roof Replacement
- How a Roofing General Contractor Can Save You Time and Money
- Does New View Offer Any Special Offers?
- Do Your Products Have Warranties?

**Materials & Systems**
- Getting to Know Your Roofing System
- The Anatomy of a Complete Roofing System
- Discover the Best Roofing Material for Your Dallas Home
- How To Maintain An Asphalt Roof
- TPO V PVC?
- Metal Roofing Myths Debunked
- Benefits Of Installing Seamless Gutters?
- Protect Your Investment with the Right Commercial Roofing System

**Working With Us**
- What Will My Roof Look Like?

### 12.7 Inspection FAQs (verbatim answers — use on `free-inspection.html`)

**Why Should I Get a Free Roof Inspection?**
> Let's say one of Texas' powerhouse storms barrels through the community and your home is hit with hailstone that are a half inch in diameter. Documentation of your roof's condition before a storm may be helpful during the insurance claims process. Coverage determinations are made by the insurance carrier based on policy terms, documented damage, and other claim-specific factors. Documentation from a roof inspection may help establish the condition of your roof at the time of the inspection.
>
> You should also get your roof inspected when you suspect that your roof has been damaged.

**When Should I Get a Free Roof Inspection?**
> You should get a roof inspection annually. Even before you believe there is damage, you should get a free roof inspection. Not only can we identify minor issues that may require attention, but annual roof inspections can help document the condition of your roof and identify potential maintenance issues.

**Can I get a Quote During My Free Roof Inspection?**
> Yes. We can give you a better idea of how long your roof replacement will take and give you an estimate of costs during a free roof inspection.

### 12.8 Real reviews — use these, no duplicates

| Reviewer | Source | Review |
|---|---|---|
| Todd Fariss | Google | "We had roof leaks near the entryway of out home and in our garage. Andy and Mike came out, assessed the problems and prepared a detailed report, explaining the issues and the required repairs. Throughout the repair process, they called daily with updates. Professional work at a great price. Would highly recommend." |
| Nicole Beck | Google | "Burton as very professional and provided quality customer service. The entire crew was on time, considerate of children living in the house and polite. They covered the pool while working and cleaned up well to ensure no nails were left. Very please with their work." |
| Matthew Carter | Google | "New View Roofing was great. I couldn't be happier. Their team was on time quick, efficient and under budget. I was in a time crunch and they were able to accommodate our busy schedule. They met and exceeded all expectations." |
| Benjamin K. | Google | "I have use New View roofing the last two times I've needed work done on my roof! Nathan Sundberg has made the whole process easy, affordable, and stress free! I wouldn't think of asking any other company or person to come work on my roof!!" |
| Mir A. | Google | "I would highly recommend Newview roofing, especially Scott Berlin and his team, for any roofing needs. From start to finish, they were professional, efficient, and extremely knowledgeable." |

Pull at least one more from their live Google profile to reach six. Light typo correction is acceptable; do not rewrite the substance.

### 12.9 Service areas

**Primary DFW:** Allen, Arlington, Carrollton, Dallas, Flower Mound, Frisco, Fort Worth, Garland, Grand Prairie, Grapevine, Irving, Lewisville, Little Elm, McKinney, Plano, Richardson, Southlake, The Colony

**Currently listed but geographically out of market — flag to client:** Austin TX, Cleveland OH, Stillwater OK

---

## 13. Deliverables Checklist

- [ ] `index.html` — all 14 sections, responsive, accessible, schema'd
- [ ] `free-inspection.html` — dedicated ad landing page
- [ ] Full `assets/css/` token-driven stylesheet set
- [ ] Full `assets/js/` vanilla module set
- [ ] Placeholder blocks for all 34 image slots, correctly named and sized
- [ ] `map-dfw-base.svg` built in code
- [ ] `scripts/optimize-images.mjs`
- [ ] `motion/capture/capture.mjs` + `scenes.json`
- [ ] `motion/audio/generate_audio.py` — all 12 stems
- [ ] `motion/build/assemble.sh` with loop-seam verification
- [ ] `motion/storyboard.md`
- [ ] `README.md`
- [ ] `docs/audit.md`, `docs/proposal.md`, `docs/content-map.md`
- [ ] Lighthouse: 95+ across Performance, Accessibility, Best Practices, SEO on mobile

---

*End of brief.*
