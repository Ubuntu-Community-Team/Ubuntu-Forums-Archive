---
title: "convert images to pdf"
date: 2009-09-16
forum: Ubuntu Studio
---

### Post by ningke on 2009-09-16
If you need to convert a bunch of images (possibly from a scanner) into a single pdf document, this is how you do it.

Install ImageMagick (Yes, with the extra k) from synaptic package manager.

On a command line,
```

ning@sandbox:~/images$ convert img1.jpg img2.jpg img3.jpg all_images.pdf

```It is that simple!

---

### Post by pattinsonrobert on 2009-09-17
Hi Everyone..

I have installed PDF Generator Professional manually.Now it can convert word,ppt,excel,ps to pdf correctly,but can't work to image(bmp,gif,jpg,tif).I have check the server log ,it always show "send virtual input to acrobat professional retry step no 1 ...".and the result returned to me always is "...timeout.". 
 I have installed photoshop cs 2 ,and I think the PDF maker has registered.So now I have no idea what's wrong with it. 

 does anyone meet the same problem or know how to resolve? 
 waiting for your answer!Thank you!

---

### Post by stinger30au on 2009-09-17
pdftk is the go

[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

sudo apt-get install pdftk

it will convert pdf files to what ever u want and slice and dice them

---

### Post by keplerspeed on 2009-09-17
I wrote a script to convert a folder full of tiff files (eg Page 27.tif) into a single pdf document.

```

#! /bin/bash

# Required packages:
# pdftk (combining docs)
# libtiff-tools (converting tiff to pdf via tiff2pdf)

# convert tiff files to pdf using tiff2pdf:
echo "Making pdf directory, 'pdf_output'"
mkdir pdf_output

echo "*****************************"
echo "Begin converting tiff to pdf:"
for a in `seq 1 34`; do
	echo "Completing unit $a of 34"
	tiff2pdf -o pdf_output/$a.pdf Page\ $a.tif
done
echo "Finished converting tiff to pdf."

echo "*****************************"
echo "Begin combining pdf docs."
echo "Combining 1 and 2."
pdftk pdf_output/1.pdf pdf_output/2.pdf cat output pdf_output/combined.pdf

for a in `seq 3 34`; do
	echo "Completing unit $a of 34"
	pdftk pdf_output/combined.pdf pdf_output/$a.pdf cat output pdf_output/combined_mid.pdf
	mv pdf_output/combined_mid.pdf pdf_output/combined.pdf
done
echo "All documents combined. DONE."

```

---

