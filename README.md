
# 📄 PDF Invoice Table Extractor


Extract invoice tables from PDFs and export them to Excel automatically using OCR powered by a Vision-Language Model (VLM).

---

## **✨ Features**

* Convert multi-page PDFs into high-resolution images.
* Automatically clean up old images before processing.
* Extract structured table data from images using VLM-based OCR.
* Convert OCR output to valid JSON and pandas DataFrame.
* Export clean Excel files for analysis.
* Handles multi-page and irregular tables with merged cells.

---

## **🚀 How It Works**

**Architecture & Pipeline:**

```text
PDF file (input) 
     │
     ▼
Convert each page → high-res image (stored in `images/`) 
     │
     ▼
Clean old images (delete folder contents before conversion)
     │
     ▼
Convert images → Base64 → send to VLM for OCR
     │
     ▼
VLM returns JSON table data → preprocess & clean JSON
     │
     ▼
Convert JSON → pandas DataFrame
     │
     ▼
Export DataFrame → Excel (`output/result.xlsx`)
```

---

## **📂 Project Structure**

```
project_root/
│
├─ images/                 # PDF pages as images
├─ output/                 # Excel output
├─ data.pdf                # Sample PDF
├─ app.ipynb                 # Main script
├─ requirements.txt        # Python dependencies
└─ README.md               # Documentation
```

---

## **⚡ Usage**

1. Clone the repository:

```bash
git clone <repo_url>
cd project_root
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Set your Hugging Face API token in `hf_token`.

4. Place your PDF file in the project folder or update `pdf_path` in `main.py`.

5. Run the script:

```bash
python main.py
```

6. Your extracted invoice table will be saved as:

```
output/result.xlsx
```

---

## **📦 Dependencies**

* `PyMuPDF` – PDF → Image conversion
* `Pillow (PIL)` – Image processing
* `huggingface_hub` – VLM OCR
* `pandas` – DataFrame & Excel export
* `openpyxl` – Excel writer
* Standard Python libraries: `os`, `shutil`, `base64`, `json`, `mimetypes`

---

## **💡 Notes**

* Handles multi-page invoices and tables that continue across pages.
* Preserves text exactly as seen in the PDF.
* Output Excel files are clean, structured, and ready for analysis.

---
