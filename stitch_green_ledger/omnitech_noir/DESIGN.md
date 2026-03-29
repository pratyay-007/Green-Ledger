# Design System Strategy: The Kinetic Grid

## 1. Overview & Creative North Star
**Creative North Star: "Interstellar Command Center"**

This design system moves away from the static nature of traditional fintech or utility apps, embracing a high-octane, futuristic aesthetic that feels like a piece of advanced alien technology. We are not building a website; we are building an interface. 

To break the "template" look, the system relies on **Kinetic Tension**. This is achieved through the juxtaposition of ultra-heavy `surface` blacks and "radioactive" `primary` greens. We avoid traditional symmetrical grids in favor of intentional "optical weight"—where large-scale `display-lg` typography is balanced by micro-detailed `label-sm` data points. The experience should feel pressurized, precise, and premium.

---

## 2. Colors & Surface Architecture
The palette is rooted in an absolute void, allowing the neon accents to "vibrate" against the charcoal background.

### The "No-Line" Rule
Explicitly prohibit 1px solid borders for sectioning. Structural separation is achieved through **background stepping**. 
- Use `surface_container_low` (#131313) for the main body.
- Use `surface_container_high` (#201f1f) for interactive cards.
- This creates "soft" boundaries that feel like part of a singular molded object rather than a collection of boxes.

### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers.
*   **Base Layer:** `surface` (#0e0e0e) - The infinite void.
*   **Section Layer:** `surface_container_low` (#131313) - Subtle grouping.
*   **Object Layer:** `surface_container_highest` (#262626) - Actionable cards.
*   **Active Layer:** `primary` (#8eff71) - High-energy state changes.

### The "Glass & Gradient" Rule
Standard flat colors are forbidden for hero elements. Use **Bioluminescent Gradients**:
- **Primary CTAs:** Transition from `primary` (#8eff71) to `primary_container` (#2ff801) at a 135-degree angle.
- **Glassmorphism:** For floating overlays (modals/tooltips), use `surface_container_highest` at 70% opacity with a `20px` backdrop-blur. This allows the neon data visualizations to bleed through the "frosted" interface.

---

## 3. Typography
We use a high-contrast pairing to balance technical precision with futuristic character.

*   **The Powerhouse (`Space Grotesk`):** Used for `display` and `headline` roles. Its quirky, geometric terminals provide the "alien tech" soul. Use `display-lg` (3.5rem) for balance totals or primary headers to command immediate attention.
*   **The Operator (`Manrope`):** Used for `title`, `body`, and `label`. Manrope provides the technical legibility required for financial data and dense information. 

**Typographic Intent:**
Always pair a `headline-sm` in `on_surface` (White) with a `label-md` in `primary` (#8eff71) for metadata. The color shift acts as the primary hierarchy driver, not just the font size.

---

## 4. Elevation & Depth
In a futuristic dark mode, traditional shadows are replaced by **Light Emission**.

*   **The Layering Principle:** Stack `surface_container_lowest` cards on top of `surface_container_low` sections. The difference in hex value is enough to signify depth without visual clutter.
*   **Glow States (Active):** Instead of a shadow, active elements receive an `outer-glow`. Use the `primary` color at 15% opacity with a 12px spread. This mimics the "Ben 10" aesthetic of a device powering up.
*   **The "Ghost Border" Fallback:** If a container requires a boundary (e.g., in complex data tables), use `outline_variant` (#494847) at **15% opacity**. It should be felt, not seen.

---

## 5. Components

### Buttons (The Core Actuators)
*   **Primary:** High-gloss. Background: `primary` gradient. Text: `on_primary` (Deep Green). Shape: `md` (0.375rem) for a sharp, tactical feel.
*   **Tertiary/Ghost:** No background. Text: `primary`. On hover/tap, add a `0.5` spacing bottom-border using `primary_fixed`.

### Cards & Lists
*   **Rule:** Forbid divider lines. Use `spacing-6` (1.3rem) of vertical whitespace to separate list items. 
*   **Data Cards:** Use `surface_container_high` (#201f1f). Positive data (gains) must use `primary` (#8eff71). Negative data (losses) must use `error` (#ff7351) with a subtle `error_container` background tint at 10% opacity.

### Sleek Data Visualizations
*   **Charts:** Line charts should use a 2px stroke of `primary` with a vertical gradient fill (Primary to Transparent).
*   **Interaction:** Tapping a data point should trigger a "pulse" animation using `primary_dim`.

### Input Fields
*   **State:** The "Idle" state is a `surface_container_highest` block.
*   **Focus:** The container shifts to `surface_bright` and a 1px "Ghost Border" of `primary` appears. The cursor/caret should always be `primary`.

---

## 6. Do's and Don'ts

### Do:
*   **Use Asymmetry:** Place `display-md` headers off-center to create a dynamic, editorial feel.
*   **Embrace the Void:** Use large amounts of `surface` (#0e0e0e) to let the neon elements breathe.
*   **Intentional Color:** Use `tertiary` (#88f6ff) only for secondary data streams (e.g., info tooltips or neutral benchmarks) to keep the green/red dichotomy clear.

### Don't:
*   **No Rounded "Pills":** Avoid `full` (9999px) rounding for buttons. It feels too soft. Stick to `md` (0.375rem) or `lg` (0.5rem) for a more aggressive, technical silhouette.
*   **No Pure Greys:** Never use standard mid-greys. All neutrals must be derived from the "Charcoal" (`surface_container`) or "Slate" (`outline`) tokens to maintain tonal depth.
*   **No Heavy Borders:** If you see a solid 1px line, delete it. Use a background color shift instead.

### Accessibility Note
While the aesthetic is "High Contrast," ensure that all `on_surface_variant` text (Grey) meets a 4.5:1 ratio against the `surface_container` tiers. If legibility is compromised, promote the text to `on_surface` (White).