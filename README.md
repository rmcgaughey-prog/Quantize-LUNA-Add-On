# Quantize for LUNA

**R-McG · Version 0.4.2 · Editing / MIDI / Workflow**

Transfer the feel of one performance to another. Capture grooves from audio or MIDI, save reusable templates, and tighten selected audio clips and MIDI notes with adjustable timing, swing and LUNA’s native audio algorithms.

## What it adds

LUNA already provides grid quantize, swing, strength and range controls. Quantize adds a reusable groove library, groove capture from audio or MIDI, supported groove-file imports, independent groove timing and MIDI velocity amounts, and a reviewed workflow for applying the same groove across selected audio clips and MIDI notes.

The library includes 12 original grooves. Imported and captured grooves are saved locally in **My Grooves**. Audio can use Polyphonic, Monophonic, LUNA Razor Blade, LUNA Polyphonic or Varispeed. Varispeed deliberately changes pitch with timing; the other choices preserve the pitch of the prepared audio.

## Install

Requires LUNA 3.1.2 or later. Tested on macOS.

Install through LUNA’s Add On installer using this public repository, or install the folder manually:

1. Choose **Code → Download ZIP** on GitHub and extract it.
2. Copy the extracted folder containing `manifest.json` into `/Library/Application Support/Universal Audio/LUNA/Add Ons/` on macOS. Administrator approval may be required.
3. Open a session in LUNA and choose **Add Ons → Windows → Quantize**.

No Node.js installation, account, API key or additional plug-in is required.

## Use a groove

1. Choose a library groove, or select **Straight** or **Swing** and a grid.
2. Select a timeline range across the audio and instrument tracks to tighten. Click **Apply to Selection…**.
3. Review each audio clip’s detected hits. Adjust **Sensitivity**, edit hit times, or use **Add Hit**. Unchecking a hit locks its position where native marker spacing permits.
4. Adjust **Timing**, **Safe Range**, **Max Move** and **Anchor**, and choose the audio algorithm. The panel shows proposed changes and the largest audio move in milliseconds.
5. Stop playback and recording, then click **Apply to Selection**. The complete operation is one LUNA Undo step. The main window’s **Apply Groove / Apply Quantize** button applies its MIDI preview only.

**Timing** controls how far events move toward the groove. **Velocity** transfers MIDI accents independently when the groove contains them. **Safe Range** protects events already close to their target; **Max Move** limits displacement. Both use a percentage of a grid step. **Session bars** keeps a shared musical phase; **Clip start** restarts the pattern for each clip.

## Capture and import

For MIDI, select reference notes and choose **Capture Groove**. For audio, select a continuous mono or stereo phrase on one track and choose **Capture Audio Groove**. Review the hits, choose the base grid, name the groove, and save it. The selection start defines the audio groove’s phase. Capture reads the current clip playback, including tempo conform, existing warps and pitch processing.

**Find Installed Grooves** scans folders you choose or approve. Supported DigiGroove `.grv` and groove JSON files are imported directly. MIDI files prompt for a track and base grid. Formats needing conversion, including Ableton `.agr` and FL Studio `.fsc`, must first be exported as MIDI in their source application. Once imported, grooves remain in **My Grooves** without rescanning. No third-party DAW groove library is included.

## Audio handling and limits

Affected audio tracks receive duplicate playlists, leaving their original versions editable. Existing processing is preserved in a working audio print before the new editable warp map is applied. Use LUNA’s track versions to compare results. Previously warped clips can be processed again. Clip gain and plain fades are preserved; track inserts and mixer processing remain separate.

Audio analysis supports mono/stereo PCM WAV or AIFF playback, phrases up to two minutes within one time signature, and a 256 MiB source/batch budget. LUNA’s 30 ms anchor-spacing constraint means close hits can share anchors. Complex comps, crossfades and licensed ARA/clip-effect combinations have limited coverage and may be rejected. Review detections on musical material.

Stereo channels use one timing map. Separate clips use independently detected hits; this is not a shared phase-coherent workflow for multi-microphone drums.

## Privacy

Quantize runs locally. It has no analytics, cloud processing, external network services or embedded credentials. It reads selected clip audio and approved groove folders, edits the selected session when Apply is used, and stores grooves, favorites and approved folder paths in the Add On’s local storage. Local library data is not included in this repository or sent to a server. Back up important grooves separately before reinstalling or replacing an Add On.

## License

Quantize is provided by R-McG under `LICENSE.txt`. The included LUNA Builder SDK retains its own terms in `THIRD-PARTY-NOTICES.txt`. Imported third-party groove files remain subject to their owners’ terms.
