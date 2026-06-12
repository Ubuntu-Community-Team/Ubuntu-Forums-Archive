---
title: "xsane and multiple pdf pages"
date: 2007-09-05
forum: The Cafe
---

### Post by oleanj on 2007-09-05
In xsane program it's possible to scan a (one)  document page directly into a pdf format document file (or other format like jpeg etc). 

But my problem is that I can't figure out how to scan  a document containing several pages into one singe pdf format file.

Today, I have to create several pdf files from one multi page pdf document, it's a bit annoying opening so many files to read the content.

thanks.

petes

---

### Post by fdhdghdg on 2007-09-05
pdfjoin *pdf

---

### Post by oleanj on 2007-09-05
Hi, thanks. 
Found out that I need to download the pdfjam package containing the pdfjoin function.

---

### Post by fdhdghdg on 2007-09-05
Yes you're right I forgot to mention it's in the pdfjam package. 

I first tried the convert command (imagemagick package) as in 'convert -compress fax *.gif doc.pdf' but it proved to be a too heavy process with lots of scans ending up segfaulting for me.

---

### Post by halfhaggis on 2008-06-23
Alternatively, change the target of the scan on the main dialogue box of xsane from "Viewer" to "Multipage"

Click "Create Project" on the new dialogue that opens up. When you scan pages, they show up there.

Once you've scanned everything, save the multipage file (file format options are pdf, ps, and tiff).

---

### Post by Adrian Challinor on 2010-02-17
HalfHaggis - Thank you

---

### Post by cariboo on 2010-02-17
CLosed due to old age.

---

