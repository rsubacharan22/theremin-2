# 🎹 Invisible 80s Rhythm Keyboard

An interactive, browser-based spatial instrument and rhythm game. This project uses AI hand-tracking to let users play a polyphonic synthesizer in mid-air using their webcam.

<div align="center">
  <video src="demo.mp4" controls="controls" style="max-width: 100%; border-radius: 8px; border: 2px solid #00f3ff; box-shadow: 0 0 20px rgba(0, 243, 255, 0.2);">
  </video>
</div>

## ✨ Overview
This project transforms a standard webcam into a digital instrument. By tracking 3D hand landmarks in real-time, the application maps spatial coordinates to musical frequencies, allowing users to trigger fully synthesized audio by "pinching" the air. It also features an integrated rhythm game tutorial modeled after the main hook of *Blinding Lights*.

## 🚀 Features
* **AI Hand Tracking:** Uses Google's MediaPipe Vision models to map real-time 3D hand landmarks for up to two hands simultaneously.
* **Spatial Interface:** Divides the webcam feed into 7 invisible, perfectly tuned vertical columns restricted to the C Minor Pentatonic scale (C4 to Eb5) to ensure harmonious playback.
* **Polyphonic Web Audio Synth:** Generates 80s-style sawtooth waves dynamically using the browser's native `AudioContext`. Features custom low-pass filtering and chorus detuning for a thick, retro sound.
* **Interactive Rhythm Game:** Includes a time-synced "falling block" state machine that teaches users how to play melodies via visual cues and precise hit-zone detection.
* **Zero Latency Gesture Control:** Uses custom trigonometric math to calculate the distance between the thumb and index finger, creating an instant "pinch" trigger without the lag of standard gesture-recognition models.

## 🛠️ Tech Stack
* **Frontend:** HTML5, CSS3, Vanilla JavaScript (ES6 Modules)
* **Computer Vision:** `@mediapipe/tasks-vision` (HandLandmarker model via WebAssembly)
* **Audio:** Native Web Audio API

## 💻 How to Run Locally
Because this project requires webcam and microphone access, modern browsers require it to be run on a secure origin (`localhost` or `HTTPS`). You cannot simply double-click the `index.html` file.

1. Clone this repository:
   ```bash
   git clone [https://github.com/your-username/invisible-keyboard.git](https://github.com/rsubacharan22/invisible-keyboard.git)
   cd invisible-keyboard
2. Open the project in your preferred code editor (e.g., VS Code).

3. Start a local development server. If using VS Code, the Live Server extension is recommended.

4. Alternatively, run via Python in your terminal: python -m http.server 8000

Open your browser to http://localhost:8000.

5. Allow webcam permissions when prompted by the browser.

How to Play:
1. Step back from your screen so both hands are clearly visible to the webcam.

2. Move Horizontally: Your hand's X-axis position determines the pitch (Left = High Pitch, Right = Low Pitch).

3. Pinch to Play: Bring your thumb and index finger close together to trigger a note. You can play polyphonically using both hands.

4. Tutorial Mode: Click the "Boot Tutorial" button to launch the rhythm game. Wait for the neon pink blocks to hit the green target line, and pinch inside the highlighted column!

 Troubleshooting:
1. Notes aren't playing when I pinch? The pinch sensitivity is mathematically tied to the distance between your fingers. If it feels unresponsive, find the const isPinching = distance < 0.08; line in index.html and increase the threshold (e.g., to 0.12 or 0.15).

2. Camera not turning on? Ensure no other applications (like Zoom or Discord) are currently using your webcam.