# AuraFace — Core ML (8-bit) for mSLICE

Core ML conversion of [`fal/AuraFace-v1`](https://huggingface.co/fal/AuraFace-v1) (`glintr100.onnx`, ArcFace ResNet-100, Apache 2.0), used by [mSLICE](https://github.com/starbudweiser/mSLICE) as an **optional, user-approved download** to group the appearances of the same face in a video. Nothing leaves the Mac.

- **File:** `AuraFace-CoreML-8bit.zip` (62.6 MB) → `AuraFace.mlpackage`, `LICENSE.txt`, `NOTICE.txt`.
- **Input:** RGB image 112 × 112 of a face **aligned on the ArcFace 5-point template**, raw 0..255 (the `(x − 127.5) / 127.5` normalisation is inside the model).
- **Output:** `emb`, 512 floats; L2-normalise, similarity = dot product.
- **Changes from the original (Apache 2.0, section 4b):** ONNX → Core ML (float16), pixel normalisation built in, weights palettised to 8 bits (k-means). No retraining.
- **Speed:** about 1.7 ms per face on the Apple Neural Engine (M5 Max). Accuracy was unchanged by the compression on our test set.
- **Licence:** Apache 2.0, same as the original. The original card states it was trained on data usable commercially; it does not name the datasets.

## Download

The file is attached to the release [`characters-auraface-1`](https://github.com/starbudweiser/mSLICE-models/releases/tag/characters-auraface-1) and checked by mSLICE against its SHA-256 before use:

```
2c1d331d88b4b7544a5835b810e6ca7203fcfc7d04b0be614787b4012331277b  AuraFace-CoreML-8bit.zip
```
