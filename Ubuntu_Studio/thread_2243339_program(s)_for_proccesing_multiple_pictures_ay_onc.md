---
title: "program(s) for proccesing multiple pictures ay once?"
date: 2014-09-08
forum: Ubuntu Studio
---

### Post by spiridonios on 2014-09-08
Hi,
 
I' m into doing a big collage and i have a lot of pictures, various sizes, that i d like to turn into b&w, do something like auto levels, auto brightnes and auto contrast and fit them in A4 paper so i can send to print. Would there be a programm which can help me out do this in an auto/fast way?
My manual solution would be to open them in gimp one by one, do the desaturation, contrast, fit them in new A4 layers and export. But we re talking for about 3.000 pictures, and i'd like to have it done quick, kinda automated if possible.

---

### Post by ibjsb4 on 2014-09-08
I think your looking for Phatch.

[http://photobatch.wikidot.com/](http://photobatch.wikidot.com/)

Its in the software center.  And not for sure, but I think gimp also uses it.

Edit
Gimp does not use this package, but has a plugin for limited batch processing.

---

### Post by spiridonios on 2014-09-09
thanks a lot [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120").
Phatch was instaleed at my ubuntu studio license.
i used it and had my first tasks made, really quickly.
I was not able to find a solution to fit them in A4 though..
i m visiting some print shops in town to find out if they could do it easaly(automated) before they send to print, and see what it can become of it..
):P

---

### Post by oldfred on 2014-09-09
Imagemagick is a command line processor.

A search in Google gave lots of results for A4 question using ImageMagick a4.

First one was this:
[http://stackoverflow.com/questions/23214617/imagemagick-convert-image-to-pdf-with-a4-page-size-and-image-fit-to-page](http://stackoverflow.com/questions/23214617/imagemagick-convert-image-to-pdf-with-a4-page-size-and-image-fit-to-page)
convert image.tif -resize 575x823^> -gravity center -background white -extent 595x842 image.pdf

With a script for mulitple files & youtube video
[http://www.youtube.com/watch?v=h-XKmN8bavg](http://www.youtube.com/watch?v=h-XKmN8bavg)

[http://unix.stackexchange.com/questions/20026/convert-images-to-pdf-how-to-make-pdf-pages-same-size](http://unix.stackexchange.com/questions/20026/convert-images-to-pdf-how-to-make-pdf-pages-same-size)

---

