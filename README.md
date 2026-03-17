# share_database   receipt_dataset_v2
A dataset suitable for large model fine-tuning


# receipt_dataset_v2
A high-quality dataset for fine-tuning large language models (LLMs) on receipt understanding and related visual-language tasks

---

## 📦 Dataset Download & Extraction
### 1. Download Link
- **Baidu Netdisk**: [https://pan.baidu.com/s/1UergRaHm_yCQ3y9BhBSSVw](https://pan.baidu.com/s/1UergRaHm_yCQ3y9BhBSSVw)
- **Extraction Code**: `fuah`
- **File Name**: `receipt_dataset_v2.zip`

### 2. Unzip Instructions
#### Windows
Right-click the ZIP file → Select **Extract All** → Choose the target folder to complete unzipping.
#### Linux/Mac
Run the following command in the terminal:
```bash
unzip receipt_dataset_v2.zip -d receipt_dataset_v2
```

### 3. File Structure (After Unzip)
The unzipped dataset contains exactly two core components:
```
receipt_dataset_v2/
├── images/                # Folder containing all receipt image files (jpg/png)
└── train_data_aligned.json # 4.00 MB, structured annotation file (image-text pairs)
```

---

## 📋 Dataset Overview
This dataset is curated for **receipt understanding tasks** in LLM/multimodal model fine-tuning, including:
- Receipt text recognition & information extraction
- Key field parsing (merchant name, total amount, date, etc.)
- Visual-language reasoning for receipt documents

### Basic Information
| Item                | Details                                  |
|---------------------|------------------------------------------|
| Dataset Name        | receipt_dataset_v2                       |
| Data Type           | Multimodal (receipt images + structured text annotations) |
| Language            | Chinese (primary)                        |
| File Size           | ~4 MB (JSON) + receipt image files       |
| Format              | JSON (annotations) + image files (jpg/png) |
| Application         | LLM/multimodal model fine-tuning, receipt OCR post-processing |

---

## 🚀 Quick Usage
### 1. Install Dependencies
```bash
pip install transformers datasets torch pillow pandas
```

### 2. Load Dataset (Python Example)
```python
import os
import json
from PIL import Image
from datasets import Dataset

# Set your dataset root path
DATA_ROOT = "path/to/receipt_dataset_v2"

# Load the annotation JSON
with open(os.path.join(DATA_ROOT, "train_data_aligned.json"), "r", encoding="utf-8") as f:
    data = json.load(f)

# Convert to Hugging Face Dataset format
dataset = Dataset.from_list(data)

# Example: Load a receipt image and its annotation
sample = dataset[0]
image_path = os.path.join(DATA_ROOT, "images", sample["image_name"])
image = Image.open(image_path).convert("RGB")

print("Sample Annotation:", sample)
image.show()
```

### 3. Fine-Tuning Recommendations
- **Suitable Models**: Multimodal LLMs (Qwen-VL, LLaVA), Chinese LLMs (ChatGLM, Qwen) paired with OCR pipelines
- **Fine-Tuning Strategy**: LoRA/QLoRA (for efficient training on consumer GPUs)
- **Key Hyperparameters**:
  - Batch Size: 4–8 (adjust based on GPU memory)
  - Learning Rate: 1e-5 ~ 3e-5
  - Epochs: 3–5
  - Max Sequence Length: 512–1024

---

## 📚 Data Source & Citation
If you use this dataset in your research or projects, please cite this repository:
```
@misc{receipt_dataset_v2,
  author = {[Your Name/Team Name]},
  title = {receipt_dataset_v2: A Multimodal Dataset for Receipt Understanding and LLM Fine-Tuning},
  year = {2026},
  url = {https://github.com/[Your GitHub Username]/[Your Repository Name]},
}
```

---

## 📄 License
This dataset is released under the **MIT License**. You are free to use, modify, and distribute it for academic research and commercial purposes, provided that you retain the original attribution.

---

## ❗ Disclaimer
- The dataset is collected from public, legal sources. The authors are not responsible for any copyright issues arising from improper use.
- This dataset is for technical research and model development only; it may not be used for illegal or unethical purposes.

---

## 📧 Contact
For questions or issues related to the dataset, please submit an **Issue** in this GitHub repository or contact the author at 2024080111@stu.sdjzu.edu.cn.

*Last Updated: 2026-03-17*
