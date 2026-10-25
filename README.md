# 🚗 Autonomous Driving Perception System

A computer-vision prototype that analyzes **recorded dashcam footage** to detect and track road users, estimate their relative distance from a monocular camera, and display a driver-assistance-style risk dashboard.

**Notebook:** `driving_perception_system.ipynb` (the uploaded `driving_perception_system (1).ipynb` is an identical copy).

## Features
- Detects **cars, motorcycles, buses, trucks, and pedestrians** with YOLO26 (`yolo26x.pt`).
- Tracks detected objects across frames using **ByteTrack**.
- Uses **Depth Anything V2 Small** to infer monocular scene depth and estimate object proximity.
- Estimates closing motion from short distance histories.
- Displays bounding boxes, object counts, nearest-object distance, and **SAFE / CAUTION / WARNING** alerts in an on-video HUD.
- Exports the annotated footage as an MP4.

## Technologies
Python, Ultralytics YOLO26, ByteTrack, Hugging Face Transformers, Depth Anything V2, PyTorch, OpenCV, NumPy, Pillow.

## Getting Started
1. Open `driving_perception_system.ipynb` in **Google Colab** (a GPU runtime is recommended).
2. Run the notebook's installation and model-loading cells. Models download automatically on first use.
3. Upload a dashcam video when prompted.
4. Optionally adjust `NEAR_DISTANCE_M`, `FAR_DISTANCE_M`, risk thresholds, and `SKIP_DEPTH_FRAMES`.
5. Run the remaining cells to produce `driving_perception_output.mp4`. The final Google Drive export cell is optional.

**Install dependencies outside Colab:**
```bash
pip install ultralytics transformers accelerate torch opencv-python numpy pillow
```

## Output
`driving_perception_output.mp4` — annotated video with detection boxes and the collision-risk HUD.

## Limitations
**Experimental visualization only, not an automotive safety system.** Depth Anything estimates *relative* monocular depth; the displayed meter values depend on manually chosen near/far anchors and are **not verified physical distances**. Closing-speed and collision alerts inherit these uncertainties. Results depend on lighting, video quality, tracking, and hardware performance.

**Maintainer:** [@sanaullahsnm899](https://github.com/sanaullahsnm899)
