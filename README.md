# Gravity Atlas | Planetary Gravity Explorer

Same universe. Different gravity. Explore surface gravity, escape velocity, weight, drops and jumps across all eight planets.

Everything lives in one file, `index.html`. No build step, no dependencies, no folders.

## Put it on GitHub Pages

1. Open your `Planetary-Gravity-Explorer` repository on GitHub.
2. Choose **Add file > Upload files** and drag in `index.html`. It replaces your current `index.html` because the name is the same.
3. Commit. After about a minute, hard-refresh your page (Ctrl+Shift+R).

Your old files (a separate stylesheet or script) are no longer used. You can leave them or delete them.

## What's on the page

1. **Home**: all eight planets orbiting in a space-time well (hover or click a planet).
2. **Choose a world**: eight dot-matrix planets. Pick one and everything below updates.
3. **Planet physics**: surface gravity, escape velocity, weight of a 70 kg mass and radius.
4. **Gravity lab**: drop a ball or run a jump with a strobe-light trail, a slow-motion switch, and a ghost "Earth" falling beside it for comparison.
5. **Gravity comparison**: four metrics across all eight planets (click a bar to select a planet).
6. **How the physics works**: the formulas and their assumptions.

## The data

Planet constants are in the `PL` array near the top of the `<script>`:

```js
{ id: 'mars', name: 'Mars', type: 'rocky world', mu: 4.282837e13, R: 3396.2 }
```

`mu` is GM in m^3/s^2 and `R` is the reference radius in km. Everything else is computed:

- `g = GM / R^2`
- `v_escape = sqrt(2 GM / R)`
- `W = m g`, `t = sqrt(2h / g)`, `v = sqrt(2 g h)`, `h_max = v0^2 / (2 g)`, `t_air = 2 v0 / g`

Notes on the constants:

- Earth's GM is rounded so that Earth reads exactly 9.81 m/s^2 (escape velocity then shows 11.18 km/s).
- For the giant planets, the radius is the 1-bar "cloud-top" level, which is what the usual reference gravities (24.79, 10.44, 8.87, 11.15 m/s^2) are quoted at.
- Values are approximate and for education, not mission planning.

Other things to tweak: slider ranges and defaults (the `CTL` and `S` variables), comparison metrics (`METRICS`), and the Source link in the header.

## Features

- Responsive, keyboard accessible (the planet picker is a real set of buttons), respects reduced motion
- Idealized physics: no air resistance, constant gravity
