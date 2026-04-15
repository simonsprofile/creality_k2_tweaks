# Creality K2 Tweaks

Configuration and macro tweaks for a **Creality K2** (standard model, not Pro/Plus/SE), running on **240V mains in the UK**.

This repo keeps the setup close to factory behaviour while documenting small, practical quality-of-life changes.

## Current Scope

- `printer.cfg` - main printer configuration.
- `gcode_macro.cfg` - macro logic for print start/end, calibration flow, and maintenance.
- `Machine start G-code.txt` - slicer start G-code example.

## Printer Context (from current config)

- Model: Creality K2 (standard)
- Firmware config version: `v1.1.260206`
- Build volume (configured): approximately **260 x 260 x 260 mm**
- Mains environment: **UK 240V**
- Bed PID values include both 220V and 110V profiles; this setup is intended for 220/240V operation.

## Notable Tweaks in This Repo

- Chinese comments translated to English and tidied for readability.
- Start-print and calibrate-print mesh paths made explicit:
  - no calibrate-print -> load saved `default` mesh
  - calibrate-print -> generate fresh mesh
- Z stepper mode flow adjusted for consistency:
  - calibration/homing paths use `VAL=0`
  - print phase switches to `VAL=0.2`
  - end-print resets to `VAL=0`
- `virtual_sdcard.offset_value` set to `0.0` so first-layer Z adjustment can be managed from slicer profiles.

## Recommended Workflow

1. Back up known-good configs before edits.
2. Make small, isolated changes and test one variable at a time.
3. Restart firmware after config edits.
4. Validate first layer with a quick single-layer test print.
5. Commit often with clear messages describing intent.

## Notes

- These files are tuned for one specific machine and environment.
- If you run a different K2 variant, voltage region, or hardware mod stack, review all values before reuse.
