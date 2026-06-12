---
title: "How to draw geometric shapes?"
date: 2007-05-19
forum: Windows
---

### Post by Zdravko on 2007-05-19
Hi there!
I search for an application for plotting geometric shapes. Example: I want to draw a circle with center 0,0, radius = 20cm etc. The graph must be exportable into png, jpg, ps, pdf etc.
Thanks!

---

### Post by steven8 on 2007-05-19
> **Zdravko said:**
> Hi there!
I search for an application for plotting geometric shapes. Example: I want to draw a circle with center 0,0, radius = 20cm etc. The graph must be exportable into png, jpg, ps, pdf etc.
Thanks!

I only see BMP, JPG and PNG, but this program is sweet:

[QCAD]("http://www.qcad.org/qcad_features.html")

---

### Post by Lux Perpetua on 2007-05-19
The first thing that comes to mind is PostScript. ```
%!
306 306 100 0 360 arc fill
showpage
```Name it, say, test.ps. You can view it on screen or convert it to jpg, png, etc. using ghostscript:```
gs -sDEVICE=x11alpha -dBATCH test.ps     # to display the circle 
```Raw PostScript is quite bare, though. If you want axes or labels or anything in your picture, you'll have to draw and typeset them from scratch. In that case, I'd recommend MetaPost over PostScript. There's also a Linux utility called xfig, but I haven't used it. MetaPost has always been sufficient for my mathematical illustrations.

---

### Post by Zdravko on 2007-05-19
It is not free.

---

### Post by steven8 on 2007-05-19
> **Zdravko said:**
> It is not free.

QCAD is free.  It's in the repos.

---

### Post by Zdravko on 2007-05-19
I gave it a try, but... It is rather too complicated for me. Kig does the same and in a better way.

---

### Post by Lux Perpetua on 2007-05-19
> **Zdravko said:**
> It is not free.What isn't? GhostScript? MetaPost? Xfig? They're all free.

---

### Post by Zdravko on 2007-05-20
I was talking about QCAD. I didn't know the Unix version is free.

---

