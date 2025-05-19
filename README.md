## Introduction

This project explores unpaired image-to-image translation using a Cycle-Consistent Generative Adversarial Network (CycleGAN). The task is inspired by the Kaggle competition titled *“I'm Something of a Painter Myself”*, which challenges participants to transform real-world photographs into Monet-style paintings.

The primary objective is to train a deep generative model that can learn to apply the artistic style of Claude Monet—known for impressionistic brushwork, soft edges, and warm palettes—to natural photographs without relying on paired examples.

---

### Problem Statement

Given:
- A dataset of **unpaired images** consisting of Monet paintings and real-life photos

We aim to:
- Train a CycleGAN to **translate real photos → Monet-style images**
- Generate at least 7,000 Monet-style outputs
- Submit these outputs for evaluation using the **MiFID score** (Memorization-informed Fréchet Inception Distance), which measures similarity between generated images and real Monet paintings based on learned perceptual and diversity features.

---

### Dataset Description

The dataset provided by Kaggle includes:

- **300 Monet paintings** stored in `/monet_jpg/`
- **7,000+ real photographs** stored in `/photo_jpg/`

All images are in `.jpg` format and resized to **256×256 pixels**. The images are **unpaired**, meaning there is no one-to-one correspondence between a photo and a painting. This makes traditional supervised training infeasible and motivates the use of CycleGAN, which learns bidirectional mappings using cycle consistency and adversarial loss without the need for paired examples.

---

### Approach Summary

The model is trained using:
- A **ResNet-based generator** with 9 residual blocks
- A **PatchGAN discriminator**
- Combined **LSGAN loss**, **cycle consistency loss**, and **identity loss**

The final output is a ZIP archive of Monet-style images, which is evaluated via Kaggle's scoring system based on MiFID.
