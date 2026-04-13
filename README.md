# nodexbt-ui

Shared styling primitives for nodexbt projects — theme tokens, Tailwind v4 preset, `cn()` utility, and `ThemeProvider`.

## Install

```bash
npm install nodexbt-ui
```

## Usage

### 1. Import the global styles

In your app's main CSS file, replace your theme tokens with:

```css
@import "nodexbt-ui/globals.css";
```

This gives you the full Tailwind v4 `@theme inline` block, light/dark CSS variables, and base styles.

### 2. Use the utilities

```tsx
import { cn, ThemeProvider, useTheme } from "nodexbt-ui";
```

**`cn(...classes)`** — merges Tailwind classes safely (clsx + tailwind-merge):

```tsx
<div className={cn("p-4 bg-primary", isActive && "ring-2 ring-ring")} />
```

**`ThemeProvider`** — wrap your app to enable dark/light mode:

```tsx
// layout.tsx
import { ThemeProvider } from "nodexbt-ui";

export default function RootLayout({ children }) {
  return (
    <html>
      <body>
        <ThemeProvider>{children}</ThemeProvider>
      </body>
    </html>
  );
}
```

**`useTheme()`** — read or toggle the current theme:

```tsx
const { theme, setTheme } = useTheme();
```

### 3. PostCSS config (optional)

```js
// postcss.config.mjs
import { postcssConfig } from "nodexbt-ui/postcss";
export default postcssConfig;
```

## Peer dependencies

- `react` >= 18
- `react-dom` >= 18
- `tailwindcss` >= 4
