<p align="center"><img src="docs/images/banner.webp" alt="Flock Emerge banner" width="100%"></p>

<div align="center">

# Flock Emerge

![JavaScript](https://img.shields.io/badge/JavaScript-ES6-F7DF1E?logo=javascript&logoColor=000)
![p5.js](https://img.shields.io/badge/p5.js-1.7.0-ED225D?logo=p5dotjs&logoColor=white)
![Canvas](https://img.shields.io/badge/Rendering-HTML5_Canvas-E34F26?logo=html5&logoColor=white)
![Status](https://img.shields.io/badge/status-interactive_demo-2ea44f)

**A real-time agent-based simulation of emergent flocking behaviour with predator-prey steering dynamics.**

![Flock Emerge animated simulation preview](docs/images/flock-emerge-demo.gif)

[Live Demo](https://ronithrashmikara.github.io/Flock-Emerge/) · [Algorithm](#algorithm) · [Controls](#controls) · [Roadmap](#roadmap)

</div>

## Overview

**Flock Emerge** is an interactive browser simulation based on Craig Reynolds' Boids algorithm. Each boid follows a small set of local steering rules, yet the group produces coordinated movement that resembles natural flocking, schooling, and swarm behaviour.

The project extends the classic boids model with a predator-prey layer: prey agents flock together while reacting to nearby predator agents, and predators pursue the closest prey within range. The result is a compact visual demonstration of how simple rules can produce complex emergent behaviour.

## Preview

![Flock Emerge browser interface screenshot](docs/images/flock-emerge-preview.png)

## Why This Project Matters

Flocking is a classic example of **emergence**: complex system-level behaviour created by simple local rules. This project translates that idea into an interactive simulation where parameters can be tuned live, making it useful as a compact demonstration of agent-based modelling, AI-adjacent simulation logic, and visual systems thinking.

## Key Features

- **Classic boids steering**
  - Separation: avoid crowding nearby agents.
  - Alignment: match the average heading of neighbours.
  - Cohesion: move toward the local centre of nearby agents.
- **Predator-prey dynamics**
  - Predator agents seek nearby prey.
  - Prey agents flee from predator influence zones.
  - Fear-based prey colouring makes threat response visible.
- **Real-time parameter tuning**
  - Adjust separation, alignment, cohesion, predator influence, and speed while the simulation runs.
- **Interactive canvas controls**
  - Click to add prey agents.
  - Hold `P` and click to add predators.
  - Export the current canvas state as a PNG.
- **Visual telemetry**
  - Live prey/predator counts.
  - Runtime FPS display.

## Demo

Open `index.html` directly in a browser, or serve it with any static file server.

```bash
# Option 1: open directly
start index.html

# Option 2: serve locally with Python
python -m http.server 8000
```

Then visit:

```text
http://localhost:8000
```

## Controls

| Control | Effect |
|---|---|
| Separation | Increases spacing between nearby boids. |
| Alignment | Makes boids match neighbour direction more strongly. |
| Cohesion | Pulls boids toward nearby flock centres. |
| Predator Influence | Controls how strongly prey flee from predators. |
| Speed | Changes movement speed for both prey and predators. |
| Mouse click | Adds a prey boid at the cursor position. |
| `P` + mouse click | Adds a predator at the cursor position. |
| Export PNG | Saves the current simulation frame as an image. |

## Algorithm

Each frame applies steering forces to every agent:

```text
prey_acceleration =
    separation_force * separation_weight
  + alignment_force  * alignment_weight
  + cohesion_force   * cohesion_weight
  + flee_force       * predator_weight

predator_acceleration =
    pursuit_force
  + local_predator_flocking_force
```

The simulation uses vector-based movement:

1. Calculate steering forces from local neighbours.
2. Add forces into acceleration.
3. Update velocity and clamp it to a maximum speed.
4. Update position.
5. Wrap agents around canvas edges.
6. Render each agent according to type and state.

## Technical Stack

- **JavaScript ES6** for simulation logic.
- **p5.js** for canvas rendering and vector math.
- **HTML/CSS** for interface and controls.
- **No build step** required.

## Project Structure

```text
Flock-Emerge/
├── docs/
│   └── images/
│       ├── flock-emerge-demo.gif
│       └── flock-emerge-preview.png
├── index.html   # Simulation, UI, and p5.js logic
├── LICENSE
└── README.md
```

## Engineering Notes

This project demonstrates:

- Agent-based modelling.
- Emergent behaviour from local rules.
- Steering behaviours and vector math.
- Real-time interactive simulation.
- Lightweight front-end prototyping without a build pipeline.
- Communicating technical work clearly through visual documentation.

## Roadmap

- [ ] Split simulation logic into separate JavaScript modules.
- [ ] Add simulation presets such as calm flock, panic, predator swarm, and high-density crowding.
- [x] Add pause/resume and reset controls.
- [x] Add screenshots and animated GIF preview.
- [ ] Add mobile-friendly canvas scaling.
- [x] Deploy with GitHub Pages.

## Author

Built by **Ronith Rashmikara** as an interactive exploration of emergent systems, flocking behaviour, and browser-based simulation.
