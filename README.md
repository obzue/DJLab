[README.md](https://github.com/user-attachments/files/34104821/README.md)
# ObzueAI DJLab

A browser-based DJ mixing playground built with plain HTML, CSS, and JavaScript. It combines an eight-deck virtual controller with local audio playback, mixer controls, performance pads, MIDI mapping, turntable skins, and an optional two-deck video mix.

> This is a browser application—not a native audio workstation. Audio output and hardware support depend on your browser and operating system. ASIO drivers and AI-isolated stems are not provided.

## Features

- **Eight virtual decks** with waveform displays, transport, cue points, pitch/rate controls, and jog controls.
- **Local audio library:** load individual audio files or browse a folder from your device. Audio is decoded and played locally in the browser.
- **Mixer:** eight channel strips, channel faders, EQ, mute, master level and filter, and crossfader.
- **Performance pads:** two editable banks, cue assignment, per-pad level and labels, and custom audio samples.
- **Audio effects:** filter, echo, reverb, flanger, phaser, delay, beat roll/slicer, and frequency-band focus.
- **MIDI mapping:** connect a USB MIDI controller, learn mappings, edit bindings, and save them in the browser. Includes an MPD218 auto-map.
- **Jog and turntable presentation:** interactive jog wheels and a catalog of visual turntable skins.
- **Video mixing:** load video files or supported streaming links on decks A/B and blend them with the crossfader.
- **Persistent preferences:** pad settings, MIDI mappings, selected skins, and supported video links are stored in browser local storage.

## Run locally

No build step, package manager, or dependencies are required. Serve the repository root over HTTP and open it in a modern browser. For example, with Python installed:

~~~sh
python -m http.server 8000
~~~

Then visit <http://localhost:8000>.

Opening index.html directly with a file URL may prevent JavaScript modules or browser APIs from working correctly. Use localhost or HTTPS instead. MIDI support requires a compatible browser and connected MIDI device; output-device selection and WebHID availability vary by browser and platform.

## Use

1. Select **Add Files** or **Open Folder** and choose audio from your device.
2. Load tracks onto a deck, then use its transport and the mixer controls to play and blend.
3. Use the **Pads**, **Effects**, **MIDI**, **Skins**, and **Settings** tabs for their respective controls.
4. Switch the center display to video mode to load a video on deck A or B. Streaming providers may limit playback or mixing through embeds.

The app does not upload your selected local music. Local media files are handled in the browser. Browser settings, including mapped MIDI controls and pad preferences, are saved to local storage for that site.

## Project structure

- index.html — application markup and entry point
- styles.css, turntable.css — interface and turntable styling
- main.js — app state, UI interactions, decks, and controller rendering
- audio.js — Web Audio graph, deck playback, and audio routing
- midi.js — MIDI device discovery, learn mode, and stored mappings
- video.js — video deck loading, playback, and crossfade output
- ui.js, controllers.js — waveform/UI helpers and controller utilities
- skinCatalog.js, turntableCatalog.js, turntableEngine.js — visual catalogs and turntable behavior
- assets/ — controller and turntable artwork
- docs/ObzueAI-DJLab-User-Guide.pdf — user guide
- vendor/scratchable-turntable/ — third-party component and its license

## Browser compatibility and limitations

The application uses JavaScript modules, Web Audio, Canvas, File APIs, and optional Web MIDI/WebHID APIs. Use a current desktop browser for the most complete experience. Browser support, audio latency, output routing, codecs, MIDI permissions, and embedded video services differ across browsers and operating systems.

- Audio starts only after browser interaction where required by autoplay policies.
- ASIO is available only to native software; this web app uses browser audio APIs.
- “Stems Focus” applies frequency-band filtering; it does not perform source separation.
- Video embeds depend on the source provider, network access, and its embedding policies.

## Credits and licensing

The repository includes third-party code under vendor/; see its accompanying license file. Review the rights and licenses for all project artwork, audio, and other media before redistributing or using them commercially. No project-wide license is specified here.
