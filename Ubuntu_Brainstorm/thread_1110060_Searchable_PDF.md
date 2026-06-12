---
title: "Searchable PDF"
date: 2009-03-29
forum: Ubuntu Brainstorm
---

### Post by artiee on 2009-03-29
Many people have expressed their wish to have a scanning tool capable of creating a searchable PDF.

Searchable PDFs are familiar on the windows side and you can use e.g. *Google desktop* to easily find what you are looking for from the scanned PDFs. Searchable PDFs are a requirement for paperless offices. So, it's a basic need but there is no proper tool for linux, yet.

On the Windows side there is at least the *ABBYY Finereader* which does a great job in OCR(Image(s))-->PDF. So, it creates a PDF which has both the image and text layer, and both fit seamlessly together. 

I think that creating a tool which accomplishes this isn't too hard, just takes some thinking. There are plenty of software around which can do half the job already.

Requirements list:
------------------

1. Good and clear GUI
2. Tool is linked/easily linkable to scanner software
3. Modular design:
 -Tool takes list of images or PDFs as parameters
 -->For those it does OCR
 -->The result is used to create a searchable PDF (we have both the text + image)

I think the problem is in the last phase. I have no idea how searchable PDFs are structured or much time to figure it out. First approach which come in to my mind is to record the position and size of each letter in the OCR-phase, something like this:

struct character {
 char c;
 int x_position;
 int y_position;
 int font_xsize;
 int font_ysize;
};

This is then glued back to PDF (how?).

-More requirements for the list?

-Ideas which software could be used to tweak for this tool?

-What do you think in general about this idea?

---

### Post by Jeffery Mewtamer on 2009-04-19
Sounds like a useful feature if the technical issues can be resolved. However, I think it would be more useful if such a system could also produce html and OpenDocument files.

---

### Post by Rosewood_Arts on 2009-04-19
I have waited for years for a local (non-web-based) opensource document management program like ScanSoft's (now Nuance) PaperPort...which can scan to pdf, ocr to searchable text, and organize gigs of documents.

An unmet need for this functionality definitely exists in Linux...wish I could create it myself.

Closest I have seen are web-based and not capable of securing confidential documents.  Can't use PaperPort in Wine because Wine cannot access a (scsi) scanner...besides, I really want an opensource equivalent for Ubuntu.

---

