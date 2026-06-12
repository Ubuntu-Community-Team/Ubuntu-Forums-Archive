---
title: "Editing .eps images without loss of quality"
date: 2009-11-29
forum: Ubuntu Studio
---

### Post by GammaPoint on 2009-11-29
Hi, I'm trying to edit some .eps images produced by gnuplot for a paper I'm writing. If I plot the *.eps images directly from gnuplot (into latex, which is why I need eps) then they look fine. Problem is that I'm first editing the images in GIMP (actually appending two eps images together with some other modifications). I then resave as an eps and the image is pretty severely hit with a loss in quality. 

Any ideas on what I can do to avoid this? And should I anti-alias the graphics or the text when I first open the original *.eps images? What does that do exactly?

Thanks in advance to anyone who can help me with this!

---

### Post by Mike'sHardLinux on 2009-11-29
.eps should be a vector image, though I have seen bitmaps. GIMP is a bitmap editing software, which may explain your problem. Have you tried Inkscape, Scribus, or Xara Extreme? Those are vector editors.

---

### Post by raboofje on 2009-11-29
Inkscape might be able to handle it.

---

### Post by GammaPoint on 2009-11-30
Thanks for the feedback! I think your suggestion will fix my problem. I'll try it later today.

---

