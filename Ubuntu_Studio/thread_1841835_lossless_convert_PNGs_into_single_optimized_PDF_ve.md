---
title: "lossless convert PNGs into single optimized PDF version 1.6"
date: 2011-09-10
forum: Ubuntu Studio
---

### Post by Marek Cupak on 2011-09-10
hello there,

i'm already a bit familiar with ImageMagick's convert, but how do i parametrize it to losslessly convert PNGs into single PDF file (optimized PDF-1.6 format)?

many thanks in advance :)

---

### Post by sgx on 2011-09-10
scribus and okular and inkscape have an 'import postscript as pdf', and 'export pdf' type options. Ghostscript and ps2pdf should be installed.

[http://wiki.inkscape.org/wiki/index.php/FAQ](http://wiki.inkscape.org/wiki/index.php/FAQ)  this faq has important
.png scaling info for inkscape, and more great details

Perhaps use inkscape to create a postscript/eps/svg doc with the .png files, and check the output for quality. If more is needed,
try scribus okular use 'save as' or 'export as' to do some magic.

pdfedit may also be useful, with loads of options, and a preferences panel to make them easy to use. These apps may also export as xml, so your final output is not limited just to pdf.

Cheers  (work with copies of your valuable photos, backups to media
are good luck before editing :guitar:

---

### Post by Marek Cupak on 2011-09-10
gscan2pdf does the job (and some more) too. format PDF-1.4, but the resulting filesize is ok when importing PNGs and choosing appropriate compression type

---

