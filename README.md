# KokoroLite-TTS: Lightweight Phoneme-Based TTS Model

A lightweight Text-to-Speech (TTS) pipeline trained using phoneme-text and audio data from Desivocal. This project uses the **Kokoro TTS** model to synthesize speech from phoneme sequences and evaluates the similarity between generated and original audio.

---

## 🎯 Objective

Train a small phoneme-based TTS model and evaluate its ability to replicate ground truth audio using similarity metrics such as Mel-Spectrogram KL Divergence and L1/L2 waveform loss.

---

## 📂 Dataset

- **metadata.csv** — Contains pipe-separated entries with graphene (text) and corresponding `.mp3` filenames.
- **audio/** — Directory containing `.mp3` voice samples aligned with the metadata.

---

## 🧠 Model Used

**Kokoro TTS**  
An open-weight TTS model with 82M parameters, optimized for fast and cost-efficient synthesis.  
GitHub: [hexgrad/kokoro](https://github.com/hexgrad/kokoro)

**Why Kokoro?**  
- Simple architecture with good synthesis quality  
- Lightweight and efficient for fast experimentation  
- Easy integration and customization

---

## ⚙️ Setup & Training

- Environment: Jupiter Notebook (local system)
- Frameworks: PyTorch, Torchaudio, Librosa
- Training pipeline includes:
  - Phoneme preprocessing
  - Feature extraction (mel-spectrograms)
  - Model fine-tuning and inference

---

## 🔍 Evaluation Metrics

We computed the following similarity metrics between the ground truth and generated audio:

- **KL Divergence** — Between original and predicted mel-spectrograms
- **L1/L2 Loss** — On raw waveform comparisons
- *(Optional)* Dynamic Time Warping (DTW) analysis

---

### 🔊 Example Results

Below are a few example test cases used to evaluate the model’s performance. Each includes the text input, basic similarity metrics, and DTW score comparing the synthesized audio to the ground truth.

| Example | Text | L1 Loss | L2 Loss | KL Divergence | DTW Score |
|---------|------|---------|---------|----------------|-----------|
| 414     | Yo guys! Loki is here | 0.0342 | 0.0030 | 3.2032 | 10,850.90 |
| 329     | oops akshit fucked the beat | 0.0233 | 0.0023 | 3.7752 | 16,943.57 |
| 152     | Close your eyes... (long input) | 0.0375 | 0.0032 | 2.9341 | 94,990.30 |
| 218     | I told you not to bother me... | 0.0378 | 0.0032 | 4.1769 | 74,677.86 |
| 317     | John deev, baby, Ok | 0.0241 | 0.0022 | 3.9511 | 21,306.44 |

> **Note:**  
> • Lower L1/L2 and KL scores indicate closer similarity to original audio.  
> • Higher DTW scores typically result from longer or more complex utterances.


---

## 💡 Observations & Improvements

- Kokoro TTS performed well on short and simple utterances, but showed limitations in prosody for longer sequences.
- KL divergence correlated well with subjective quality, validating our metric choices.
- Future improvements:
  - Incorporate pitch/energy embeddings
  - Fine-tune using voice cloning for better alignment
  - Try StyleTTS for better prosodic variation

---

## 📬 Contact

If you’re working on phoneme-based speech synthesis or interested in lightweight TTS research, feel free to connect!

