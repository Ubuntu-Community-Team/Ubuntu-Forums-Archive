---
title: "Ubuntu Imagemagick"
date: 2008-07-01
forum: Repositories &amp; Backports
---

### Post by bwhiti on 2008-07-01
Hi

Not sure if this is the right place but I am trying to crop an svg image to a small size and save as a new svg image to serve in a pdf document.

I have imagemagick from the ubuntu repository but everytime I run the command I get this error.

convert: no image vector graphics 'new.svg'

The commad I am using at present for testing before I place into a server side script is:

convert old.svg -crop 100x100+100+100 new.svg

If I run convert and transform the svg to png everything runs fine.

Can anybody please help as this really has to be a svg after cropping to retain the quality when zooming the pdf.

Thanks

Barry

---

### Post by konungursvia on 2008-07-01
I would try using Gimp or Inkscape, open the svg, scale it or crop it, then save it as an svg again.

---

### Post by kaibob on 2008-07-02
I'm not sure what the issue is but convert support of SVG apparently is not very good and requires two additional files:

*Requires libxml2 and freetype-2. Note that SVG is a very complex specification so support is still not complete.*

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

As an aside (which is probably none of my business), is it your intention for the final image to measure 100x100? 

[http://www.imagemagick.org/script/command-line-options.php#crop](http://www.imagemagick.org/script/command-line-options.php#crop)

---

### Post by bwhiti on 2008-07-02
Hi

My intension is that I have a full sized svg map on our server and we build a pdf document that holds slices of this map depending on your location.

The svg may not be 100x100 Im just trying to get imagemagick to generate this on the command line as an example to prove if it can be done with this tool or not.  If it can then I can write a server side script to make these calls to image magick with the dimensions needed to get the correct crop's from the map to embed into the pdf.

I have managed to get imagemagick to work with converting an svg to a png but this quality of image is no where good enough for our needs hence why we need to convert back to an svg.

After many attempts and installing lots of different librarys such as freetype and libxml2-dev I know get the error

convert: no image vector graphics `test_crop.svg'.

after running 

convert Jim_SVG.svg -crop 100X100+100+100 test_crop.svg

Thanks for all your help

Barry

---

