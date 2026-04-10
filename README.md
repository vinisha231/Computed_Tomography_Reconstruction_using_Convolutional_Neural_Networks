# CT Reconstruction using Convolutional Neural Networks

Research project at the **University of Washington Bothell** focused on improving CT image quality from sparse and limited-angle projections using deep learning — reducing the radiation dose patients need while maintaining diagnostic accuracy.

---

## Overview

Standard CT scans require many X-ray projections (angles) to reconstruct a high-quality image. Reducing the number of projections (sparse-view CT) lowers radiation exposure but degrades image quality. This project combines classical iterative reconstruction (SART) with modern deep learning to recover that quality.

**Key results:**
- PSNR: **36.5 – 39.9 dB** (with 144 and 360 sparse projections matching full-scan quality)
- SSIM: **0.95 – 0.97** (near-perfect structural similarity to ground truth)

---

## Methods

| Component | Description |
|-----------|-------------|
| **SART** | Simultaneous Algebraic Reconstruction Technique — iterative CT reconstruction baseline |
| **U-Net** | Encoder-decoder CNN for image artifact removal and enhancement |
| **DnCNN** | Denoising CNN applied as a plug-and-play prior within SART iterations |
| **Transformer** | Vision transformer architecture for global feature reconstruction |
| **Combined Loss** | Custom loss combining pixel-wise and perceptual metrics |

The core idea: use CNN models either as **post-processing denoisers** or **plug-and-play priors** inside the SART loop to iteratively refine reconstructions from sparse data.

---

## Repository Structure

```
├── main.py                    # Primary training/evaluation entry point
├── main2025.py                # Updated 2025 pipeline
├── Unet.py                    # U-Net architecture
├── dncnn.py / dncnn2.py       # DnCNN variants
├── dncnnsart.py               # DnCNN integrated with SART
├── Transformer.py             # Transformer-based reconstruction model
├── SART_pnp_nn.py             # SART + plug-and-play neural network prior
├── Combined_Loss.py           # Custom combined loss function
├── PSNR_SSIM_of_model_output.py  # Evaluation metrics
├── model_check.py             # Model checkpointing utilities
├── converter.py               # Data format conversion (e.g., .flt to .png)
├── flt_to_png.py              # Float array to PNG conversion
├── residual_comparison.py     # Residual image analysis
└── SV_Combined_PSNR_StatsSignificance/  # Statistical significance results
```

---

## Tech Stack

- **Python** — core language
- **TensorFlow / Keras** — deep learning models
- **NumPy** — array operations and projection math
- **Matplotlib** — visualization and comparison plots
- **OpenCV** — image processing utilities

---

## Evaluation Metrics

- **PSNR (Peak Signal-to-Noise Ratio):** measures pixel-level reconstruction fidelity
- **SSIM (Structural Similarity Index):** measures perceptual/structural similarity to ground truth

Both metrics are computed against full-projection CT ground truth scans.

---

## Research Context

This work is part of an ongoing undergraduate research project at UWB exploring how neural networks can enable **low-dose CT imaging** — a clinically significant problem where reducing radiation exposure is critical for patient safety, especially in repeated scans (e.g., cancer monitoring).

---

## Author

**Vinisha Bala Dhayanidhi** · [LinkedIn](https://linkedin.com/in/vinishab) · [viba2022@gmail.com](mailto:viba2022@gmail.com)  
University of Washington Bothell — Student Researcher, Jun 2024 – Present
