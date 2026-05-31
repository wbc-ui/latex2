<p align="center">
  <img src="https://cdn.jsdelivr.net/npm/@wbc-ui/latex2/logo/latex2.svg" alt="@wbc-ui/latex2" width="220" style="max-width: 100%;"/>
</p>

<p align="center">
  <strong>Math as Data. Vue 2. LaTeX.</strong><br/>
  <em>Pass a LaTeX expression — <code>\\frac{-b \\pm \\sqrt{b^2-4ac}}{2a}</code> — and get crisp rendered math. Inline or display mode, custom macros, configurable font size. Powered by KaTeX.</em>
</p>

<p align="center">
<a href="https://www.npmjs.com/package/@wbc-ui/latex2"><img src="https://img.shields.io/npm/v/@wbc-ui/latex2?color=1976D2" alt="npm"></a>
<a href="https://www.npmjs.com/package/@wbc-ui/latex2?activeTab=versions"><img src="https://img.shields.io/npm/dm/@wbc-ui/latex2?color=1976D2" alt="downloads"></a>
<a href="https://github.com/wbc-ui/latex2/blob/main/LICENSE"><img src="https://img.shields.io/npm/l/@wbc-ui/latex2?color=blue" alt="license"></a>
<a href="https://vuejs.org"><img src="https://img.shields.io/badge/vue-2.7%2B-42b883" alt="vue"></a>
</p>

<p align="center">
  <a href="https://latex2.wbc-ui.com">📘 Docs</a> ·
  <a href="https://github.com/wbc-ui/latex2">🐙 GitHub</a> ·
  <a href="https://latex2.wbc-ui.com">▶️ Playground</a> ·
  <a href="https://wbc-ui.com">💎 Pro</a>
</p>

---

## Why?

**@wbc-ui/latex2** renders LaTeX math expressions with [KaTeX](https://katex.org/) — fast, no MathML quirks, no global setup. Pass the expression, pick inline or display mode, done.

### Render math in one line

```html
<WBLatex expression="E = mc^2" />
```

### Display mode + custom macros

```html
<WBLatex
  expression="\\RR^n \\to \\RR"
  :displayMode="true"
  :macros="{ '\\RR': '\\mathbb{R}' }"
/>
```

> **One component. One `<WBLatex>` tag.** The expression is the input. Everything is data.

---

## What is @wbc-ui/latex2?

A **Vue 2.7+ component** — `<WBLatex>` — that renders a LaTeX string to typeset math via KaTeX. Works standalone or as a plugin inside the `@wbc-ui/core2` (WBC) ecosystem.

| Prop | Type | Default | Purpose |
|---|---|---|---|
| `expression` | `string` *(required)* | — | The LaTeX source to render. |
| `displayMode` | `boolean` | `false` | Block/centered display math vs inline. |
| `fontsize` | `number` | `16` | Rendered font size (px). |
| `macros` | `object` | — | Custom macro map, e.g. `{ '\\RR': '\\mathbb{R}' }`. |
| `throwOnError` | `boolean` | `false` | Throw vs render the error in place. |
| `errorColor` | `string` | — | Color for rendered errors. |
| `minRuleThickness` / `maxSize` / `maxExpand` / `colorIsTextColor` | `number` / `boolean` | — | KaTeX passthrough options. |

**Who's it for?** Education platforms, scientific docs, technical blogs, and any app that renders formulas without bundling MathJax.

---

## Teasing Examples

### Level 1 — Inline formula
```html
<WBLatex expression="a^2 + b^2 = c^2" />
```

### Level 2 — Display mode (the quadratic formula)
```html
<WBLatex expression="x = \\frac{-b \\pm \\sqrt{b^2 - 4ac}}{2a}" :displayMode="true" />
```

### Level 3 — Inside a WBC tree
```html
<WBC :item="{
  comp: 'WBLatex',
  options: { props: { expression: '\\int_0^\\infty e^{-x^2}\\,dx = \\frac{\\sqrt{\\pi}}{2}', displayMode: true } }
}" />
```

---

## 🚀 Try it in 30 seconds

```bash
# Live interactive lab — paste any LaTeX, see it render
open https://latex2.wbc-ui.com
```

> Explore at **[latex2.wbc-ui.com](https://latex2.wbc-ui.com)** — paste an expression, toggle display mode, copy the snippet back to your project.

---

## Installation

### Prerequisites

- **Node.js** ≥ 18 · **Vue 2.7.x** (Vue 3 tracked as `@wbc-ui/latex3`)
- **[`@wbc-ui/core2`](https://www.npmjs.com/package/@wbc-ui/core2)** — optional; only needed for WBC tree integration

### npm (recommended)

```bash
npm install @wbc-ui/latex2

# Peer dependencies — install once per project
npm install vue@^2.7.16
# Optional, for WBC integration:
npm install @wbc-ui/core2
```

### Yarn / pnpm

```bash
yarn add @wbc-ui/latex2 vue@^2.7.16
pnpm add @wbc-ui/latex2 vue@^2.7.16
```

### Vue 2 plugin registration

```javascript
// main.js
import Vue from 'vue';
import WBLatexPlugin from '@wbc-ui/latex2';
Vue.use(WBLatexPlugin);
// Use <WBLatex expression="..."> anywhere in your app.
```

### Troubleshooting common install errors

| Symptom | Cause | Fix |
|---|---|---|
| Math renders as raw text | `<WBLatex>` not registered | `Vue.use(WBLatexPlugin)` in `main.js`. |
| Backslashes vanish in a JS string | `\` is a JS escape char | Double them in source: `"\\frac{a}{b}"`. |
| A command throws / shows red | KaTeX doesn't support it, or a typo | Define it via `:macros`, or check [KaTeX support](https://katex.org/docs/supported.html); set `:throwOnError="false"` to render inline. |

For worked examples, see [latex2.wbc-ui.com](https://latex2.wbc-ui.com).

---

## 💎 Free vs Pro

> **`@wbc-ui/latex2` is open-source and a complete math renderer today** — full KaTeX rendering, display/inline modes, macros, and WBC integration are free. The Pro lane follows the same open-core tiering as the underlying [`@wbc-ui/core2`](https://www.npmjs.com/package/@wbc-ui/core2) engine.

| Capability | Free | Pro |
|---|---|---|
| KaTeX rendering, inline / display mode | ✅ Full | ✅ Full |
| Custom macros, font size, KaTeX options | ✅ Full | ✅ Full |
| WBC tree integration | ✅ | ✅ |
| Depth / item caps on the rendered WBC tree | core2 free caps | ∞ (via core2 Pro) |
| Advanced engine hooks & headless extraction | — | ✅ (via core2 Pro) |

👉 **[Compare in detail →](https://wbc-ui.com/free-vs-pro)** · **[Buy Pro →](https://wbc-ui.com/pricing)**

---

## 🌐 Ecosystem

`@wbc-ui/latex2` is a sibling package in the **@wbc-ui** monorepo. Every package is published to npm and shares the same versioning line.

| Package | What it adds | Status |
|---|---|---|
| [`@wbc-ui/core2`](https://www.npmjs.com/package/@wbc-ui/core2) | "UI as Data" engine — the foundation | 🟢 GA |
| [`@wbc-ui/code2`](https://www.npmjs.com/package/@wbc-ui/code2) | JSON-driven code editor + live run | 🟢 GA |
| [`@wbc-ui/chart2`](https://www.npmjs.com/package/@wbc-ui/chart2) | ECharts integration | 🟢 GA |
| [`@wbc-ui/dataviewer2`](https://www.npmjs.com/package/@wbc-ui/dataviewer2) | JSON / data-table explorer | 🟢 GA |
| **[`@wbc-ui/latex2`](https://www.npmjs.com/package/@wbc-ui/latex2)** | **LaTeX math rendering** *(this package)* | 🟢 GA |
| [`@wbc-ui/mermaid2`](https://www.npmjs.com/package/@wbc-ui/mermaid2) | Diagram-as-code rendering | 🟢 GA |
| [`@wbc-ui/alert2`](https://www.npmjs.com/package/@wbc-ui/alert2) | Notification / toast system | 🟢 GA |
| [`@wbc-ui/press2`](https://www.npmjs.com/package/@wbc-ui/press2) | Markdown-driven docs engine | 🟢 GA |

---

## Build artifacts

| Format | File |
|---|---|
| ESM | `dist/latex2.es.js` |
| UMD | `dist/latex2.umd.js` |

---

## 📄 License

MIT © [Wissem Boughamoura](https://github.com/wissemb11) · [wi-bg.com](https://www.wi-bg.com) · [wbc-ui.com](https://wbc-ui.com)
