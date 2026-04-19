# Nexar Design

## 1. Visual Theme & Atmosphere

VERA (Visual Edge Real-world Architecture) is Nexar's verification platform brand -- a dark-mode-native design language built on deep space backgrounds where content emerges through layered particle atmospherics. The overall impression is cinematic depth: every page feels like peering into a data-rich cosmos, with pre-rendered 3D particle art providing organic texture behind crisp, high-contrast typography. This is not a dark theme applied to a light design -- darkness is the native medium, and light is used surgically through teal and purple accents that evoke verification, trust, and intelligence.

The typography system pairs two custom typefaces: Hellix for display headings (tight-tracked, authoritative) and Roobert for body text and UI (generous line-height, approachable). Hellix at 600 weight with aggressive negative tracking creates compressed, engineered headlines. Roobert at 400 weight with relaxed 1.65 line-height balances density with readability. The contrast between the two creates a clear visual hierarchy without relying on size alone.

The color system is strictly controlled: a near-black background (`#060612` -- not pure black, but deep space with a blue undertone) anchors everything. Only two accent colors exist -- teal (`#23e7d8`) and purple (`#a183fa`) -- used for CTAs, data highlights, atmospheric gradients, and section alternation. No warm colors are permitted. No orange, red, gold, or amber -- ever. This constraint creates a cold, precise, trustworthy atmosphere that reinforces VERA's verification narrative.

Every section is immersive and full-bleed. No narrow centered containers. Content sits over layered atmospheric stacks: radial gradient glows, pre-rendered particle PNG imagery at low opacity, and SVG noise textures. The particle images dissolve into the background via CSS masks -- they feel like atmosphere, not cropped photos.

**Key Characteristics:**
- Dark-mode-native: `#060612` (Deep Space) background with blue undertone
- Two custom typefaces: Hellix (display, weight 600) and Roobert (body, weight 400)
- Aggressive negative letter-spacing on display text (-1.76px at hero scale)
- Two-accent system: teal `#23e7d8` + purple `#a183fa` -- the only chromatic colors
- No warm colors: orange, red, gold, amber are forbidden
- Pre-rendered 3D particle art in every section (opacity 0.3 sections, 0.35 heroes)
- Layered atmospheric stack: radial glow + particle image + SVG noise + content
- Full-bleed immersive sections with clamp-based responsive padding
- Glass morphism for cards and navigation (backdrop-filter blur)
- Scroll-triggered reveal animations (fade-up, 0.8s ease-out)
- Text readability enforced: minimum 0.60 opacity for any text, 0.78 for body copy

## 2. Color Palette & Roles

### Background Surfaces
- **Deep Space** (`#060612`): Primary page background. Near-black with subtle blue undertone -- the canvas for all VERA pages.
- **Panel Background** (`oklch(10% 0.02 280)`): Card and panel surfaces. One step above Deep Space.
- **Alternate Section** (`oklch(13% 0.02 280)`): Alternating section backgrounds for rhythm.
- **Glass Fill** (`rgba(255,255,255,0.035)`): Translucent glass card fill, always with backdrop blur.
- **Alt Section Tint** (`rgba(255,255,255,0.015)`): Barely-visible surface lift for `.alt` sections.

### Text & Content
- **Heading White** (`rgba(255,255,255,0.92)`): Primary heading color. Bright but not pure white.
- **Body Text** (`rgba(255,255,255,0.78)`): Standard body copy. This is the MINIMUM for readable body text -- never go below.
- **Dim Text** (`oklch(68% 0.02 280)`): Labels, captions, footnotes. Never below 68% lightness.
- **Stat Labels** (`rgba(255,255,255,0.70)`): Minimum opacity for stat descriptors and secondary labels.
- **Near White** (`#fafafa`): Utility white for maximum emphasis.
- **Light Grey** (`#e8e8e8`): Subtle borders, secondary text on dark backgrounds.

### Brand Accents (ONLY THESE)
- **Teal / Green** (`#23e7d8`, Pantone 3255 C): Primary CTA, counters, active states, data highlights, chapter labels. The "action" color.
- **Purple** (`#a183fa`, Pantone 2655 C): Atmospheric gradients, particle tints, secondary accent, alternate stat colors. The "atmosphere" color.
- **Light Purple** (`#c084fc`): Tertiary accent. Replaces any legacy red/orange usage.

### Tint Scales
- **Teal tints**: `#23e7d8` (100%) > `#4fece0` (80%) > `#7bf1e8` (60%) > `#a7f5ef` (40%) > `#d3faf7` (20%)
- **Purple tints**: `#a183fa` (100%) > `#b49cfb` (80%) > `#c7b5fc` (60%) > `#d9cdfd` (40%) > `#ece6fe` (20%)
- **Grey tints**: `#e8e8e8` (100%) > `#ededed` (80%) > `#f1f1f1` (60%) > `#f6f6f6` (40%) > `#fafafa` (20%)

### Border & Divider
- **Glass Border** (`rgba(255,255,255,0.07)`): Standard card and section borders.
- **Section Divider** (`rgba(255,255,255,0.07)`): 1px horizontal dividers between sections.

### Forbidden Colors
- **No orange**: not `#FF6B2B`, not `#d4a853`, no warm yellows
- **No red**: not `#FF3B30`, no crimson, no scarlet (except semantic error states in forms)
- **No gold**: not `#d4a853`, no amber, no warm metallics
- **No arbitrary accents**: only the brand palette above
- If legacy code contains `--gold`, `--red`, or warm variables, remap: `--gold` > `#23e7d8`, `--red` > `#c084fc`

### CSS Custom Properties

```css
/* Backgrounds */
--bg: #060612;
--bg-panel: oklch(10% 0.02 280);
--bg-alt: oklch(13% 0.02 280);
--glass-bg: rgba(255,255,255,0.035);
--glass-border: rgba(255,255,255,0.07);
--glass-blur: 20px;

/* Brand Accents */
--green: #23e7d8;
--teal: #23e7d8;
--purple: #a183fa;
--light-purple: #c084fc;

/* Text */
--white: #fafafa;
--light-grey: #e8e8e8;
--text: oklch(88% 0.01 280);
--text-bright: rgba(255,255,255,0.92);
--text-mid: rgba(255,255,255,0.78);
--text-dim: oklch(68% 0.02 280);

/* Spacing */
--section-pad-x: clamp(28px, 8vw, 140px);
--section-pad-y: clamp(80px, 12vh, 160px);
```

## 3. Typography Rules

### Font Families
- **Display**: `Hellix, system-ui, -apple-system, sans-serif` -- used for all headings (H1, H2). Custom typeface with geometric character.
- **Body / UI**: `Roobert, system-ui, -apple-system, sans-serif` -- used for body text, labels, stats, navigation. Friendly geometric sans.
- **Stack**: `Hellix, Roobert, system-ui, -apple-system, sans-serif`

### Hierarchy

| Role | Font | Size | Weight | Line Height | Letter Spacing | Notes |
|------|------|------|--------|-------------|----------------|-------|
| H1 Hero | Hellix | `clamp(36px, 6vw, 88px)` | 600 | 1.05 | -1.76px | Maximum impact headlines |
| H2 Section | Hellix | `clamp(28px, 4vw, 64px)` | 600 | 1.1 | -1.28px | Section headlines |
| Body Large | Roobert | 22px | 400 | 1.6 | normal | Introduction text, lead paragraphs |
| Body | Roobert | 18px | 400 | 1.65 | normal | Standard reading text |
| Chapter Label | Roobert | 13px | 400 | -- | 0.16em | Always uppercase, brand color (teal/purple) |
| Stat Value | Roobert | `clamp(24px, 3.5vw, 44px)` | 600 | 1.0 | tight | Large display numbers |
| Stat Label | Roobert | 14px | 400 | 1.4 | normal | Stat descriptors |

### Principles
- **Hellix = authority**: Tight-tracked, compressed headings that feel engineered. Always weight 600, always negative letter-spacing.
- **Roobert = approachability**: Generous line-height (1.6+), relaxed tracking. The readable workhorse for everything that isn't a headline.
- **Two fonts only**: No monospace, no decorative, no fallback mixing. Hellix for display, Roobert for everything else.
- **No emojis**: Ever. Use text labels, CSS shapes, or SVG icons instead.
- **No em dashes**: No `--` or `---` rendering as em dashes. Use en dashes or rewrite.

## 4. Component Stylings

### Navigation (Sticky)
- Background: glass (`backdrop-filter: blur(20px)`, translucent dark)
- Logo: Nexar logotype image (`nexar-logo-white.png`), 22px height -- NEVER bold text saying "NEXAR"
- Position: sticky top, z-index 10
- Border bottom: `1px solid rgba(255,255,255,0.07)`

### Buttons

**Primary CTA**
- Background: `#23e7d8` (teal)
- Text: `#060612` (dark)
- Padding: 12px 24px
- Radius: 6px
- Use: Primary actions, conversion CTAs

**Ghost Button**
- Background: transparent
- Text: `rgba(255,255,255,0.78)`
- Border: `1px solid rgba(255,255,255,0.07)`
- Padding: 12px 24px
- Radius: 6px
- Use: Secondary actions

### Glass Cards
- Background: `rgba(6,6,18,0.6)`
- Backdrop filter: `blur(16px)`
- Border: `1px solid rgba(255,255,255,0.07)`
- Radius: 8px
- Use: Content cards, feature highlights

### Stat Display
- `.tab-stat .n`: Large display number in teal (`#23e7d8`) or purple (`#a183fa`)
- `.tab-stat .l`: Descriptor label below at `rgba(255,255,255,0.70)` minimum
- Layout: flex row with `clamp(24px, 4vw, 48px)` gap

### Tab Navigation
- Background: `rgba(7,12,24,0.85)` with backdrop blur
- Active tab: teal text + teal underline
- Inactive: `rgba(255,255,255,0.70)`

### Chapter Labels
- Font: Roobert 13px, uppercase, letter-spacing 0.16em
- Color: brand color (teal `#23e7d8` or purple `#a183fa`) -- NEVER white-with-opacity
- Format: `01 -- Section Name` (with en dash)

### Blockquote / Insight
- Left border: 3px accent (teal or purple)
- Slightly elevated background
- Use: key takeaways, highlighted quotes

## 5. Layout Principles

### Immersive Full-Bleed Sections
Every section uses full-bleed immersive layout -- NOT a narrow `.container` wrapper:

```html
<div class="tab-section">
  <div class="tab-bg">
    <div class="tab-glow"></div>
    <img class="tab-particle-img" src="..." alt="" loading="lazy">
    <svg class="tab-noise">...</svg>
  </div>
  <div class="tab-content-inner">
    <div class="tab-chapter teal">01 -- Section Name</div>
    <div class="tab-headline">The Big Statement</div>
    <div class="tab-copy">Narrative paragraph...</div>
  </div>
</div>
```

### Atmospheric Stack (per section)
Every section has a 4-layer atmospheric background:
1. **Radial gradient glow** (bottom): teal or purple, low opacity (0.04-0.08), blur 80px
2. **Particle image** (middle): pre-rendered 3D art, opacity 0.3, absolute positioned
3. **SVG noise texture** (top): `feTurbulence` fractalNoise, opacity 0.04
4. **Content** (foreground): positioned relative, z-index 3

Alternate glow colors between sections: teal > purple > teal.

### Spacing System
- Section padding X: `clamp(28px, 8vw, 140px)`
- Section padding Y: `clamp(80px, 12vh, 160px)`
- Content inner max-width: 720px (standard), 960px (wide)
- Stat row gap: `clamp(24px, 4vw, 48px)`

### Layout Patterns

| Pattern | Structure | Use |
|---------|-----------|-----|
| Hero | Full viewport, centered headline, particle bg at 0.35 opacity | Page opening |
| Text + Atmosphere | Copy left (720px max), particle right (55% width, 0.3 opacity) | Narrative sections |
| Big Stat | Large display numbers in flex row, no card borders | Data highlights |
| Blockquote | Left accent border, elevated bg | Key takeaways |
| Closing CTA | Centered heading + teal primary button | Conversion |

### Section Dividers
- 1px horizontal line: `rgba(255,255,255,0.07)`
- Between every section
- No visible gap -- divider sits flush

## 6. Depth & Elevation

| Level | Treatment | Use |
|-------|-----------|-----|
| Base (Level 0) | `#060612` bg, no shadow | Page background |
| Section Alt (Level 1) | `rgba(255,255,255,0.015)` bg tint | Alternating sections |
| Glass Card (Level 2) | `rgba(6,6,18,0.6)` + `blur(16px)` + `1px rgba(255,255,255,0.07)` border | Cards, panels |
| Panel (Level 3) | `oklch(10% 0.02 280)` solid bg | Elevated panels |
| Nav (Level 4) | Glass + `backdrop-filter: blur(20px)` + sticky | Fixed navigation |

**Depth Philosophy**: Elevation is communicated through translucency and blur rather than shadows. Glass morphism (backdrop-filter blur + semi-transparent fills) creates layering. The background particle imagery shows through glass surfaces, reinforcing the atmospheric depth. Borders are always semi-transparent white -- never solid dark lines.

## 7. Visual Imagery -- Particle Art System

Every section uses **pre-rendered 3D particle images** for atmospheric depth. These are NOT CSS-generated particles -- they are high-quality rendered PNGs.

### Bundled Particle Library (15 images)

This repo includes 15 curated particle images in `particles/` covering all major categories. Use these as the default -- no external dependencies required.

| File | Category | Best For |
|------|----------|----------|
| `particles/02-data-cloud.png` | Abstract | Network sections, scattered teal-purple cloud |
| `particles/05-intersection-vehicles.png` | Vehicles | Safety/trust sections, busy intersection |
| `particles/07-road-map.png` | Infrastructure | Solutions sections, topographic terrain peaks |
| `particles/12-data-visualization.png` | Panoramic | Technical sections, ultrawide teal-purple cloud |
| `particles/13-giant-cloud.png` | Abstract | Scale/impact sections, massive particle mountain |
| `particles/brand-data-paths.png` | Abstract | Flow/pipeline sections, multi-color data paths |
| `particles/collision-wonder.png` | Vehicles | Safety sections, two particle cars colliding |
| `particles/data-sphere-hero.png` | Panoramic | Hero sections, ultrawide purple-gold-teal cloud |
| `particles/dna-growth-cta.png` | Organic | Closing/CTA sections, organic growth |
| `particles/exec-data-cloud.png` | Abstract | Hero sections, green-teal-purple cloud on grid |
| `particles/exec-data-flow.png` | Data | Data sections, cloud with flow lines and labels |
| `particles/road-map-belief.png` | Infrastructure | Platform sections, terrain with depth-of-field |
| `particles/sprint-infrastructure.png` | Infrastructure | Immersive sections, teal-purple aurora landscape |

**Usage in HTML:**
```html
<img class="tab-particle-img" src="particles/01-data-particle.png" alt="" loading="lazy">
```

### Extended Library (Nexar Internal)

Nexar team members with a `@getnexar.com` Google account have access to the full **Particle Gallery** with 219+ images, searchable by keyword and category.

| Resource | URL |
|----------|-----|
| Gallery UI | `https://particle-gallery.corp.nexars.ai` |
| Integration Guide | `https://particle-gallery.corp.nexars.ai/guide` |

**API endpoints** (browser-access only, behind IAP):

| Endpoint | Use |
|----------|-----|
| `GET /api/search?q=KEYWORD&limit=5` | Search by keyword |
| `GET /api/random?count=4&category=abstract` | Random particles |
| `GET /api/file/{ID}` | Image file (signed URL redirect) |
| `GET /api/categories` | List categories with counts |

**Programmatic usage** (for dynamic variety):
```javascript
async function loadParticles() {
  const sections = document.querySelectorAll('.tab-particle-img');
  try {
    const resp = await fetch(`https://particle-gallery.corp.nexars.ai/api/random?count=${sections.length}`);
    const data = await resp.json();
    if (data.images) {
      data.images.forEach((img, i) => {
        if (sections[i]) sections[i].src = img.imageUrl;
      });
    }
  } catch {
    // Gallery unavailable -- bundled particles already set as src fallback
  }
}
```

**Recommended pattern**: Set bundled particle paths as the default `src`, then optionally upgrade to gallery images via JS. This way pages always work, with richer variety when the gallery is available.

### Image Rules
- Use `<img>` tags (not CSS `background-image`) for loading control
- Section particles: `opacity: 0.3` -- heroes: `opacity: 0.35`
- Position: `absolute` inside atmospheric stack, `object-fit: cover`
- **Edges must dissolve**: Apply CSS `mask-image` with radial or linear gradient so images fade into the background. Example: `mask-image: radial-gradient(ellipse 80% 70% at 70% 50%, black 30%, transparent 100%);`
- Subtle ambient animation: `@keyframes pulse` (scale/opacity breathe, 7s ease-in-out infinite)
- `loading="lazy"` on all particle images
- **NEVER repeat the same image in consecutive sections**
- **EVERY section must have a particle image** -- no empty backgrounds

## 8. Animation & Motion

### Scroll Reveal
- Class: `.tab-reveal` on any element that should animate in
- Trigger: IntersectionObserver at 0.15 threshold
- Animation: fade-in + translateY(24px), 0.8s ease-out
- One-shot: unobserve after first intersection

### Ambient Loops
- `pulse`: Subtle scale/opacity breathe for particle images (7s ease-in-out infinite)
- `ring`: Expanding ring from center for glow elements
- `hint`: Attention-draw for scroll indicators

### Motion Rules
- Animations are subtle, never flashy
- Reveal duration: 0.6-1.2s
- Loop duration: 3-8s
- Easing: ease-out for reveals, ease-in-out for loops
- No canvas or WebGL in standard pages -- use pre-rendered imagery with CSS animation

## 9. Responsive Behavior

### Fluid Sizing
VERA uses `clamp()` for all major measurements rather than breakpoints:

| Element | Minimum | Preferred | Maximum |
|---------|---------|-----------|---------|
| H1 Hero | 36px | 6vw | 88px |
| H2 Section | 28px | 4vw | 64px |
| Stat Value | 24px | 3.5vw | 44px |
| Section Pad X | 28px | 8vw | 140px |
| Section Pad Y | 80px | 12vh | 160px |

### Collapsing Strategy
- Particle images: maintain cover + mask at all sizes, may reduce opacity on mobile
- Stat rows: flex-wrap, stack on narrow viewports
- Content inner: max-width 720px naturally responds
- Glass nav: maintains sticky behavior at all sizes
- Section padding compresses via clamp -- no breakpoint jumps

## 10. Do's and Don'ts

### Do
- Use `#060612` as the page background -- not pure black, not arbitrary dark gray
- Use ONLY teal (`#23e7d8`), purple (`#a183fa`), and light purple (`#c084fc`) as accent colors
- Use Hellix weight 600 for all headings with negative letter-spacing
- Use Roobert weight 400 for all body text with 1.6+ line-height
- Keep body text at minimum `rgba(255,255,255,0.78)` opacity -- readability is non-negotiable
- Place a unique particle image in every section with dissolving edges via CSS masks
- Use full-bleed sections with clamp-based padding -- never narrow centered containers
- Alternate radial glow colors (teal/purple) between consecutive sections
- Use the actual Nexar logo image file -- never render the brand name as styled text
- Give every SVG noise filter a unique ID to prevent conflicts
- Use chapter labels in brand color (teal/purple), uppercase, 13px, 0.16em tracking
- Format chapter numbering as `01 -- Section Name` (en dash)

### Don't
- Don't use orange, red, gold, amber, or any warm color anywhere
- Don't use body text below `rgba(255,255,255,0.78)` opacity -- it's unreadable on dark backgrounds
- Don't use the same particle image in consecutive sections
- Don't leave any section without a particle image
- Don't use narrow `.container` wrappers -- every section is full-bleed immersive
- Don't use emojis anywhere in the interface
- Don't use em dashes (`--` or `---`) -- use en dashes or rewrite
- Don't use `oklch` lightness below 68% for any text (`--text-dim`)
- Don't use stat label text below `rgba(255,255,255,0.70)`
- Don't render "NEXAR" as bold styled text -- always use the logo image
- Don't use solid borders -- all borders are semi-transparent white
- Don't use shadows for depth -- use glass morphism (blur + translucency)

## 11. Agent Prompt Guide

### Quick Color Reference
- Page Background: Deep Space (`#060612`)
- Panel: `oklch(10% 0.02 280)`
- Heading Text: `rgba(255,255,255,0.92)`
- Body Text: `rgba(255,255,255,0.78)`
- Dim Text: `oklch(68% 0.02 280)`
- Primary Accent: Teal (`#23e7d8`)
- Secondary Accent: Purple (`#a183fa`)
- Tertiary Accent: Light Purple (`#c084fc`)
- Glass Fill: `rgba(255,255,255,0.035)`
- Glass Border: `rgba(255,255,255,0.07)`
- CTA Button: `#23e7d8` bg, `#060612` text

### Example Component Prompts
- "Create a hero section on `#060612` background. Headline at `clamp(36px, 6vw, 88px)` Hellix weight 600, line-height 1.05, letter-spacing -1.76px, color `rgba(255,255,255,0.92)`. Subtitle at 18px Roobert weight 400, line-height 1.65, color `rgba(255,255,255,0.78)`. A pre-rendered particle image at 0.35 opacity fills the background with dissolving edges via CSS mask. Teal CTA button (`#23e7d8` bg, `#060612` text, 6px radius) and ghost button (transparent, `1px solid rgba(255,255,255,0.07)`)."
- "Design a content section: full-bleed layout with `clamp(48px, 8vh, 100px)` vertical padding. Teal chapter label (`#23e7d8`, Roobert 13px uppercase, 0.16em tracking) reading `01 -- Section Name`. Hellix headline at `clamp(28px, 4vw, 52px)` weight 600. Body at 18px Roobert, `rgba(255,255,255,0.82)`, max-width 580px. Atmospheric background: radial teal glow at 0.08 opacity + particle image at 0.3 opacity + SVG noise at 0.04."
- "Build a stat row: flex layout with `clamp(24px, 4vw, 48px)` gap. Each stat has a large number in Roobert `clamp(24px, 3.5vw, 44px)` weight 600 colored `#23e7d8`, with a 14px label below at `rgba(255,255,255,0.70)`. Alternate stat colors: first teal, second purple (`#a183fa`)."
- "Create a glass card: `rgba(6,6,18,0.6)` background, `backdrop-filter: blur(16px)`, `1px solid rgba(255,255,255,0.07)` border, 8px radius."
- "Design sticky navigation: glass background with `backdrop-filter: blur(20px)`, Nexar logo image at 22px height left-aligned, z-index 10. Bottom border: `1px solid rgba(255,255,255,0.07)`."

### Iteration Checklist
1. Background is `#060612` -- not black, not gray, not arbitrary dark
2. Only teal, purple, light-purple as accents -- zero warm colors anywhere
3. Body text at 0.78+ opacity, dim text at 68%+ lightness, stat labels at 0.70+
4. Every section has a unique particle image with dissolving edges
5. Headings use Hellix 600 with negative tracking; body uses Roobert 400 with 1.6+ line-height
6. Sections are full-bleed with clamp padding -- no narrow containers
7. Logo is an image file, not styled text
8. Chapter labels use brand color (teal/purple), not white-with-opacity
9. Glass morphism for cards and nav -- no drop shadows
10. Scroll reveal animations: fade-up, 0.8s ease-out, IntersectionObserver
