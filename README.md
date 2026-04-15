# Doorstep

A barebones SCSS framework for small web projects. Lightweight, unopinionated, and driven entirely by CSS custom properties so you can rebrand without recompiling.

## What it gives you

- A minimal modern reset
- Semantic colour tokens with automatic dark mode via `prefers-color-scheme`
- A t-shirt-sized typography and spacing scale
- Styled native form elements (inputs, textarea, select, buttons)
- A small SCSS breakpoints mixin for media queries

No utility classes. No layout helpers. Base elements only.

## Install

Clone it into your project:

```bash
git clone https://github.com/YOUR_USERNAME/doorstep.git src/styles/doorstep
```

Then in your own stylesheet:

```scss
@use "doorstep/scss";

// Override any token:
:root {
  --color-accent: #ff5a8a;
  --font-sans: "Inter", system-ui, sans-serif;
}
```

Compile with Dart Sass:

```bash
npx sass src/styles/main.scss dist/style.css
```

## Customising

Every default is a CSS variable declared in `scss/_tokens.scss`. To customise, redeclare variables in your own `:root` block *after* importing Doorstep. No SCSS recompilation is needed to rebrand — you can even flip tokens at runtime.

### Colour tokens

| Token                 | Purpose                       |
| --------------------- | ----------------------------- |
| `--color-bg`          | Page background               |
| `--color-fg`          | Body text                     |
| `--color-muted`       | Secondary text                |
| `--color-subtle`      | Subtle surface backgrounds    |
| `--color-border`      | Borders and dividers          |
| `--color-accent`      | Primary brand / link / button |
| `--color-accent-fg`   | Text on accent background     |
| `--color-danger`      | Destructive state             |
| `--color-success`     | Positive state                |
| `--color-focus`       | Focus ring colour             |

### Spacing tokens

`--space-xs` through `--space-3xl`.

### Type scale

`--text-xs` through `--text-3xl`, plus `--leading-tight`, `--leading-base`, `--leading-loose`, and `--measure` for prose line length.

## Dark mode

Automatic via `@media (prefers-color-scheme: dark)` in `_tokens.scss`. If you want a manual toggle, override the same variables inside a `.dark` selector in your own stylesheet.

## Button variants

Buttons use data attributes, not classes:

```html
<button>Primary</button>
<button data-variant="secondary">Secondary</button>
<button data-variant="ghost">Ghost</button>
```

## File layout

```
scss/
  _tokens.scss        # all CSS custom-property defaults
  _reset.scss         # minimal modern reset
  _typography.scss    # base element typography
  _forms.scss         # inputs, textarea, select, buttons
  _breakpoints.scss   # SCSS map + up()/down() mixins
  index.scss          # forwards everything
example/
  index.html          # demo page for eyeballing changes
  style.scss          # example consumer stylesheet
```

## Demo

```bash
npx sass example/style.scss example/style.css
open example/index.html
```

## Licence

MIT
