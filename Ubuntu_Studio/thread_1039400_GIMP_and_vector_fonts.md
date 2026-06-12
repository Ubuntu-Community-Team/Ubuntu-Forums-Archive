---
title: "GIMP and vector fonts"
date: 2009-01-14
forum: Ubuntu Studio
---

### Post by x1a4 on 2009-01-14
Hi,
I'm creating an ad for a phone book and one of the requirements is that I'm supposed to use vector fonts.  What are vector fonts?  How do I use them with GIMP?  

Thank you.

---

### Post by mcduck on 2009-01-15
If they want vector fonts, Gimp probably isn't the correct tool for the task. Unless they are able to open and use Gimp's native file format and you send all used fonts with the file).

Gimp is bitmap graphics editor. To do the work you should most likely use vector graphics editor, like Inkscape. Or alternatively some desktop publishing tool like Scribus.

(Vector fonts are the most common font type used these days, for example all TrueType fonts are vectors. But the important thing in this case is that the fonts should stay as vectors all the way to the press. So you can't use any bitmap image formats like BMP, JPG or PNG.)

One more thing you need to consider is that usually the fonts used are not saved as part of the image. You'll need to either convert the text into vector paths, include used fonts with the vector image file or send the final image in PDF format (which will include all fonts used).

---

### Post by Cybervirem on 2009-01-20
yes, you have to use different softs to obtain a pre-press file ; think to use same color profiles (.icc files) in gimp, inkscape and scribus.

You can use gimp to work around, let us say, a 300dpi raster image ; then you use inkscape to add fonts, and then export from inkscape to high def pdf (pdf/x-3)

To obtain good cmyk, i use scribus (thru ps from inkscape) to obtain cmyk pdf ; i also use moonshiner, a gs guy  to obtain pdf from ps ([http://moonshiner.sourceforge.net/](http://moonshiner.sourceforge.net/))

---

