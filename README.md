# Psihoterapeut
Professional website for a psychotherapy and counseling practice.
# Premium Psychotherapy Web Client – Front-End Architecture

> A high-performance, zero-dependency UI built for a psychotherapy practice. The project focuses on fluid state transitions, hardware-accelerated animations, and a grid-breaking editorial design system.

This repository contains the source code for a premium presentation website. The architecture is designed with a zero-tolerance policy for layout shifts and is optimized for stable 60fps rendering, relying exclusively on native Web APIs without the use of external libraries (No jQuery, No GSAP).

## 🏗 Technical Architecture & Implementation

### 1. State & Render Optimization
* **Intersection Observer API:** Instead of resource-intensive `scroll` event listeners, an asynchronous observer pattern is implemented. It detects DOM elements entering the viewport and triggers document-level `background-color` state mutations, ensuring O(1) complexity during scroll.
* **Hardware Acceleration:** All transitions and animations (custom cursor, reveal effects) rely exclusively on `transform` and `opacity` properties. Through the strategic use of the `will-change` directive, paint operations are offloaded directly to the GPU, eliminating unnecessary browser reflow/repaint cycles.

### 2. Custom Pointer Engine (LERP)
* The custom interactive cursor is synchronized with the screen refresh rate using `requestAnimationFrame`.
* Linear interpolation (LERP) is implemented for fluid mouse tracking that does not block the main thread.
* **Graceful Degradation:** Through CSS Level 4 media queries (`@media (hover: none) and (pointer: coarse)`), the custom pointer logic is automatically suspended on touch devices to preserve native UX standards and performance.

### 3. Responsive Design System
* **Fluid Typography:** Font and margin scaling is controlled by CSS `clamp()` functions, eliminating the need for excessive breakpoints.
* **Grid-Breaking Layout:** The asymmetrical design is achieved through advanced CSS Grid and CSS Custom Properties. On resolutions below 1024px, the DOM structure safely adapts into a vertical flow, and navigation transitions into an optimized fullscreen overlay with scroll blocking (`overflow: hidden` on the body element).

## 💻 Tech Stack
* **DOM / UI:** HTML5 (Semantic, a11y ready)
* **Styling:** CSS3 (Custom Properties, Grid, Flexbox, CSSOM manipulation)
* **Logic:** Vanilla JavaScript (ES6+)

## 🚀 Local Development Setup

The project requires a local server due to modern browser security policies (CORS restrictions for ES6 modules and Storage APIs).

```bash
# 1. Clone the repository
git clone [https://github.com/vas-username/ime-repozitorijuma.git](https://github.com/vas-username/ime-repozitorijuma.git)

# 2. Navigate into the directory
cd ime-repozitorijuma

# 3. Serve via a local server
# (e.g., using Live Server in VS Code, or via Node.js:)
npx serve .
