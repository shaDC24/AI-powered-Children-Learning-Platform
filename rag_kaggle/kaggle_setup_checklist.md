# ✅ Kaggle Setup Checklist — NCTB Bengali OCR

## Step 1: PDF Dataset Upload করো
- [ ] kaggle.com এ login করো
- [ ] **Datasets** → **New Dataset** click করো
- [ ] Dataset name: `nctb-class3` দাও
- [ ] `Class-3__Bangla_combine__compressed.pdf` upload করো
- [ ] **Create** click করো

---

## Step 2: Notebook তৈরি করো
- [ ] **Code** → **New Notebook** click করো
- [ ] Notebook name: `NCTB Class3 Bengali OCR` দাও
- [ ] উপরের মেনু থেকে **File** → **Import Notebook** → `nctb_bengali_ocr_easyocr.ipynb` upload করো

---

## Step 3: Dataset Add করো
- [ ] Notebook এর right panel এ **Add Data** click করো
- [ ] **Your Datasets** → `nctb-class3` select করো
- [ ] Add করলে path হবে:
  `/kaggle/input/nctb-class3/Class-3__Bangla_combine__compressed.pdf`
- [ ] Notebook এর `PDF_PATH` variable এ এই path আছে কিনা confirm করো ✅

---

## Step 4: GPU Enable করো (CRITICAL!)
- [ ] Right panel → **Session Options** (বা Settings)
- [ ] **Accelerator** → **GPU T4 x2** select করো
- [ ] EasyOCR GPU ছাড়া অনেক slow (CPU তে ~৩ ঘণ্টা, GPU তে ~১৫ মিনিট)

---

## Step 5: Internet Enable করো
- [ ] **Session Options** → **Internet** → **On** করো
- [ ] EasyOCR model download করার জন্য internet লাগবে (প্রথমবার)

---

## Step 6: Run করো
- [ ] **Run All** (Shift + Enter সব cell এ) অথবা উপরে **▶▶ Run All** button
- [ ] প্রথম cell (install) শেষ হতে ~৩ মিনিট লাগবে
- [ ] OCR step শেষ হতে ~১৫-২০ মিনিট লাগবে
- [ ] Session timeout এর আগেই শেষ হবে ✅

---

## Step 7: Output Save করো
Run শেষ হলে এই files পাবে:
```
/kaggle/working/
├── class3_bangla_full.txt     ← পুরো বইয়ের text
├── texts/
│   ├── page_004.txt
│   ├── page_005.txt
│   └── ... (per-page backup)
└── faiss_index/
    ├── bangla_class3.faiss    ← Vector index
    └── chunks.pkl             ← Text chunks
```

- [ ] **Save Version** করো (File → Save Version → Save & Run All)
- [ ] Output tab থেকে files download করো অথবা next notebook এ use করো

---

## ⚠️ Common Issues

| সমস্যা | সমাধান |
|--------|--------|
| PDF_PATH not found | Dataset ঠিকমতো add হয়েছে কিনা check করো |
| CUDA out of memory | batch_size 128 → 64 করো |
| EasyOCR install fail | Internet ON আছে কিনা check করো |
| Session timeout | Resume support আছে — আবার Run করলে completed pages skip করবে |

---

## পরবর্তী Notebook (এরপর বানাবো)
- Phi-3 Mini inference — RAG দিয়ে Bengali Q&A
- Whisper STT — Bengali voice → text  
- Edge-TTS — text → Bengali audio
