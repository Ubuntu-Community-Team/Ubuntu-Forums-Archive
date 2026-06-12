---
title: "Change multiple .jpg file sizes - ImageMagick?"
date: 2008-11-13
forum: Ubuntu Studio
---

### Post by NEUR0M4NCER on 2008-11-13
Hi all - is there any simple way of lowering the file-size of a bunch of different .jpg's across different folders to 150kb? ImageMagick looks promising, but TBH I don't really want to learn the complex syntax to perform a one time only operation... Yes, I know it's lazy.

---

### Post by nowardev on 2008-11-14
xD 

well i have made my little converter .. it's for kde i know but look at my signature 

anyway...

you have to install imagemagick then just type this 

convert -resize  720x576 input output

[B]
convert input-file [options] output-file[/B]

---

### Post by NEUR0M4NCER on 2008-11-14
Thanks nowardev... I spent a few hours doing it manually with the Gimp last-night..... Man was that a pain in the behind.

---

