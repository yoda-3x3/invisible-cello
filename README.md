# Invisible Cello

Play a cello in the air with your webcam. Hand tracking (MediaPipe) follows both hands, and a Web Audio synth makes the sound. Nothing is recorded or uploaded: the camera feed stays in your browser.

**Play it:** https://yoda-3x3.github.io/invisible-cello/

## How to play

- **Right hand bows.** Sweep it side to side; faster is louder. Raise or lower it to change string (A at the top, C at the bottom).
- **Left hand fingers.** Slide your index finger down the neck to raise the pitch, up to an octave.
- **Pinch** your left thumb and index finger to stop the note.
- **Lean** your bow hand toward the camera to dig in for a denser, brighter tone.
- Click **Calibrate** once so the neck, string heights and bow speeds fit your reach. It's saved in your browser.

Works best in Chrome or Edge with good lighting in front of you.

## Under the hood

- Hand tracking: MediaPipe Tasks Vision `HandLandmarker`, run once per camera frame, with a One Euro filter, hand identity tracking and short-gap prediction so fast bowing stays tracked.
- Sound: per-string detuned saw oscillators, a lowpass that follows bow speed and pressure, bow noise, a cello-body EQ and a generated reverb.
- Vibrato and bowing values are based on published measurements of cellists' vibrato (about 5.2 Hz, 25 cents wide in first position) and on string-teaching material about bow speed, pressure and contact point.

To run it locally, serve the folder over `http://localhost` (cameras need a secure origin), for example `python -m http.server`.
