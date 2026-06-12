---
title: "Cleartype/Anti-Aliasing/Subpixel-Smoothing fonts in WINE"
date: 2009-07-11
forum: Wine
---

### Post by There Was A Time on 2009-07-11
I have the latest version of Wine installed and managed to get MS Office 2007 installed without any problems. Except it has become evident, that fonts do not use window's Cleartype, and appear ugly and jagged.

[s]Is there a way to turn on Cleartype? I've tried changing fontsmoothing "0" user.reg to "1", but that had no effect.[/s]

Okay, with a registry tweak, I've got most fonts working, but Calibri and Cambria refuse to render properly. I have them working in Ubuntu with a fonts.conf edit, but that change hasn't carried over.

Has anyone had any luck with this, as from searching for screenshots, I've found that people have it enabled.

---

### Post by Jonathan Moerman on 2011-06-14
I've posted this on several threads:

[FONT="Arial"]This is very easy to fix: 
1. install FontForge
2. navigate to the fonts directory.
3. open the font you want (Calibri) and _do NOT import the bitmaps  fonts_
4. file -> generate fonts : save as TrueType and with the option _"No Bitmap Fonts"_ (and I recommend to disable the validate before saving option)
5. rename and replace the font
6. repeat this with the Italic and bold variants[/FONT]

this fixes the problem for calabri and cambria.

---

### Post by Brebs on 2011-06-16
You probably the 2 tweaks (*embeddedbitmap* false and *scalable* false) in ~/.fonts.conf - see [post](http://forums.gentoo.org/viewtopic-p-6183606.html#6183606) in huge fonts thread.

---

### Post by Jonathan Moerman on 2011-06-16
wine doesn't read the .fonts.conf file so that doesn't work

---

