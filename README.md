# 🎙️ OmniVoice Web UI — Run on Google Colab

Run **[OmniVoice](https://github.com/k2-fsa/OmniVoice)** (600+ language zero-shot voice cloning TTS) on Google Colab
with a full Gradio web interface — Voice Clone, Voice Design, and SRT subtitle generation.

**এই রিপো কোনো ফর্ক না** — সম্পূর্ণ স্বনির্ভর (self-contained)। `omnivoice` মডেল প্যাকেজ সরাসরি PyPI থেকে
ইনস্টল হয়; UI ও subtitle কোড এই রিপোর নিজস্ব ফাইল থেকে আসে, তাই কোনো তৃতীয় পক্ষের রিপো ডিলিট/প্রাইভেট হয়ে গেলেও
এটা ভেঙে পড়বে না।

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pabitra-senpai/omnivoice-colab/blob/main/OmniVoice_Colab.ipynb)

---

## ✨ Features

- **Voice Clone** — clone any voice from a 3–10 second reference audio
- **Voice Design** — build a voice from attributes (gender, age, pitch, accent, dialect) with no reference audio
- **600+ languages**, non-verbal tags (`[laughter]`, `[sigh]`, ...), one-click emotion tag buttons
- **Optional SRT subtitle generation** — sentence-level, word-level, and "Shorts" style, generated via faster-whisper
- **Auto-transcribe** reference audio into Reference Text
- **HuggingFace mirror fallback** — if the main HF endpoint is slow/blocked, falls back to a parallel downloader

## 🚀 Run it

1. Click the **Open in Colab** badge above (or upload `OmniVoice_Colab.ipynb` to Colab manually)
2. **Runtime → Change runtime type → T4 GPU**
3. Run **cell 1** ("Install OmniVoice Web UI") — takes ~2–4 minutes
4. Run **cell 2** ("Run Gradio APP") — wait for the model to load, then click the `https://xxxx.gradio.live` link that appears

## 📁 Repo structure

```
.
├── OmniVoice_Colab.ipynb   ← Colab notebook (Install cell + Run cell)
├── app.py                  ← Gradio web UI (Voice Clone / Voice Design tabs)
├── subtitle.py             ← self-contained SRT subtitle generation (faster-whisper)
├── hf_mirror.py            ← fallback model downloader if huggingface.co is unreachable
├── colab.txt               ← dependencies for Colab (torch already provided by Colab)
├── requirements.txt        ← full dependencies for running locally (non-Colab)
└── README.md
```

## 🖥️ Running locally (optional, needs an NVIDIA GPU)

```bash
git clone https://github.com/pabitra-senpai/omnivoice-colab.git
cd omnivoice-colab
pip install -r requirements.txt
python app.py
```

## 🔧 If you rename this repo

The notebook's Install cell hardcodes this repo's clone URL:
```
https://github.com/pabitra-senpai/omnivoice-colab.git
```
If you fork or rename it, open `OmniVoice_Colab.ipynb`, edit that line (and the matching `%cd` line) to match your
new repo URL/name, and update the Colab badge link above the same way.

## ⚖️ Usage Disclaimer

Use of this voice cloning model is subject to strict ethical and legal standards. By using this tool you agree
**not to** use it for fraud/deception, non-consensual voice impersonation, illegal activity, or generating
harmful/misleading content. The developers disclaim all liability for misuse — users bear full responsibility
for lawful, ethical use.

## 🙏 Credits

- Model & core TTS code: **[k2-fsa/OmniVoice](https://github.com/k2-fsa/OmniVoice)** — Xiaomi AI Lab, Next-gen Kaldi team
  ([paper](https://arxiv.org/abs/2604.00688), Apache-2.0 license)
- Web UI / subtitle wrapper in this repo: maintained independently, inspired by the community OmniVoice Colab demo
