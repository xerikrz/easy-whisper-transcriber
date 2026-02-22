# Easy Whisper Transcriber

This repository provides a streamlined automated workflow for extracting, managing, and transcribing audio content. Leveraging the power of **OpenAI's Whisper**, this tool handles everything from downloading content from popular platforms to generating production-ready subtitle formats.

## 🌟 Key Features

- **Multi-Source Audio Acquisition**:
  - **YouTube Extraction**: Integrated with `yt-dlp` to pull high-quality audio (192K MP3) directly from URLs.
  - **Google Drive Integration**: Seamlessly download individual files or entire folders using `gdown`.
- **High-Performance Transcription**: 
  - Utilizes the **OpenAI Whisper** engine for robust speaker-independent speech recognition.
  - Fully compatible with GPU acceleration (tested on NVIDIA T4).
- **Comprehensive Output Formats**:
  - Generates industry-standard `.srt` (SubRip) and `.vtt` (WebVTT) subtitle files.
  - Automatic organization of audio and subtitle assets.
- **Automated Packaging**: Bundles all generated subtitles into a portable `.zip` archive for easy distribution.

## 🛠️ Technical Stack & Prerequisites

The core logic is contained within a Jupyter Notebook environment, making it ideal for interactive data processing or deployment in platforms like Google Colab or Kaggle.

### Dependencies
Install the required packages using the following command:

```bash
pip install -qU openai-whisper setuptools-rust gdown yt-dlp
```

| Package | Purpose |
|---------|---------|
| `openai-whisper` | Core ASR (Automatic Speech Recognition) engine |
| `yt-dlp` | Advanced YouTube and media downloader |
| `gdown` | Google Drive public link downloader |
| `setuptools-rust` | Required for Whisper's underlying Rust dependencies |

## 🚀 Step-by-Step Usage Guide

### 1. Model Configuration
Whisper offers several model sizes. Choose the one that best fits your hardware and accuracy requirements:

- **tiny / base**: Extremely fast, suitable for simple clear audio.
- **small / medium**: Good balance between speed and accuracy.
- **large / turbo**: Recommended for most use cases, providing the highest accuracy with state-of-the-art performance.

### 2. Audio Ingestion
The notebook provides two primary methods for bringing audio into the workflow:
- **YouTube**: Simply paste common video URLs to trigger a background extraction process. Content is stored in the `/audio` directory.
- **Google Drive**: Use File or Folder IDs to fetch existing audio datasets.

### 3. Automated Transcription
Once audio files are present in the `/audio` folder, the transcription engine iterates through them. It performs:
- **Audio Pre-processing**: Ensuring compatibility with the Whisper model.
- **Inference**: Generating timestamps and text content.
- **Post-processing**: Formatting the raw output into readable subtitle files stored in `/subtitles`.

### 4. Results Export
To simplify file management, the system creates a `subtitles.zip` file containing all generated `.srt` and `.vtt` files across your session.

## 📂 Project Architecture

```text
.
├── whisper.ipynb       # Main interactive processing pipeline
├── audio/              # Temporary storage for downloaded MP3s
├── subtitles/          # Output directory for SRT and VTT files
├── subtitles.zip       # Final packaged output
└── README.md           # Project documentation
```

## ⚖️ License & Acknowledgments

- **Whisper**: Developed by [OpenAI](https://github.com/openai/whisper).
- **yt-dlp**: Community-maintained fork of youtube-dl.