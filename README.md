# 3D Scene Reconstruction from Satellite Imagery 🌍🛰️

This project explores the feasibility of reconstructing 3D urban scenes using satellite images via classical Structure-from-Motion (SfM) and Multi-view Stereo (MVS) techniques. We collect satellite images from Google Earth Pro, perform SfM using COLMAP, and fuse depth information to produce sparse and dense point clouds.

## 📌 Overview

- **Domain:** 3D Scene Reconstruction
- **Techniques:** Structure-from-Motion (SfM), Multi-View Stereo (MVS), Monocular Depth Estimation
- **Tools:** Google Earth Pro, COLMAP, MiDaS, Open3D, Python
- **Dataset:** Satellite imagery of the UCI campus from 2005–2025 (temporal), 2025 (current), and 3D-enabled satellite view

## 📂 Project Structure

├── data_collection.ipynb # Satellite image extraction and dataset generation
├── reconstruction_pipeline.ipynb # Reconstruction experiments and visualizations
├── report.pdf # Final technical report with results and discussion
├── images/ # Qualitative reconstruction outputs
└── colmap_workspace/ # Sparse and dense reconstruction outputs

## 📸 Dataset Variants

- **Temporal:** Multi-year (2005–2025) satellite images (~300 frames)
- **Current:** High-resolution, single-date images from 2025 (~50 frames)
- **3D-enabled:** Terrain and 3D buildings enabled (~140 images)

## ⚙️ Pipeline

1. **Image Extraction & Preprocessing**: Google Earth Pro recordings → Frame extraction → Resizing
2. **Sparse Reconstruction**: Feature extraction (SIFT), exhaustive matching, SfM via COLMAP
3. **Dense Reconstruction**:
   - PatchMatch stereo + depth fusion (COLMAP MVS)
   - Alternative: MiDaS monocular depth backprojection
4. **Visualization**: Point cloud and mesh rendering via Open3D / MeshLab

## 📊 Results Summary

| Dataset            | Images | 3D Points | Mean Reproj. Error |
|--------------------|--------|-----------|--------------------|
| 3D-Enabled (2025)  | 132    | 112,177   | 0.7343             |
| Temporal (2005–25) | 279    | 309,103   | 1.0924             |
| Current (2025)     | 47     | 88,436    | 1.1614             |

## 🔍 Key Insights

- Multi-temporal images improve coverage but suffer from inconsistency.
- 3D-enabled images yield best structure with minimal error.
- Monocular depth maps can extend COLMAP outputs when hardware is limited.

## 🚧 Challenges

- Limited parallax in satellite views
- Shadows, trees, and occlusions
- No native support in COLMAP for learned depth fusion

## 🔮 Future Directions

- Integrating segmentation (e.g., Mask2Former) for dynamic object masking
- Testing learned stereo fusion (e.g., NeuralRecon, OpenMVS)
- Using hybrid pipelines combining SfM and monocular depth priors

## 📎 Resources

- [COLMAP](https://colmap.github.io/)
- [MiDaS Depth Estimation](https://github.com/isl-org/MiDaS)
- [Open3D](http://www.open3d.org/)
- [Google Earth Pro](https://www.google.com/earth/versions/)
