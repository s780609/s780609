---
name: design-system-clean-ui
description: Clean UI design principles based on Steve Schoger's approach. Use this skill when doing any UI/frontend design work — building landing pages, styling components, polishing layouts, or reviewing design quality.
trigger: When the user asks to design, style, build, or polish any UI component, page, or layout.
---

# Clean UI Design System

A comprehensive set of design principles for building professional, clean interfaces.
Reference these rules when making any UI/design decisions.

---

## 1. Borders & Shadows

### 1.1 Outer Ring > Solid Border

- **Never** combine `box-shadow` with `border` on the same element — it creates a muddy, dirty transition.
- Instead, remove the border entirely and use an **outer ring**: `ring-1 ring-gray-950/10` (gray-950 at 10% opacity).
- The ring sits outside the element, giving a sharper, cleaner edge that blends naturally with shadows.
- Apply this to: cards, buttons, navbars, containers — anything with a shadow.

### 1.2 Concentric Border Radius

- When a rounded container holds a rounded child element:
  - **Inner radius = Outer radius - padding**
- Example: outer `rounded-2xl` (16px) with 8px padding → inner should be `rounded-lg` (8px).
- Using the same radius on both creates an awkward visual gap at small spacing.

### 1.3 Inset Ring for Edge Definition

- On light-background containers, use `ring-1 ring-inset ring-gray-950/5` (5% opacity inset ring) instead of a traditional border.
- More subtle than a border — defines the edge without stealing visual focus from the content.

---

## 2. Typography

### 2.1 Inter Variable (Display)

- Use the **variable** version of Inter from [rsms.me](https://rsms.me/inter/), not Google Fonts.
- Enables intermediate font weights like **550** (between medium 500 and semi-bold 600).
- Disable the tailed lowercase L variant (stylistic set `ss02`) — it looks odd in certain contexts.

### 2.2 Tighten Tracking on Large Text

- Any text **24px and above**: reduce letter-spacing (`tracking-tight` or tighter).
- Larger type visually amplifies letter gaps — tightening makes headlines punchier and more compact.

### 2.3 Eyebrow Text Formula

- Small label above section headings (e.g. "Everything you need", "Get started"):
  - Font: **Geist Mono** (monospace)
  - Transform: **uppercase**
  - Spacing: **tracking-wider**
  - Size: **text-xs**
  - Color: **gray-600**
- Monospace gives these labels a refined, technical feel.

### 2.4 text-pretty vs text-balance

- `text-pretty` — prevents orphan words (single word on last line).
- `text-balance` — distributes text lines more evenly.
- Test both on each text block and pick whichever looks better in context.

### 2.5 Double Line Height for Small Text

- For 14px (`text-sm`) body/subtitle text, try line-height **28px** (2x font size).
- Sounds extreme, but gives descriptions and subtext more breathing room and readability.

---

## 3. Layout

### 3.1 Left-Align Instead of Center

- Avoid the default "everything centered" AI layout.
- Hero section: use a **split headline** layout:
  - Left column (~3/5 width): heading
  - Right column (~2/5 width): subtitle and description
  - Top-aligned
- More intentional, easier to read, stronger design presence.

### 3.2 Inline Section Headings

- Don't use the "big title + line break + subtitle" structure.
- Put heading and subtitle **on the same line**, differentiated by color and weight:
  - Title: **neutral-950, bold**
  - Subtitle: **neutral-600, medium weight**, continuing inline
- Inspired by Apple, Linear, Stripe, Adio. Works best with longer subtitle copy.

### 3.3 Max-Width in `ch` Units

- Use `ch` units for text block max-width (e.g. `max-w-[40ch]`).
- `ch` is based on the width of the `0` character — keeps comfortable reading width regardless of font size.
- Test values: try 35, 40, 45 and pick the one that feels right.

---

## 4. Components

### 4.1 Button Design

- Height: **36–38px**, controlled via padding (not fixed height).
- Shape: **pill / fully rounded** (`rounded-full`).
- Font size: **14px** (`text-sm`).
- Remove default icons — keep buttons clean and text-only unless icons add clear meaning.

### 4.2 Button Height Alignment (Ring Fix)

- A button with a ring/border will be **2px taller** than one without.
- Fix: wrap the bordered button in a `<span>` with `inline-flex p-px`, then use `calc()` to equalize visual height.
- This is a subtle but critical alignment detail.

### 4.3 Well-Styled Container (Sunken Container)

- For screenshot/demo containers in feature sections:
  - Background: **gray-950 at 2.5–5% opacity** (very faint).
  - **No border** — use inset ring at 5% opacity for edge definition.
  - Screenshot crops at the bottom (zero bottom padding, no bottom border-radius) — creates a "sitting in the container" effect.

### 4.4 Screenshots as Hero Visuals

- A high-resolution app screenshot is the simplest way to create visual impact.
- Capture at **3x resolution** for crispness on high-DPI displays.
- If you lack custom illustrations, a good screenshot beats a generic graphic every time.

---

## 5. Decoration & Polish

### 5.1 Canvas Grid (Decorative Border Grid)

- Add decorative line borders between sections across the page:
  - Horizontal lines: extend to **full viewport width**.
  - Vertical lines: stay within the **page container width**.
- Creates a refined grid framework that eliminates "template" feel.
- Inspired by Stripe, Adio, and Tailwind's official sites.
- Great substitute when you lack custom graphic assets.

### 5.2 Background Image Testimonial Cards

- Instead of avatar + quote, use an **AI-generated portrait as the card background**.
- Add a **dark gradient overlay (shim)** at the bottom so white quote text remains legible.
- Far more visually impactful than standard circular avatars.

### 5.3 Logo Cloud

- No title needed — logos are self-explanatory.
- Use **real SVG logos**, not text placeholders.
- Color: **gray-950** (remove variable opacity — keep them solid).
- Fill the container width evenly. Keep it simple — don't over-design this section.

---

## Quick Reference: Tailwind Utility Patterns

| Purpose | Pattern |
|---|---|
| Outer ring (replace border) | `ring-1 ring-gray-950/10 shadow-md` |
| Inset ring (edge definition) | `ring-1 ring-inset ring-gray-950/5` |
| Eyebrow text | `font-mono uppercase tracking-wider text-xs text-gray-600` |
| Tight heading tracking | `tracking-tight` (24px+) |
| Relaxed body line-height | `text-sm leading-7` (14px / 28px) |
| Pill button | `rounded-full px-4 py-2 text-sm` |
| Sunken container bg | `bg-gray-950/[0.025]` or `bg-gray-950/5` |
| Concentric radius | outer `rounded-2xl` + inner `rounded-lg` (difference = padding) |
| Text wrapping | `text-pretty` or `text-balance` (test both) |
| Max text width | `max-w-[40ch]` |
