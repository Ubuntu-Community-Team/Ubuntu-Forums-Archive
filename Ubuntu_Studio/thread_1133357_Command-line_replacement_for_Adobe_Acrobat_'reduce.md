---
title: "Command-line replacement for Adobe Acrobat 'reduce file size' function."
date: 2009-04-22
forum: Ubuntu Studio
---

### Post by oxygen on 2009-04-22
Hi all,

I have some PDF documents which I need to reduce the size on. I download them automatically everyday and I can't modify how they are originally created. Each one is 887KB.

If I open the file with Adobe Acrobat on a Windows-based machine, I can run the 'Reduce file size' command and it outputs a file that's 74KB.

Does anyone know how I could do something similar (doesn't have to be 74KB - just a significant reduction from 887KB) using the command line only.

I want to batch process this everyday so no GUI intervention hopefully.

[LIST]
[*]The uncompress / compress functionality of PDFTK does not work.

[*]Converting using Imagemagick yields a ~100KB file, but that is a JPG image (all text is lost).
[/LIST]

I think I might be able to do it using OpenOffice in a headless setup - but Google results are confusing me!

---

### Post by kaibob on 2009-04-22
I have never seen a linux option or tool that will do what you want. You can try the following ghostscript command line on a test file to see if it might help. I use this command to reduce PDF file size, but I've never seen the reduction in file size that you're achieving with Acrobat. 

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```

In the above command, you need to change output.pdf and input.pdf.

BTW, Ghostscript seems to always issue a number of warnings after processing a file. Just ignore these.

---

### Post by oxygen on 2009-04-24
Worked like a charm! 887KB down to 99KB. Absolute legend.

---

### Post by anne_maree on 2009-05-21
Thanks heaps for this - did the job perfectly :)

---

### Post by vishnuvardan on 2009-06-29
superb tool..
9 mb compressed to 2 mb

---

### Post by gollum2000 on 2009-07-03
Awesome! Many thanks. :)

---

### Post by rykel on 2009-07-26
Thanks, it works!

No visible reduction of quality for images and fonts in the compressed file.

btw, would you know if pdftk can do the same job?

---

### Post by kaibob on 2009-07-27
> **rykel said:**
> ...btw, would you know if pdftk can do the same job?
As far as I know, pdftk cannot be used to reduce the size of a PDF file.

---

### Post by gbigot on 2009-08-04
Hi,

I tried your command but for one page, I obtain very small images in my reduce pdf.

What could I try to solve it ?

Regards

> **kaibob said:**
> I have never seen a linux option or tool that will do what you want. You can try the following ghostscript command line on a test file to see if it might help. I use this command to reduce PDF file size, but I've never seen the reduction in file size that you're achieving with Acrobat. 

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```

In the above command, you need to change output.pdf and input.pdf.

BTW, Ghostscript seems to always issue a number of warnings after processing a file. Just ignore these.

---

### Post by biodiesel-bri on 2009-08-09
Try this, it worked for me on a similar problem:

```
convert -compress JPEG -quality 100 input.pdf output.pdf
```

You'll need imagemagick installed:

```
sudo apt-get install imagemagick
```

Using a quality value less than 100 reduces the size of the image, but I achieved a massive decrease in file size on a one-page pdf (from ~50mb to 5mb) using this.  Good luck.

Not sure if this won't work unless you have JPGs in your PDF, but it is worth a try.  Convert also supports many other types of compression, check the manual for others.

---

### Post by kaibob on 2009-08-12
I was curious after reading biodiesel-bri's post and ran some tests. I created two PDF files. The first was a document created with my scanner using xsane; the second was a very long web page created with cups-pdf. I then used two different command lines to reduce the size of these documents.

The command lines and the results were:

```
convert input.pdf -compress Zip output.pdf
```

Scanned document
Original file size: 15.6 MB
Reduced file size: 961 KB

Web page
Original file size: 2.7 MB
Reduced file size: 2.3 MB

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```

Scanned document
Original file size: 15.6 MB
Reduced file size: 47 KB

Web page
Original file size: 2.7 MB
Reduced file size: 766 KB

A few comments on the above:

* The images were scanned with xsane set at 300 dpi and full color, which accounts in part for the large file size. I tried various xsane preferences to see if I could reduce the size of the PDF file but without significant success.

* The web page and scanned PDF's that were compressed with the convert command line were of reduced quality as compared with the corresponding PDF's created with the gs command line. In some cases, the difference was substantial.

---

### Post by kaibob on 2009-08-12
Post deleted by Kaibob

---

### Post by overfloat on 2009-09-11
removing
-dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen

from the command further decreased the filesize for me

---

### Post by kaibob on 2009-09-12
> **overfloat said:**
> removing
-dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen

from the command further decreased the filesize for me

The -dCompatibilityLevel option sets the PDF version and shouldn't have a significant impact on file size. The -dPDFSETTINGS option is the one that significantly reduces file size. There are instances where this option will not reduce file size and may even increase it somewhat, but this is not normally the case.

The bottom line is that PDF documents vary greatly, and the best idea is to experiment and see what works.

---

### Post by jeroen.bakker on 2009-12-19
> **biodiesel-bri said:**
> Try this, it worked for me on a similar problem:

```
convert -compress JPEG -quality 100 input.pdf output.pdf
```

You'll need imagemagick installed:

```
sudo apt-get install imagemagick
```

Using a quality value less than 100 reduces the size of the image, but I achieved a massive decrease in file size on a one-page pdf (from ~50mb to 5mb) using this.  Good luck.

Not sure if this won't work unless you have JPGs in your PDF, but it is worth a try.  Convert also supports many other types of compression, check the manual for others.
Thanks, biodiesel-bri! The "convert -compress JPEG..." works perfectly for me.

---

### Post by lambengolmor on 2010-03-10
I had a problem with the "gs" command. In particular the pdf had some vectorial graphics in that where completely removed from the compressed version. Taking out the "-dPDFSETTINGS=/screen" option fixes seems to solve everything.

---

### Post by wujastyk on 2010-03-11
> **kaibob said:**
> I have never seen a linux option or tool that will do what you want. You can try the following ghostscript command line on a test file to see if it might help. I use this command to reduce PDF file size, but I've never seen the reduction in file size that you're achieving with Acrobat. 

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```

In the above command, you need to change output.pdf and input.pdf.

BTW, Ghostscript seems to always issue a number of warnings after processing a file. Just ignore these.

Thanks for this, it's great.  I wanted slightly higher quality, so I replaced /screen with /ebook, and got what I wanted.

Also, I wrote the command into a little bash script that takes the first argument as the pdf file to be shrunk, and writes it out with "-smaller" attached to the filename.  Foo.pdf -> Foo-smaller.pdf

> #!/bin/bash
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile=${1%\.pdf}-smaller.pdf ../$1

Many thanks for the original!

Dominik

---

### Post by process91 on 2010-03-22
Seemed to be a problem with your code above, the leading ../ for the input file was causing a problem when I tried to run it as a script. It did work when I modified it as follows:

```
#!/bin/bash
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile=${1%\.pdf}-smaller.pdf $1

```

Thanks!

---

### Post by rrfx on 2010-04-28
> **lambengolmor said:**
> I had a problem with the "gs" command. In particular the pdf had some vectorial graphics in that where completely removed from the compressed version. Taking out the "-dPDFSETTINGS=/screen" option fixes seems to solve everything.

Same here with a PDF diagram output from Inkscape (Cairo pdf rendering engine). The original looks fine, the gs output has one small line of text corrupted. 

No combination of gs options have seemed to help.

---

### Post by DodgeV83 on 2010-08-06
> **lambengolmor said:**
> I had a problem with the "gs" command. In particular the pdf had some vectorial graphics in that where completely removed from the compressed version. Taking out the "-dPDFSETTINGS=/screen" option fixes seems to solve everything.

It wouldn't even work for me without removing the "-dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen".  Kept erroring out.

Thanks!

Correction: It was the "-dCompatibilityLevel=1.4" that gave errors.  It still looked better without the flags, however, so I kept them out.

---

### Post by WarrenL on 2010-10-01
> **kaibob said:**
> I have never seen a linux option or tool that will do what you want. You can try the following ghostscript command line on a test file to see if it might help. I use this command to reduce PDF file size, but I've never seen the reduction in file size that you're achieving with Acrobat. 

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```In the above command, you need to change output.pdf and input.pdf.

BTW, Ghostscript seems to always issue a number of warnings after processing a file. Just ignore these.

Worked beautifully - 16.4 MB to 1.4 MB. You've saved me considerable frustration, since PDFTK/PDFChain just doesn't seem to cut the mustard when it comes to compression.

---

### Post by hforbess on 2010-10-20
Both
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
And
convert -compress JPEG -quality 100 input.pdf output.pdf 
produce empty PDFs.  I am using a different input and output file name.Wonder what I could be doing wrong?

---

### Post by hforbess on 2010-10-20
> **hforbess said:**
> Both
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
And
convert -compress JPEG -quality 100 input.pdf output.pdf 
produce empty PDFs.  I am using a different input and output file name.Wonder what I could be doing wrong?

Argh.. I guess it helps if the pdfs you are trying to reduce are not blank to begin with.

---

### Post by rtega on 2011-03-15
For what it's worth, one thing you can do as well is first convert the pdf to djvu and then back to pdf. It seems djvu has much better compression:
pdf2djvu -d [dpi-resolution] input.pdf -o temp.djvu
djvups temp.djvu temp.ps
ps2pdf temp.ps output.pdf

The resulting pdf is even smaller than the original djvu. Replace the [dpi-resolution] with the resulotion you scanned your original with. pdf2djvu sets it to 300dpi. I'd like to use 600dpi for decent quality. It reduces a 23MB file into a 2.6 MB pdf.

---

### Post by AMTQ on 2011-08-17
> **kaibob said:**
> I have never seen a linux option or tool that will do what you want. You can try the following ghostscript command line on a test file to see if it might help. I use this command to reduce PDF file size, but I've never seen the reduction in file size that you're achieving with Acrobat. 

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```

In the above command, you need to change output.pdf and input.pdf.

BTW, Ghostscript seems to always issue a number of warnings after processing a file. Just ignore these.

works great, thanks! one reason less to stick with M$ :)

---

### Post by JuanPabloCuervo on 2011-08-18
> **oxygen said:**
> Hi all,

I have some PDF documents... 887KB
Google results are confusing me!
[SIZE=4]887KB ?[/SIZE]

[SIZE=2]are you insane?[/SIZE]
[SIZE=2]buy a 3TB hitachi hdd.[/SIZE]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472)
[http://www.hitachigst.com/internal-drives/desktop/deskstar/deskstar-7k3000](http://www.hitachigst.com/internal-drives/desktop/deskstar/deskstar-7k3000)

if need server quality buy Ultrastar.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145477](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145477)

1TB = [http://en.wikipedia.org/wiki/Terabyte](http://en.wikipedia.org/wiki/Terabyte)

---

### Post by majedaly on 2011-10-31
> **kaibob said:**
> I have never seen a linux option or tool that will do what you want. You can try the following ghostscript command line on a test file to see if it might help. I use this command to reduce PDF file size, but I've never seen the reduction in file size that you're achieving with Acrobat. 

```
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```In the above command, you need to change output.pdf and input.pdf.

BTW, Ghostscript seems to always issue a number of warnings after processing a file. Just ignore these.
Thanks, Worked like a charm:D

---

### Post by christopher.wortman on 2011-10-31
> **oxygen said:**
> Hi all,

I have some PDF documents which I need to reduce the size on. I download them automatically everyday and I can't modify how they are originally created. Each one is 887KB.

If I open the file with Adobe Acrobat on a Windows-based machine, I can run the 'Reduce file size' command and it outputs a file that's 74KB.

Does anyone know how I could do something similar (doesn't have to be 74KB - just a significant reduction from 887KB) using the command line only.

I want to batch process this everyday so no GUI intervention hopefully.

[LIST]
[*]The uncompress / compress functionality of PDFTK does not work.
[*]Converting using Imagemagick yields a ~100KB file, but that is a JPG image (all text is lost).
[/LIST]

I think I might be able to do it using OpenOffice in a headless setup - but Google results are confusing me!


Have you tried Acrobat Reader for Linux and Unix clients?

[http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/)

Get the deb for Ubuntu of 9.4.2 lol Does the same job as the Windows version here...

> **JuanPabloCuervo said:**
> [SIZE=4]887KB ?[/SIZE]

[SIZE=2]are you insane?[/SIZE]
[SIZE=2]buy a 3TB hitachi hdd.[/SIZE]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145472)
[http://www.hitachigst.com/internal-drives/desktop/deskstar/deskstar-7k3000](http://www.hitachigst.com/internal-drives/desktop/deskstar/deskstar-7k3000)

if need server quality buy Ultrastar.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822145477](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145477)

1TB = [http://en.wikipedia.org/wiki/Terabyte](http://en.wikipedia.org/wiki/Terabyte)
Not everyone has $400 USD laying around...

---

### Post by rws221 on 2012-08-20
This still works. Thanks a bunch! :D

---

### Post by smartboyhw on 2012-08-21
Er, I think that modern drives at least one TB (though my notebook only has 300GB, and I think that's the minimum.
 
It is not difficult to download the trial version of Adobe Acrobat, right? Just install it. BTW, really, why do you need command-line / terminal to reduce file size? It isn't necessary, and definitely 887KB is a very small file. The pdf compression is excellent by all means.
 
Regards,
Howard Chan
Ubuntu Studio Team Member in [https://wiki.ubuntu.com/UbuntuStudio/TeamStructure](https://wiki.ubuntu.com/UbuntuStudio/TeamStructure)

---

### Post by Elfy on 2012-08-21
Old thread closed.

---

