---
title: "PDF to PNG with fixed resolution"
date: 2011-04-01
forum: Ubuntu Studio
---

### Post by lucacerone on 2011-04-01
Dear all,
I'm in need to convert a bunch of PDF files to PNG (or JPEG).
If I use a program like Inkscape setting the DPI for the output
file the result is fine (the original PDF are vectorial so I can resize them as I like). 
The problem is that I've many figures to
resize and would like to convert them using some batch approach.
I've tried the mogrify command (part of ImageMagick) like this:
> mogrify -format png -resize 800x600 *.pdf
but I don't like the final outcome.
The images are "blurred" like if they're first converted from 
pdf to png and then resized.
What I'd have to do is probably "rastering" (is this the right term?) them, setting the resolution of the output file rather than the dimension.
Has anyone some good suggestion?
Thanks a lot in advance,
Luca

---

### Post by laubblatt on 2011-11-04
the density option is important - as the default of convert  usually creates some low res raster images.

convert -density 300 *.pdf newfile.png

see also:
[http://vollnixx.wordpress.com/2011/03/08/convert-pdf2png-with-imagick-linux/](http://vollnixx.wordpress.com/2011/03/08/convert-pdf2png-with-imagick-linux/)

---

