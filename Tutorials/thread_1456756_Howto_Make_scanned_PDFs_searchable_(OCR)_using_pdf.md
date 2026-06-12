---
title: "Howto: Make scanned PDFs searchable (OCR) using pdfocr"
date: 2010-04-17
forum: Tutorials
---

### Post by tuxcantfly on 2010-04-17
**What pdfocr is for**

Suppose you have a PDF document that was made using a scanner, or otherwise consists of image data but doesn't have text data. Such a PDF can't be searched by PDF readers or desktop search applications. pdfocr is a simple utility I made that takes a PDF file, then generates a new one that has the text layer added, so it's searchable by your PDF reader and can be indexed by your desktop search application, but is still identical when printed.

**What pdfocr is not for**

This is only of use if your PDF was made from a scanned source; if you exported your PDF from OpenOffice or the like it already has a text layer so this is unnecessary.

If what you're looking for is to simply extract the plain text from a PDF file, but not to embed the text into the PDF file, see [this guide](http://ubuntuforums.org/showthread.php?t=880471).

**Compatibility**

This guide will work on Ubuntu Karmic (9.10) or Lucid (10.04); the dependencies for this software don't build on older versions.

**Installing pdfocr**

The easiest way to install pdfocr is to add my [PPA](https://launchpad.net/~gezakovacs/+archive/pdfocr) and use apt-get. If you would instead prefer to install it manually, see [here](http://github.com/gkovacs/pdfocr/) for instructions

```

sudo add-apt-repository ppa:gezakovacs/pdfocr
sudo apt-get update
sudo apt-get install pdfocr

```

**Using pdfocr to add a text layer to your scanned PDF file**

Open a terminal, go to the directory that has the PDF file you want to convert, and enter (substituting input.pdf with the input PDF file, and output.pdf with the output PDF file)

```

pdfocr -i input.pdf -o output.pdf

```

Now wait as OCR is performed on the PDF file page-by-page, and the output file is generated. This should take a few seconds per page, depending on the resolution of your PDF file (high-res PDF files get better accuracy, but will take longer). Once done, you should now have a searchable PDF at output.pdf.

**Credits**

[pdfocr](http://github.com/gkovacs/pdfocr/) was written by me (Geza Kovacs). It is simply a script which automates the following process:

1. Splitting the PDF file into separate pages using pdftk
2. Extracting out the image data using pdfimages
3. Doing OCR (optical character recognition) using cuneiform
4. Embedding the detected text back into the PDF file using hocr2pdf
5. Merging together the files using pdftk.

Hence, if you want more fine-grained control than the defaults, you can just invoke these utilities manually. Source is available on [github](http://github.com/gkovacs/pdfocr/). Feedback is welcome.

---

### Post by Yva on 2010-04-19
Sounds like an awesome program, unfortunately I've got the following errors any idea why?

$pdfocr -i Acceptance.pdf -o test.pdf
Input file is /mnt/data/tmp/Acceptance.pdf
Output file is /mnt/data/tmp/test.pdf
Using working dir /tmp/d20100419-4215-ohxah0
Getting info from PDF file

Warning: no info dictionary found
NumberOfPages: 1

Converting 1 pages
==========
Extracting page 1
Converting page 1 to ppm
Running OCR on page 1
PUMA_XFinalrecognition failed.
Cuneiform for Linux 0.9.0
Error while running OCR on page 1
Merging together PDF files
Error: Failed to open PDF file: 
   /tmp/d20100419-4215-ohxah0/*-new.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Updating PDF info for /mnt/data/tmp/test.pdf
Error: Failed to open PDF file: 
   /tmp/d20100419-4215-ohxah0/merged.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Cleaning up temporary files

---

### Post by Sub101 on 2010-04-19
Very nice. And certainly extremely useful.

Thanks.

I did get a few errors, but none of them stopped the program working.

Errors below.
```
Warning: Image x/y resolution not set, defaulting to: 300
Warning: tag mismatch: 'b' can not close last open: 'i'
Warning: tag mismatch: 'span' can not close last open: 'b'
Warning: tag mismatch: 'p' can not close last open: 'b'
Warning: tag mismatch: 'div' can not close last open: 'b'
Warning: tag mismatch: 'body' can not close last open: 'b'
Warning: tag mismatch: 'html' can not close last open: 'b'
Warning: unclosed tag: 'b'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'div'
Warning: unclosed tag: 'body'
Warning: unclosed tag: 'html'

```

---

### Post by a.w.howell on 2010-04-21
I am excited about this script, I think it will be very useful. However I ran into a different error than the one posted above:

```
aaron@aaron-desktop:~$ pdfocr -i 0175.pdf -o out3.pdf
Input file is /home/aaron/0175.pdf
Output file is /home/aaron/out3.pdf
Using working dir /tmp/d20100421-20950-4g11i8
Getting info from PDF file

InfoKey: Creator
InfoValue: XSane version 0.996 (sane 1.0) - by Oliver Rauch
InfoKey: Title
InfoValue: XSane scanned image
InfoKey: Producer
InfoValue: XSane 0.996
InfoKey: CreationDate
InfoValue: D:20100421215339+00'00'
NumberOfPages: 1

Converting 1 pages
==========
Extracting page 1
Converting page 1 to ppm
Running OCR on page 1
1.ppm is not a BMP file.
Cuneiform for Linux 0.9.0
Error while running OCR on page 1
Merging together PDF files
Error: Failed to open PDF file: 
   /tmp/d20100421-20950-4g11i8/*-new.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Updating PDF info for /home/aaron/out3.pdf
Error: Failed to open PDF file: 
   /tmp/d20100421-20950-4g11i8/merged.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Cleaning up temporary files
```

Notice the "1.ppm is not a BMP file." line. I get a similar error if I run cuneiform by itself:

```
aaron@aaron-desktop:~$ cuneiform -f hocr -o out.hocr 0175.pdf
Cuneiform for Linux 0.9.0
0175.pdf is not a BMP file.
```

It's as if cuneiform defaults to assuming the input file is a bmp. Is there a way to change this?

I should also mention that I am on amd64, and I initially had problems with cuneiform throwing an error. I had to add /usr/local/lib64 to a .conf file in /etc/ld.so.conf.d, and running ldconfig (per [https://answers.launchpad.net/cuneiform-linux/+question/100695](https://answers.launchpad.net/cuneiform-linux/+question/100695)). After making this change cuneiform seems to work, but there still could be other unseen issues.

Thanks.

---

### Post by meho_r on 2010-04-25
Thanks a lot, great utility.

---

### Post by clasikowski on 2010-04-29
Hi!

> **a.w.howell said:**
> 
It's as if cuneiform defaults to assuming the input file is a bmp. Is there a way to change this?



Yes; you just have to install

**libmagick++-dev**

before compiling cuneiform, then it'll be able to recognize just about every input format (all imagemagick is able to use, to be precise)

so long
clasikowski aka hank

---

### Post by the_summer on 2010-04-29
Its a great helper. I tried it on some files. The ocr seem to work, but when i search for words, the marks are often quite far away from the searched word.
Maybe it's because there is always the warning:

```
Warning: Image x/y resolution not set, defaulting to: 300

```

Is there a way to manually set different values for the resolution.
I didnt find something about it in the man-page.

Best wishes

 Jan

---

### Post by mdwy62 on 2010-05-07
Great utility!  Just used in on a 60 page document. Many Thanks. In evince, I also find that the placement of the search term results is off.  Any suggestions how to improve this would be appreciated.

---

### Post by nanonils on 2010-05-20
> **clasikowski said:**
> Hi!



Yes; you just have to install

**libmagick++-dev**

before compiling cuneiform, then it'll be able to recognize just about every input format (all imagemagick is able to use, to be precise)

so long
clasikowski aka hank

Hank,
Does that mean install libmagick++-dev before doing "sudo add-apt-repository ppa:gezakovacs/pdfocr
sudo apt-get update
sudo apt-get install pdfocr"?

I do have libmagick++-dev installed and did a reinstall of Geza's pdfocr but I still get the following error output:
pdfocr -i 1.pdf -o 2.pdf
Input file is /home/nils/1.pdf
Output file is /home/nils/2.pdf
Using working dir /tmp/d20100520-15606-f6vqow
Getting info from PDF file

InfoKey: Title
InfoValue: /tmp/simple-scan-RDLXCV.pdf
InfoKey: Producer
InfoValue: ImageMagick 6.5.7-8 2009-11-26 Q16 [http://www.imagemagick.org](http://www.imagemagick.org)
InfoKey: ModDate
InfoValue: D:20100520074947
InfoKey: CreationDate
InfoValue: D:20100520074947
NumberOfPages: 1

Converting 1 pages
==========
Extracting page 1
Converting page 1 to ppm
Running OCR on page 1
*** buffer overflow detected ***: cuneiform terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f742e9131a7]
/lib/libc.so.6(+0xfe060)[0x7f742e912060]
/usr/lib/cuneiform/libfon32.so.0.9.0(+0x21a5c)[0x7f7429d93a5c]
/usr/lib/cuneiform/libfon32.so.0.9.0(+0x2226a)[0x7f7429d9426a]
/usr/lib/cuneiform/libfon32.so.0.9.0(FONRecog2Glue+0x1e7)[0x7f7429d81f47]
/usr/lib/cuneiform/libpass2.so.0.9.0(+0x73b3)[0x7f742a8793b3]
/usr/lib/cuneiform/libpass2.so.0.9.0(+0x7592)[0x7f742a879592]
/usr/lib/cuneiform/libpass2.so.0.9.0(+0xab63)[0x7f742a87cb63]
/usr/lib/cuneiform/libpass2.so.0.9.0(p2_proc+0xa7a)[0x7f742a87d85a]
/usr/lib/cuneiform/librstr.so.0.9.0(+0x98e01)[0x7f742ad4de01]
/usr/lib/cuneiform/librstr.so.0.9.0(RSTRRecognizeMain+0x224)[0x7f742ad60184]
/usr/lib/cuneiform/librstr.so.0.9.0(RSTRRecognize+0x19)[0x7f742ad60dc9]
/usr/lib/cuneiform/libcuneiform.so.0.9.0(+0xcafe)[0x7f742f343afe]
/usr/lib/cuneiform/libcuneiform.so.0.9.0(PUMA_XFinalRecognition+0xd1)[0x7f742f345091]
cuneiform[0x403beb]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f742e832c4d]
cuneiform[0x402a19]
======= Memory map: ========
00400000-00405000 r-xp 00000000 08:01 59229185                           /usr/bin/cuneiform
00604000-00605000 r--p 00004000 08:01 59229185                           /usr/bin/cuneiform
00605000-00606000 rw-p 00005000 08:01 59229185                           /usr/bin/cuneiform
010d0000-04c92000 rw-p 00000000 00:00 0                                  [heap]
7f741ef2d000-7f741ef31000 r-xp 00000000 08:01 59232850                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/dib.so
7f741ef31000-7f741f130000 ---p 00004000 08:01 59232850                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/dib.so
7f741f130000-7f741f131000 r--p 00003000 08:01 59232850                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/dib.so
7f741f131000-7f741f132000 rw-p 00004000 08:01 59232850                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/dib.so
7f74236b5000-7f74236b6000 ---p 00000000 00:00 0 
7f74236b6000-7f7423eb6000 rw-p 00000000 00:00 0 
7f7423eb6000-7f7423eb7000 ---p 00000000 00:00 0 
7f7423eb7000-7f74246b7000 rw-p 00000000 00:00 0 
7f74246b7000-7f74246b8000 ---p 00000000 00:00 0 
7f74246b8000-7f7424eb8000 rw-p 00000000 00:00 0 
7f7424eb8000-7f7424ec1000 r-xp 00000000 08:01 59232948                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/pnm.so
7f7424ec1000-7f74250c0000 ---p 00009000 08:01 59232948                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/pnm.so
7f74250c0000-7f74250c1000 r--p 00008000 08:01 59232948                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/pnm.so
7f74250c1000-7f74250c2000 rw-p 00009000 08:01 59232948                   /usr/lib/ImageMagick-6.5.7/modules-Q16/coders/pnm.so
7f74250c2000-7f74250c7000 r-xp 00000000 08:01 59231793                   /usr/lib/libXdmcp.so.6.0.0
7f74250c7000-7f74252c6000 ---p 00005000 08:01 59231793                   /usr/lib/libXdmcp.so.6.0.0
7f74252c6000-7f74252c7000 r--p 00004000 08:01 59231793                   /usr/lib/libXdmcp.so.6.0.0
7f74252c7000-7f74252c8000 rw-p 00005000 08:01 59231793                   /usr/lib/libXdmcp.so.6.0.0
7f74252c8000-7f74252ca000 r-xp 00000000 08:01 59231782                   /usr/lib/libXau.so.6.0.0
7f74252ca000-7f74254ca000 ---p 00002000 08:01 59231782                   /usr/lib/libXau.so.6.0.0
7f74254ca000-7f74254cb000 r--p 00002000 08:01 59231782                   /usr/lib/libXau.so.6.0.0
7f74254cb000-7f74254cc000 rw-p 00003000 08:01 59231782                   /usr/lib/libXau.so.6.0.0
7f74254cc000-7f74254d3000 r-xp 00000000 08:01 50824095                   /lib/librt-2.11.1.so
7f74254d3000-7f74256d2000 ---p 00007000 08:01 50824095                   /lib/librt-2.11.1.so
7f74256d2000-7f74256d3000 r--p 00006000 08:01 50824095                   /lib/librt-2.11.1.so
7f74256d3000-7f74256d4000 rw-p 00007000 08:01 50824095                   /lib/librt-2.11.1.so
7f74256d4000-7f74256ef000 r-xp 00000000 08:01 59232788                   /usr/lib/libxcb.so.1.1.0
7f74256ef000-7f74258ee000 ---p 0001b000 08:01 59232788                   /usr/lib/libxcb.so.1.1.0
7f74258ee000-7f74258ef000 r--p 0001a000 08:01 59232788                   /usr/lib/libxcb.so.1.1.0
7f74258ef000-7f74258f0000 rw-p 0001b000 08:01 59232788                   /usr/lib/libxcb.so.1.1.0
7f74258f0000-7f74258f4000 r-xp 00000000 08:01 50824123                   /lib/libuuid.so.1.3.0
7f74258f4000-7f7425af3000 ---p 00004000 08:01 50824123                   /lib/libuuid.so.1.3.0
7f7425af3000-7f7425af4000 r--p 00003000 08:01 50824123                   /lib/libuuid.so.1.3.0
7f7425af4000-7f7425af5000 rw-p 00004000 08:01 50824123                   /lib/libuuid.so.1.3.0
7f7425af5000-7f7425b02000 r-xp 00000000 08:01 59232191                   /usr/lib/libgomp.so.1.0.0
7f7425b02000-7f7425d01000 ---p 0000d000 08:01 59232191                   /usr/lib/libgomp.so.1.0.0
7f7425d01000-7f7425d02000 r--p 0000c000 08:01 59232191                   /usr/lib/libgomp.so.1.0.0
7f7425d02000-7f7425d03000 rw-p 0000d000 08:01 59232191                   /usr/lib/libgomp.so.1.0.0
7f7425d03000-7f7425e34000 r-xp 00000000 08:01 59231778                   /usr/lib/libX11.so.6.3.0
7f7425e34000-7f7426034000 ---p 00131000 08:01 59231778                   /usr/lib/libX11.so.6.3.0
7f7426034000-7f7426035000 r--p 00131000 08:01 59231778                   /usr/lib/libX11.so.6.3.0
7f7426035000-7f7426039000 rw-p 00132000 08:01 59231778                   /usr/lib/libX11.so.6.3.0
7f7426039000-7f7426050000 r-xp 00000000 08:01 59231747                   /usr/lib/libICE.so.6.3.0
7f7426050000-7f742624f000 ---p 00017000 08:01 59231747                   /usr/lib/libICE.so.6.3.0
7f742624f000-7f7426250000 r--p 00016000 08:01 59231747                   /usr/lib/libICE.so.6.3.0
7f7426250000-7f7426251000 rw-p 00017000 08:01 59231747                   /usr/lib/libICE.so.6.3.0
7f7426251000-7f7426254000 rw-p 00000000 00:00 0 
7f7426254000-7f742625c000 r-xp 00000000 08:01 59231776                   /usr/lib/libSM.so.6.0.1
7f742625c000-7f742645b000 ---p 00008000 08:01 59231776                   /usr/lib/libSM.so.6.0.1
7f742645b000-7f742645c000 r--p 00007000 08:01 59231776                   /usr/lib/libSM.so.6.0.1
7f742645c000-7f742645d000 rw-p 00008000 08:01 59231776                   /usr/lib/libSM.so.6.0.1
7f742645d000-7f7426465000 r-xp 00000000 08:01 59232423                   /usr/lib/libltdl.so.7.2.1
7f7426465000-7f7426665000 ---p 00008000 08:01 59232423                   /usr/lib/libltdl.so.7.2.1Cuneiform for Linux 0.9.0
Error while running OCR on page 1
Merging together PDF files
/tmp/d20100520-15606-f6vqow/*-new.pdf not found as file or resource.
Error: Failed to open PDF file: 
   /tmp/d20100520-15606-f6vqow/*-new.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Updating PDF info for /home/nils/2.pdf
/tmp/d20100520-15606-f6vqow/merged.pdf not found as file or resource.
Error: Failed to open PDF file: 
   /tmp/d20100520-15606-f6vqow/merged.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Cleaning up temporary files

---

### Post by texla on 2010-06-23
> **tuxcantfly said:**
> **What pdfocr is for**

**Installing pdfocr**

The easiest way to install pdfocr is to add my [PPA](https://launchpad.net/~gezakovacs/+archive/pdfocr) and use apt-get. If you would instead prefer to install it manually, see [here](http://github.com/gkovacs/pdfocr/) for instructions

```

sudo add-apt-repository ppa:gezakovacs/pdfocr
sudo apt-get update
sudo apt-get install pdfocr

```

**Using pdfocr to add a text layer to your scanned PDF file**

Open a terminal, go to the directory that has the PDF file you want to convert, and enter (substituting input.pdf with the input PDF file, and output.pdf with the output PDF file)

```

pdfocr -i input.pdf -o output.pdf

```

Now wait as OCR is performed on the PDF file page-by-page, and the output file is generated. This should take a few seconds per page, depending on the resolution of your PDF file (high-res PDF files get better accuracy, but will take longer). Once done, you should now have a searchable PDF at output.pdf.


Worked great for me - thanks!  I had to go in and fix about 20% of the text but this helped a lot - will be using this more... ):P

---

### Post by cataddict on 2010-07-02
OK, I'm new to Linux so this may be some config problem of mine. I've installed pdfocr from the PPA and when I run the script it fails on the line:

sh "pdftoppm #{basefn+'.pdf'} > #{basefn+'.ppm'}"

The line runs, but pdftoppm is not allowing a redirection via ">" into the output .ppm file. It just creates a 0 byte file and outputs the pdftoppm help message. pdfocr carries on because it just checks to see if a .ppm file is there, which there is, but it's empty.

If I run pdftoppm by hand using the same syntax, it fails the same way. If in run it using a PPM-root file name (not >), it works fine. pdftoppm manpage doesn't say anything about redirection.

FYI Ubuntu Lucid 10.04

Ideas??

---

### Post by nanonils on 2010-07-02
As of note, Google Docs allows now uploading PDFs that can be OCRed (must check box). This works surprisingly well even with low resolution PDF files. The disappointing thing is that the PDF pages appear embedded in a GDoc with the text wrapping around them and not "embedded". Text can obviously be searched but you won't be pointed to the actual position in the PDF file, just the surrounding text.

It is a killer feature if you (hypothetically) wanted to convert a paper book into text: simply snap pictures with your camera, bundle it into a single PDF, convert it into text and delete the pictures of the pages. Manual reformatting required.

---

### Post by walshy2 on 2010-07-02
Great info just used it and it works great.

Cheers,
D[.]("http://www.flightsimulatornow.com/?p=28")

---

### Post by varunto on 2010-07-04
Thanks, sounds just what I was looking for. Unfortunately, I haven't got any success. I got the following error:

> Extracting page 1
Converting page 1 to ppm
Running OCR on page 1
Magick: NoDecodeDelegateForThisImageFormat `1.ppm' @ constitute.c/ReadImage/530
Cuneiform for Linux 0.9.0
Error while running OCR on page 1

I think I installed correctly all of the imagemagick stuff. Any ideas on what's going wrong?

---

### Post by Bif Powell on 2010-07-09
thank you very much for posting this useful information - this worked really well for me for a few documents but then I installed the pdftotext per the other instruction thread from that post and it seems like I can't process any more, I get the following errors at the console

any guidance appreciated

> john@ubuntu:~$ pdfocr -i /home/john/firsttest.pdf -o output.pdf
Input file is /home/john/firsttest.pdf
Output file is /home/john/output.pdf
Using working dir /tmp/d20100708-8664-k9qzbg
Getting info from PDF file

InfoKey: Creator
InfoValue: PScript5.dll Version 5.2
InfoKey: Title
InfoValue: 74-120-155  092970.pub
InfoKey: Author
InfoValue: Cindy
InfoKey: Producer
InfoValue: GPL Ghostscript 8.64
InfoKey: ModDate
InfoValue: D:20100708211330-07'00'
InfoKey: CreationDate
InfoValue: D:20100503094726-05'00'
PdfID0: 56aa2475327b6351a435090fb8a5489
PdfID1: 9e788838d0c37c7723539b8c4afeffdd
NumberOfPages: 1

Converting 1 pages
==========
Extracting page 1
Converting page 1 to ppm
pdftoppm version 3.02
Copyright 1996-2007 Glyph & Cog, LLC
Usage: pdftoppm [options] <PDF-file> <PPM-root>
  -f <int>          : first page to print
  -l <int>          : last page to print
  -r <int>          : resolution, in DPI (default is 150)
  -mono             : generate a monochrome PBM file
  -gray             : generate a grayscale PGM file
  -t1lib <string>   : enable t1lib font rasterizer: yes, no
  -freetype <string>: enable FreeType font rasterizer: yes, no
  -aa <string>      : enable font anti-aliasing: yes, no
  -aaVector <string>: enable vector anti-aliasing: yes, no
  -opw <string>     : owner password (for encrypted files)
  -upw <string>     : user password (for encrypted files)
  -q                : don't print any messages or errors
  -cfg <string>     : configuration file to use in place of .xpdfrc
  -v                : print copyright and version info
  -h                : print usage information
  -help             : print usage information
  --help            : print usage information
  -?                : print usage information
Running OCR on page 1
ImageMagick: Memory allocation failed `' @ dib.c/WriteDIBImage/1066
Cuneiform for Linux 0.9.0
Error while running OCR on page 1
Merging together PDF files
Error: Failed to open PDF file: 
   /tmp/d20100708-8664-k9qzbg/*-new.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Updating PDF info for /home/john/output.pdf
Error: Failed to open PDF file: 
   /tmp/d20100708-8664-k9qzbg/merged.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Cleaning up temporary files


---

### Post by drewsimon on 2010-07-16
Great idea! I'm trying it right now. My first error was when running your script in a directory that contains spaces in the name. Or when running your script on a file that has a space in the filename. 

Your script seems to cut off the directoryname/filename at the space. You can fix your script by escaping spaces in your script.

Thanks! I'm excited to see how my first OCR'ed PDF comes out. :)

---

### Post by Marlonsm on 2010-07-16
Thank you!
I've been looking for something like this for a long time.

I'm installing it right now.

---

### Post by sasa.tomic on 2010-07-24
Thanks!!!
I've been looking for a long time for something like this (as an alternative to FineReader) and it works flawlessly!!!!

---

### Post by trumpeteersman on 2010-08-06
I seem to be having this common issue:
```
Warning: Image x/y resolution not set, defaulting to: 300
```

I am running 64-bit 10.04.
Any way to fix this?

texla was able to fix this, but how?

My ocr'd text is not where it is supposed to be.

---

### Post by Marlonsm on 2010-08-06
> **trumpeteersman said:**
> I seem to be having this common issue:
```
Warning: Image x/y resolution not set, defaulting to: 300
```

I am running 64-bit 10.04.
Any way to fix this?

texla was able to fix this, but how?

My ocr'd text is not where it is supposed to be.

It also happens here, the generated text is much bigger than the original one, so it gets out of place.

---

### Post by joehill on 2010-08-15
I hope I can get this working soon. I was excited when I saw that I could actually select text in an OCRed document, but then I realized it was only detecting something like 15 to 30 words per page. Any ideas on how to get it to see all the text?

---

### Post by clasikowski on 2010-08-18
Hi!

There seem to be problems for hocr2pdf with the hocr files produced by cuneiform in version 0.9.0 or higher. The reocgnition is pretty good, but when adding the hocr file to the pdf sometimes the font size used in the hidden layer is blown way out of proportion, so that the hidden layer doesn't fit the image layout at all, even some parts of the ocr result are not saved at all.

I haven't found out why this happens, it seems that hocr2pdf is not able to work with the new hocr format used in cuneiform 0.9.0 or higher. 

pdfsandwich ( [http://www.tobias-elze.de/pdfsandwich/index.html](http://www.tobias-elze.de/pdfsandwich/index.html) ) could be worth looking at, it works with cuneiform 0.7.0, the standard ubuntu packages, since it first converts the pdf image to bmp3 (the format cuneiform was written for); the resulting hocr files are slightly larger than those produced by cuneiform 0.9.0 or higher. The results match much better!


so long
clasikowski aka hank

---

### Post by snoozy23 on 2010-08-24
Hi, the program doesn't work for me. I'm on Ubuntu 10.4 with actual kernel.

I've tried a large ebook. The quality is ok.

here is the output:

```
Error while running OCR on page 275
==========
Extracting page 276
Converting page 276 to ppm
pdftoppm version 3.02
Copyright 1996-2007 Glyph & Cog, LLC
Usage: pdftoppm [options] <PDF-file> <PPM-root>
  -f <int>          : first page to print
  -l <int>          : last page to print
  -r <int>          : resolution, in DPI (default is 150)
  -mono             : generate a monochrome PBM file
  -gray             : generate a grayscale PGM file
  -t1lib <string>   : enable t1lib font rasterizer: yes, no
  -freetype <string>: enable FreeType font rasterizer: yes, no
  -aa <string>      : enable font anti-aliasing: yes, no
  -aaVector <string>: enable vector anti-aliasing: yes, no
  -opw <string>     : owner password (for encrypted files)
  -upw <string>     : user password (for encrypted files)
  -q                : don't print any messages or errors
  -cfg <string>     : configuration file to use in place of .xpdfrc
  -v                : print copyright and version info
  -h                : print usage information
  -help             : print usage information
  --help            : print usage information
  -?                : print usage information
Running OCR on page 276
Magick: Improper image header `276.ppm' @ pnm.c/ReadPNMImage/297
Cuneiform for Linux 0.9.0
Error while running OCR on page 276
Merging together PDF files
/tmp/d20100824-6962-1fqv3qc/*-new.pdf not found as file or resource.
Error: Failed to open PDF file: 
   /tmp/d20100824-6962-1fqv3qc/*-new.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Updating PDF info for /home/steffen/tmp/morgen.pdf
/tmp/d20100824-6962-1fqv3qc/merged.pdf not found as file or resource.
Error: Failed to open PDF file: 
   /tmp/d20100824-6962-1fqv3qc/merged.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
Cleaning up temporary files

```maybe there is allready a solution. thank you

---

### Post by old robots never rust on 2010-08-25
> **clasikowski said:**
> Hi!

There seem to be problems for hocr2pdf with the hocr files produced by cuneiform in version 0.9.0 or higher. The reocgnition is pretty good, but when adding the hocr file to the pdf sometimes the font size used in the hidden layer is blown way out of proportion, so that the hidden layer doesn't fit the image layout at all, even some parts of the ocr result are not saved at all.

I haven't found out why this happens, it seems that hocr2pdf is not able to work with the new hocr format used in cuneiform 0.9.0 or higher. 

pdfsandwich ( [http://www.tobias-elze.de/pdfsandwich/index.html](http://www.tobias-elze.de/pdfsandwich/index.html) ) could be worth looking at, it works with cuneiform 0.7.0, the standard ubuntu packages, since it first converts the pdf image to bmp3 (the format cuneiform was written for); the resulting hocr files are slightly larger than those produced by cuneiform 0.9.0 or higher. The results match much better!


so long
clasikowski aka hank

Hank, thanks for this suggestion. It is giving me the same mis-matching results that others have had.

I tried the option -noimage and can see that the output has random sized text that often overlap one another, which is why they never line up with the original image. 

Has anyone come up with a solution to this yet?

---

### Post by geodanny on 2010-10-04
Like the others, the text and image layers do not match up. Do you need samples of our files?

btw: thanks for providing this program. Things are better than before.

---

### Post by gourneau on 2010-10-22
> **snoozy23 said:**
> Hi, the program doesn't work for me. I'm on Ubuntu 10.4 with actual kernel.

I modified your solution to work with Ubuntu 9.10 and pdftoppm 3.02 (which looks like what you used too).  The problem I had was that pdftoppm pads the output .ppm with 5 zeros.  Mine will only work for pdfs less than 100 pages.

```

#!/bin/bash

TESS_LANG=eng
rflag=
# first figure out what args we have
getopts 'r:' OPT;
shift $(($OPTIND - 1))
if [ $OPT == "r" ]
then
    rflag="-rotate $OPTARG";
fi

CURRENT_DIR=`pwd`
SCRIPT_NAME=`basename "$0" .sh`
TMP_DIR=${SCRIPT_NAME}-tmp
mkdir ${TMP_DIR}

for thisfile in "$@"
do
    NAME=`basename "${thisfile}" .pdf`
    cp "$thisfile" ${TMP_DIR}
    cd ${TMP_DIR}

    echo "Examining: ${thisfile}";
    pgs=`pdfinfo "${thisfile}" | grep Pages | awk '{print $2}'`
    echo "Found ${pgs} pages; converting...";
    # it's only fair, since we're suppressing it later...
    echo "Tesseract Open Source OCR Engine";
    for x in `seq 1 ${pgs}`
    do
        echo -en "  Page ${x}...";
        pdftoppm -f $x -l $x -r 600 "$thisfile" ocrbook;
		if [ $x -gt 9 ]; then
        		BASE=ocrbook-0000${x};
		else 
        		BASE=ocrbook-00000${x};
		fi 
        convert ${BASE}.ppm ${rflag} ${BASE}.tif;
        tesseract ${BASE}.tif ${BASE} -l ${TESS_LANG} > /dev/null 2>&1;
        cat ${BASE}.txt >> "${NAME}.txt";
        echo "[pagebreak]" >> "${NAME}.txt";
        rm ocrbook*;
        echo "done";
    done;

    echo "Conversion complete";

    mv "${NAME}.txt" ${CURRENT_DIR}
    rm *
    cd ${CURRENT_DIR}
done

rmdir ${TMP_DIR}


```

---

### Post by gourneau on 2010-10-22
wrong thread, sorry for the post. Please delete.

---

### Post by fuzzyworbles on 2010-11-12
this app is really promising, especially because there's nothing out there like it for linux. it would be extremely useful for any organization that images a grip of documents. 

in our office, for example, we image all our files. the fancy expensive feed scanners we have scan into pdf, but aren't OCR'd. 

if this app were accurate, i'd use it to image tens of thousands of pdf's that i otherwise have to rely on effective file names to find what i'm looking for. 

my experience, however, is like the rest: poor recognition and badly misaligned. sure, tesseract is out there, but OCRing to a separate text file isn't very useful in this context.

---

### Post by potrick on 2010-11-30
I'm really wanting to try this out and write it up, but the PPA doesn't work for 10.10. Is there any chance of that happening soon?

---

### Post by nortexoid on 2010-12-03
I just tried installing from the PPA in Maverick 10.10 too, but the dependencies don't allow one to install it. Quite unfortunate. Will there be updated packages soon?

---

### Post by Paqman on 2010-12-11
The dependency problem is because it depends on libmagick++2, while recent versions of Ubuntu only have libmagick++3.

You can get a copy of libmagick++2 from the lucid repos [here]("http://packages.ubuntu.com/lucid/libmagick++2"). Install the .deb then go ahead and install pdfocr as normal.

---

### Post by segamsu on 2010-12-15
I have one problem. After recognizing the created pdf file is so small that it is readable only on 300% zoom, 400% has artefacts already. Is it normal? How can I increase it's size?

---

### Post by ohiknow on 2010-12-19
The script errors out with 
```
"Error: there are 0 pages in the input PDF File."
```

But the output of pdftk dump_data shows "NumberOfPages: 11"

```
InfoKey: Creator
InfoValue: PScript5.dll Version 5.2
InfoKey: Title
InfoValue: PartList_Parts_Explosion_LST2.pdf
InfoKey: Producer
InfoValue: Acrobat Distiller 7.0 (Windows)
InfoKey: Author
InfoValue: jspencer
InfoKey: ModDate
InfoValue: D:20050929120602-05'00'
InfoKey: CreationDate
InfoValue: D:20050929120602-05'00'
PdfID0: 20ac307166dce2f6b8e7982e42c9eae
PdfID1: 2818188aa0687043a69a97e172b78b3a
NumberOfPages: 11
PageLabelNewIndex: 1
PageLabelStart: 1
PageLabelNumStyle: DecimalArabicNumerals
```



I have tried editing the script to correctly define "pagenum", but I have no experience with Ruby.

Any help is appreciated.


Jeremy

---

### Post by fungiblename on 2011-01-09
I tried this script, but did not get great results with English text. 

For those having problems here, you may want to try the solutions in this thread: 

[http://ubuntuforums.org/showthread.php?t=1647350](http://ubuntuforums.org/showthread.php?t=1647350)

The thread provides instructions on how to install Tesseract 3.00--which now produces hOCR output--and I've posted a shell script there that will take an image-type PDF, process it with Tesseract, and then convert it back into a single PDF. 

I can't take credit for the script (acknowledgements included in the script itself), but it seems to work pretty well for me, except for a file size issue that sometimes arises (sometimes it will save about 10-15% over the original file size, sometimes it will double it - still can't figure that out). But it's a shell script, and not too tough to modify to suit your needs/wants.

Alternatively, it may be worth seeing if it's possible to use Tesseract in the script in this thread, but that may be tricky for those of us completely unfamiliar with Ruby, particularly if there's a shell script that offers similar functionality.....

---

### Post by paul@cyberengel.com on 2011-01-10
> **drewsimon said:**
> Great idea! I'm trying it right now. My first error was when running your script in a directory that contains spaces in the name. Or when running your script on a file that has a space in the filename. 

Your script seems to cut off the directoryname/filename at the space. You can fix your script by escaping spaces in your script.

Thanks! I'm excited to see how my first OCR'ed PDF comes out. :)

I see Drewsimon has already noted this back in July.  Not escaping the filenames to handle spaces and other characters really is putting a damper on this tool.  Will you be fixing this?

Otherwise it seems a really useful tool.

---

### Post by fuzzyworbles on 2011-01-15
> **fungiblename said:**
> 

The thread provides instructions on how to install Tesseract 3.00--which now produces hOCR output--and I've posted a shell script there that will take an image-type PDF, process it with Tesseract, and then convert it back into a single PDF. 
....

cool. i'll try the tesseract solution when i've got a chance.

---

### Post by barna on 2011-03-03
Hi guys, there doesn't seem to be a repository for maverick, ubuntu 10.10. Does it exist for maverick in a package format? Can I just get the source and compile it for myself?
Thanks

---

### Post by barna on 2011-03-03
Hi, I have implemented the same thing in /bin/sh (i.e. no need to install ruby). By default, it overlays the recognized text with the original pdf, and not the rasterized image (as in the case of pdfocr), although that can also be enforced with the --ppm option. 

It uses tesseract (one needs version >3.0), which works very nicely, in contrast to cuneiform (which did not recognize practically anything, whatever I tried - I did not try to tweak it, though)

I have a problem: the output looks ok on the screen, it is searchable, etc - but when I print it, the recognized text also appears on the printer. How can this be solved?

...start edit: well, I discovered that I skipped a large part of this (and another, here referenced) thread, and I am not the only one who implemented their own version for this task. What I do differently is that I specify the -n option to hocr2pdf (i.e. do not overlay the raster image over the recognized text), but then do it later with pdftk, overlaying the original pdf page over the recognized text. That should be, I think, better. 

However, all the implementations (including pdfsandwich, which also works quite nicely) have the problem, that the OCR-et document is ok on the screen, in a pdf reader, but when printed, the background text gets also printed. Any idea how to solve this?

... end edit.

```

#!/bin/sh

# Dependencies: pdftoppm, pdftk, tesseract (>3.0), hocr2pdf
# see http://code.google.com/p/tesseract-ocr/wiki/ReadMe how to install tesseract (>3.0)

input=""
output=""
from=1
to=0
verbose=false
useppm=false
resolution=450

help()
{
cat <<EOF

Usage: pdf-ocr <-i input> [options]

  -o <output>         Specify output filename

  -f|--from <number>  Specify starting page

  -t|--to <number>    Specify last page

  -p|--ppm            Use the ppm image instead of the original pdf

  -r <resolution>     Specify resolution (image given to the OCR program)
                      Default is $resolution

  -v|--verbose

EOF
}

while [ $# -gt 0 ] ; do
  case $1 in
    -i) input=$2; shift;;
    -o) output=$2; shift;;
    -f|--from) from=$2; shift;;
    -t|--to) to=$2; shift;;
    -v|--verbose) verbose=true;;
    -r) resolution=$2; shift;;
    -p|--ppm) useppm=true;;
    -h|--help) help; exit;;
    *) echo Unknown argument: $1; exit;;
  esac
  shift
done

if [ "$input" = "" ] ; then
  help
  exit 1
fi

if [ "$output" = "" ] ; then
  output=`echo $input | sed 's/\.[pP][dD][fF]$//g'`
  output="${output}-ocr.pdf"
fi

echo "###  $input -->  $output"

tmp=`mktemp -d`

pdfinfo=${tmp}/pdfinfo.txt
pdftk ${input} dump_data > ${pdfinfo}
pages=`awk '$1=="NumberOfPages:" { print $2 }' ${pdfinfo}`
echo "###  Input file has $pages pages"
if [ $from -lt 1 ] ; then from=1; fi
if [ $to = 0 -o $to -gt $pages ] ; then to=$pages; fi

if [ "$pages" = "" -o "$pages" = 0 ] ; then
  echo "### input file has no pages"
  exit 2
fi

i=1
if [ "$from" -gt $i ] ; then
  i="$from"
fi
if [ "$to" -lt $pages ] ; then
  pages="$to"
fi

pagelist=""
while [ $i -le $pages ] ; do
  echo " >> Processing page $i"
  page_pdf=${tmp}/${i}.pdf
  page_base=`echo $page_pdf | sed 's/\.pdf$//g'`
  page_ppm=${page_base}.ppm
  page_hocr=${page_base}.html
  page_ocr=${page_base}.tmp.pdf
  page_final=${page_base}.ocr.pdf
  echo -n "   Extracting page... "
  pdftk $input cat $i output $page_pdf
  echo "DONE, return status: $?"
  echo -n "   Converting to ppm... "
  pdftoppm -r ${resolution} $page_pdf > $page_ppm
  echo "DONE, return status: $?"
  echo -n "   Running tesseract (OCR)... "
  tesseract_output=`tesseract ${page_ppm} ${page_base} hocr 2>&1`
  tesseract_status=$?
  if [ $verbose = true -o $tesseract_status != 0 ] ; then echo; echo $tesseract_output; fi
  echo "DONE, return status: $tesseract_status"
  if [ $useppm = false ] ; then
    echo -n "   Creating text layer (hocr2pdf)... "
    hocr2pdf -r ${resolution} -n -s -i ${page_ppm} -o ${page_ocr} < ${page_hocr}
    echo "DONE, status: $?"
    echo -n "   Underlaying text below original image (pdftk)... "
    pdftk ${page_pdf} background ${page_ocr} output ${page_final}
    echo "DONE, status: $?"
  else
    echo -n "   Creating page with recognized text (hocr2pdf)... "
    hocr2pdf -r ${resolution}  -s -i ${page_ppm} -o ${page_final} < ${page_hocr}
    echo "DONE, status: $?"
  fi
  pagelist="${pagelist} ${page_final}"
  i=$((i+1))
done

echo Merging pages: pdftk ${pagelist} cat output "${output}"
pdftk ${pagelist} cat output ${tmp}/final.pdf

echo Updating PDF info
pdftk ${tmp}/final.pdf update_info ${pdfinfo} output "${output}"

rm -rf ${tmp}


```

---

### Post by barna on 2011-03-08
It seems that the problem mentioned above (i.e. the recognized pdf, with the text layer behind the original scanned document displays correctly in a reader on screen (text layer is invisible), but both layers appear on the printer) is related to maybe the printing system. At least when printing the same document from Acrobat on MacOS, it was OK. Printing from both acroread and okular on linux produced wrong output.

---

### Post by zeddock on 2011-03-28
I would say this is the closest I have come to a replacement of Adobe Acrobat for Ubuntu or linux in general.

I too have to say placement of the resulting OCRed text is off in its location by quite a bit.

I also see the default of 300dpi which may have something to do with it.

Being so close... and also using PDF Studio for all other replacement of Adobe Acrobat, can't those final fixes, like position of merged text, and an install routine, be created by someone out there?  Please?

I know I would have a hard time getting success again if I had to try and install and use via command line.

Just hoping, certainly not complaining!

This pdfocr works better than anything else on Ubuntu for OCRing like Acrobat does.

zeddock

---

### Post by clasikowski on 2011-05-09
Hi!

It still doesen't work properly; the best solution I found so far for pdf files with searchable text layer is gscan2pdf 0.9.31; using ocropus as engine the recognition is pretty good; the matching between image and text is very accurate. 

I have developed another solution producing djvu-files, see  [http://wiki.ubuntuusers.de/xsane2djvu](http://wiki.ubuntuusers.de/xsane2djvu) , a wrapper for xsane-text recognition; it's german, but the script is anotated, so it should be not too difficult to use...

so long
clasikowski AKA hank

---

### Post by bonfire89 on 2011-06-16
Honestly, this failed miserable, but I wish it didn't. I'm on 11.04 64-bit and here is the output I received while running the script

```

dave@dave:~/Public$ pdfocr -i chapter1.pdf -o ocrChapter1.pdf
Input file is /home/dave/Public/chapter1.pdf
Output file is /home/dave/Public/ocrChapter1.pdf
Using working dir /tmp/d20110616-18134-1fnw6dx
Getting info from PDF file

InfoKey: Creator
InfoValue: PScript5.dll Version 5.2.2
InfoKey: Title
InfoValue: C:\Documents and Settings\dave\Desktop\FP00001.SPL
InfoKey: Author
InfoValue: me
InfoKey: Producer
InfoValue: GPL Ghostscript 8.15
InfoKey: ModDate
InfoValue: D:20110512182529
InfoKey: CreationDate
InfoValue: D:20110512182529
PdfID0: 1e3052408a834d039f6d4a01a63f4d7
PdfID1: 1e3052408a834d039f6d4a01a63f4d7
NumberOfPages: 43

Converting 43 pages
==========
Extracting page 1
Converting page 1 to ppm
Running OCR on page 1
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 1
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 2
Converting page 2 to ppm
Running OCR on page 2
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 2
Warning: Image x/y resolution not set, defaulting to: 300
Warning: tag mismatch: 'b' can not close last open: 'i'
Warning: tag mismatch: 'span' can not close last open: 'b'
Warning: tag mismatch: 'p' can not close last open: 'b'
Warning: tag mismatch: 'i' can not close last open: 'b'
Warning: tag mismatch: 'span' can not close last open: 'i'
Warning: tag mismatch: 'p' can not close last open: 'i'
Warning: tag mismatch: 'i' can not close last open: 'b'
Warning: tag mismatch: 'span' can not close last open: 'i'
Warning: tag mismatch: 'p' can not close last open: 'i'
Warning: tag mismatch: 'b' can not close last open: 'i'
Warning: tag mismatch: 'span' can not close last open: 'b'
Warning: tag mismatch: 'b' can not close last open: 'i'
Warning: tag mismatch: 'span' can not close last open: 'b'
Warning: tag mismatch: 'p' can not close last open: 'b'
Warning: tag mismatch: 'div' can not close last open: 'b'
Warning: tag mismatch: 'body' can not close last open: 'b'
Warning: tag mismatch: 'html' can not close last open: 'b'
Warning: unclosed tag: 'b'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'b'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'i'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'i'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'b'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'div'
Warning: unclosed tag: 'body'
Warning: unclosed tag: 'html'
==========
Extracting page 3
Converting page 3 to ppm
Running OCR on page 3
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 3
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 4
Converting page 4 to ppm
Running OCR on page 4
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 4
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 5
Converting page 5 to ppm
Running OCR on page 5
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 5
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 6
Converting page 6 to ppm
Running OCR on page 6
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 6
Warning: Image x/y resolution not set, defaulting to: 300
Warning: tag mismatch: 'i' can not close last open: 'b'
Warning: tag mismatch: 'i' can not close last open: 'b'
Warning: tag mismatch: 'span' can not close last open: 'i'
Warning: tag mismatch: 'p' can not close last open: 'i'
Warning: tag mismatch: 'b' can not close last open: 'i'
Warning: tag mismatch: 'span' can not close last open: 'b'
Warning: tag mismatch: 'p' can not close last open: 'b'
Warning: tag mismatch: 'b' can not close last open: 'i'
Warning: tag mismatch: 'span' can not close last open: 'b'
Warning: tag mismatch: 'p' can not close last open: 'b'
Warning: tag mismatch: 'i' can not close last open: 'b'
Warning: tag mismatch: 'span' can not close last open: 'i'
Warning: tag mismatch: 'p' can not close last open: 'i'
Warning: tag mismatch: 'i' can not close last open: 'b'
Warning: tag mismatch: 'span' can not close last open: 'i'
Warning: tag mismatch: 'p' can not close last open: 'i'
Warning: tag mismatch: 'div' can not close last open: 'i'
Warning: tag mismatch: 'body' can not close last open: 'i'
Warning: tag mismatch: 'html' can not close last open: 'i'
Warning: unclosed tag: 'i'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'i'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'b'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'b'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'i'
Warning: unclosed tag: 'i'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'div'
Warning: unclosed tag: 'body'
Warning: unclosed tag: 'html'
==========
Extracting page 7
Converting page 7 to ppm
Running OCR on page 7
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 7
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 8
Converting page 8 to ppm
Running OCR on page 8
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 8
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 9
Converting page 9 to ppm
Running OCR on page 9
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 9
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 10
Converting page 10 to ppm
Running OCR on page 10
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 10
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 11
Converting page 11 to ppm
Running OCR on page 11
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 11
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 12
Converting page 12 to ppm
Running OCR on page 12
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 12
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 13
Converting page 13 to ppm
Running OCR on page 13
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 13
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 14
Converting page 14 to ppm
Running OCR on page 14
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 14
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 15
Converting page 15 to ppm
Running OCR on page 15
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 15
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 16
Converting page 16 to ppm
Running OCR on page 16
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 16
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 17
Converting page 17 to ppm
Running OCR on page 17
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 17
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 18
Converting page 18 to ppm
Running OCR on page 18
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 18
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 19
Converting page 19 to ppm
Running OCR on page 19
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 19
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 20
Converting page 20 to ppm
Running OCR on page 20
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 20
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 21
Converting page 21 to ppm
Running OCR on page 21
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 21
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 22
Converting page 22 to ppm
Running OCR on page 22
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 22
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 23
Converting page 23 to ppm
Running OCR on page 23
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 23
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 24
Converting page 24 to ppm
Running OCR on page 24
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 24
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 25
Converting page 25 to ppm
Running OCR on page 25
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 25
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 26
Converting page 26 to ppm
Running OCR on page 26
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 26
Warning: Image x/y resolution not set, defaulting to: 300
Warning: tag mismatch: 'i' can not close last open: 'b'
Warning: tag mismatch: 'b' can not close last open: 'i'
Warning: tag mismatch: 'span' can not close last open: 'b'
Warning: tag mismatch: 'p' can not close last open: 'b'
Warning: tag mismatch: 'div' can not close last open: 'b'
Warning: tag mismatch: 'body' can not close last open: 'b'
Warning: tag mismatch: 'html' can not close last open: 'b'
Warning: unclosed tag: 'b'
Warning: unclosed tag: 'i'
Warning: unclosed tag: 'span'
Warning: unclosed tag: 'p'
Warning: unclosed tag: 'div'
Warning: unclosed tag: 'body'
Warning: unclosed tag: 'html'
==========
Extracting page 27
Converting page 27 to ppm
Running OCR on page 27
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 27
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 28
Converting page 28 to ppm
Running OCR on page 28
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 28
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 29
Converting page 29 to ppm
Running OCR on page 29
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 29
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 30
Converting page 30 to ppm
Running OCR on page 30
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 30
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 31
Converting page 31 to ppm
Running OCR on page 31
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 31
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 32
Converting page 32 to ppm
Running OCR on page 32
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 32
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 33
Converting page 33 to ppm
Running OCR on page 33
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 33
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 34
Converting page 34 to ppm
Running OCR on page 34
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 34
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 35
Converting page 35 to ppm
Running OCR on page 35
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 35
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 36
Converting page 36 to ppm
Running OCR on page 36
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 36
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 37
Converting page 37 to ppm
Running OCR on page 37
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 37
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 38
Converting page 38 to ppm
Running OCR on page 38
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 38
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 39
Converting page 39 to ppm
Running OCR on page 39
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 39
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 40
Converting page 40 to ppm
Running OCR on page 40
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 40
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 41
Converting page 41 to ppm
Running OCR on page 41
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 41
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 42
Converting page 42 to ppm
Running OCR on page 42
Cuneiform for Linux 1.0.0
Embedding text into PDF for page 42
Warning: Image x/y resolution not set, defaulting to: 300
==========
Extracting page 43
Converting page 43 to ppm
Running OCR on page 43
Cuneiform for Linux 1.0.0
PUMA_XFinalrecognition failed.
Error while running OCR on page 43
Merging together PDF files
Updating PDF info for /home/dave/Public/ocrChapter1.pdf
Cleaning up temporary files
/usr/bin/pdfocr:287:in `delete': Is a directory - /tmp/d20110616-18134-1fnw6dx/20_files (Errno::EISDIR)
	from /usr/bin/pdfocr:287
	from /usr/bin/pdfocr:283:in `foreach'
	from /usr/bin/pdfocr:283

```

---

### Post by mejoe2 on 2012-06-03
It seems the script is not handling spaces in both the file and path to the file. Are you still supporting updates?  Is there anyway one could access your repo to fix this bug?

---

### Post by bovender on 2012-06-03
The new version PDF Xchange Viewer can OCR scanned pages very well. Its not a native Linux app and it's proprietary, but runs very well under Wine and has multiple language support.

---

### Post by barna on 2012-06-04
If command line tools are not an absolute must for you, give a try to PDF Xchange Viewer ([http://www.tracker-software.com/product/pdf-xchange-viewer](http://www.tracker-software.com/product/pdf-xchange-viewer)). It is a windows program, but runs flawlessly under wine, it has OCR and a whole lot of other features. It has a free and a pro version - I decided to pay for the pro version which is offering more tools.

---

### Post by tarverator on 2012-07-13
> **the_summer said:**
> Its a great helper. I tried it on some files. The ocr seem to work, but when i search for words, the marks are often quite far away from the searched word.
Maybe it's because there is always the warning:

```
Warning: Image x/y resolution not set, defaulting to: 300

```

Is there a way to manually set different values for the resolution.
I didnt find something about it in the man-page.

Best wishes

 Jan

At least part of the problem here is that pdftoppm and hocr2pdf (used by pdfocr) default to low resolutions, like 150. If the input file has higher resolution, nothing lines up. Here is how to hard-code a 600dpi resolution in /usr/bin/pdfocr:

```

1.upto(pagenum) { |i|
	puts "=========="
	puts "Extracting page #{i}"
	basefn = i.to_s.rjust(numdigits, '0')
	sh "pdftk #{infile} cat #{i} output #{basefn+'.pdf'}"
	if not File.file?(basefn+'.pdf')
		puts "Error while extracting page #{i}"
		next
	end
	puts "Converting page #{i} to ppm"
	sh "pdftoppm -r 600 #{basefn+'.pdf'} > #{basefn+'.ppm'}"
	if not File.file?(basefn+'.ppm')
		puts "Error while converting page #{i} to ppm"
		next
	end
	puts "Running OCR on page #{i}"
	sh "cuneiform -l #{language} -f hocr -o #{basefn+'.hocr'} #{basefn+'.ppm'}"
	if not File.file?(basefn+'.hocr')
		puts "Error while running OCR on page #{i}"
		next
	end
	puts "Embedding text into PDF for page #{i}"
	sh "hocr2pdf -r 600 -i #{basefn+'.ppm'} -s -o #{basefn+'-new.pdf'} < #{basefn+'.hocr'}"
	if not File.file?(basefn+'-new.pdf')
		puts "Error while embedding text into PDF for page #{i}"
		next
	end
}

```

Add "-r 600" (coincidentally the same parameter) in two places, to the pdftoppm and hocr2pdf sections of the above block of code (assuming 600dpi input), as shown.

This gives significantly better results.

---

### Post by SkekTek on 2013-02-19
I have found that Tesseract (3.02) is more accurate than Cuneiform (1.1.0).

Tesseract is much slower though; ~10-15 seconds a page on a Core i5.


To use Tesseract instead of Cuneiform change

```
sh "cuneiform -l #{language} -f hocr -o #{basefn+'.hocr'} #{basefn+'.ppm'}"
```to

```
sh "tesseract #{basefn+'.ppm'} #{basefn+'.hocr'} -l #{language} hocr"
```and

```
sh "hocr2pdf -i #{basefn+'.ppm'} -s -o #{basefn+'-new.pdf'} < #{basefn+'.hocr'}"
```to

```
sh "hocr2pdf -i #{basefn+'.ppm'} -s -o #{basefn+'-new.pdf'} < #{basefn+'.hocr.html'}"
```YMMV but this also cleared up some formatting errors and inconsistencies I was getting with Cuneiform's hOCR.

---

### Post by kagashe on 2013-03-28
I tried both pdfocr (which uses cuneiform) and tesseract on scanned pdf files and could not make them work.

Then I installed [Lios]("http://code.google.com/p/linux-intelligent-ocr-solution/") (in which you can choose cuneiform or tesseract in preferences) which has GUI. By using OCR-Pdf from Menu I tried the same file and got good results with both the engines.

[Lios thread]("http://ubuntuforums.org/showthread.php?t=1903221") is also present on this forum.

Kamalakar

---

