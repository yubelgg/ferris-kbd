# Ferris Sweep Custom Build

A fully custom ergonomic split keyboard build featuring custom PCB design, 3D-printed case, and ZMK firmware with advanced hold-tap macros and layer configurations.

![Ferris Sweep Setup](images/ferris%20sweep%20setup.jpg)
![Ferris Sweep](images/Ferris%20sweep.jpg)

## Project Overview

This project is a complete custom implementation of the Ferris Sweep, a 34-key wireless split keyboard. Every aspect was designed and built from scratch to create an ultra-portable, ergonomic typing experience.

## Hardware

### PCB Design

- **Designed custom PCB in KiCad** with adapted circuit traces for optimal component placement
- Based on the Ferris Sweep design philosophy with personalized modifications
- Uses **nice!nano v2** controllers for wireless Bluetooth connectivity
- Split keyboard architecture with 34 keys (17 per half)

### Case Design

- **Engineered low-profile case in AutoCAD** optimized for ergonomics and portability
- 3D-printed prototypes with iterative refinements
- Flush PCB fit achieved through precision standoff placement
- Minimal height profile for reduced wrist strain

## Firmware Configuration

This build runs [ZMK firmware](https://zmk.dev/) with extensive customization for optimal typing efficiency.

### Layout

The keyboard uses a custom **Engram layout**:

```
Z  Y  O  U  ;     '  L  D  W  Q
C  I  E  A  B     V  H  T  S  N
G  X  J  K  ,     .  R  M  F  P
      ⌘  ⌫         ␣  ⌥
```

### Advanced Features

#### Home Row Mods

- **Left hand**: GUI (C) • Alt (I) • Shift (E) • Ctrl (A)
- **Right hand**: Ctrl (H) • Shift (T) • Alt (S) • GUI (N)
- Tap-preferred behavior with 200ms tapping term
- 125ms prior-idle requirement to prevent accidental activations

#### Custom Layer-Mod Macro

Created a unique `lm` (layer-mod) macro that simultaneously:

- Activates a momentary layer
- Applies a modifier key
- Releases both together for seamless layer+modifier combinations

#### Combos

Strategic two-key combinations for frequently used keys:

- `D + W` → ESC
- `Y + O` → TAB
- `' + L` → ENTER
- `O + U` → (
- `L + D` → )
- `E + A` → [
- `H + T` → ]
- `J + K` → {
- `R + M` → }

### Layer System

**Layer 0 - Default**: SOUL layout with home row mods  
**Layer 1 - i3/WM**: Window management and numpad  
**Layer 2 - Numbers/Symbols**: Number pad, mathematical operators, and special characters  
**Layer 3 - Media**: Volume, playback, and brightness controls  
**Layer 4 - System**: Bluetooth profiles, reset, and bootloader access

### Power Management

- Sleep mode enabled after 15 minutes of inactivity (`CONFIG_ZMK_IDLE_SLEEP_TIMEOUT=900000`)
- Optimized for battery life on nice!nano controllers

## Build Instructions

### Prerequisites

- ZMK development environment
- GitHub Actions (for automated firmware building)

### Firmware Build

This repository uses GitHub Actions for automated firmware compilation:

```yaml
Board: nice_nano_v2
Shields: cradio_left, cradio_right
```

The workflow automatically builds both halves and generates UF2 files for flashing.

### Flashing

1. Put the nice!nano into bootloader mode (double-tap reset)
2. Drag and drop the appropriate `.uf2` file (`cradio_left` or `cradio_right`)
3. Wait for the board to reboot
4. Repeat for the other half

### Customizing the Keymap

Edit `config/cradio.keymap` to customize:

- Key positions and bindings
- Layer behaviors
- Combo definitions
- Hold-tap timing parameters

## Design Philosophy

This build prioritizes:

- **Ergonomics**: Split design with columnar stagger reduces finger travel and wrist strain
- **Portability**: Low-profile design and wireless operation
- **Efficiency**: Custom layout and layers optimize for programming and daily use
- **Customizability**: Open-source firmware allows infinite configuration possibilities

## Resources

- [ZMK Firmware Documentation](https://zmk.dev/)
- [Ferris Sweep on GitHub](https://github.com/davidphilipbarr/Sweep)
- [KiCad PCB Design Software](https://www.kicad.org/)
- [nice!nano Documentation](https://nicekeyboards.com/docs/nice-nano/)

## License

This configuration is released under the MIT License. See individual component licenses for PCB designs and firmware.

---
