---
title: "REQUEST: Backport libungif packages from Feisty?"
date: 2007-01-24
forum: Ubuntu Backports
---

### Post by Motley Fool on 2007-01-24
Hi!  Even though I just LOVE MAKING MONEY WITH STOCKS! I've decided to use FuzzyOCR in conjunction with SpamAssassin to deal with the image-spam I'm getting.

Libungif (i.e. the packages libungif4g, libungif4-dev, libungif-bin) are used by FuzzyOCR.  There is a bug in the colormap-lookup function of Dapper's libungif packages (4.1.4-1) that can result in a segfault.  Fortunately, the solution is a one-line fix.  That fix (along with others) now exists in the 3 libungif-related packages in Feisty (4.1.4-4).

So, could libungif4g, libungif4-dev and libungif-bin 4.1.4-4 be backported to Dapper?  If not the whole package, how about the one-line fix?

Here's the Debian bug report for this issue: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=384773]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=384773")

And here's the one-line fix: [http://bugs.debian.org/cgi-bin/bugreport.cgi/giftext-segfault.patch?bug=384773;msg=5;att=1]("http://bugs.debian.org/cgi-bin/bugreport.cgi/giftext-segfault.patch?bug=384773;msg=5;att=1")


```
[FONT="Courier New"]*** giftext.c.orig	2006-08-21 15:41:47.000000000 -0400
--- giftext.c	2006-08-21 15:41:55.000000000 -0400
***************
*** 135,141 ****
  	       GifFileName, GifFile->SWidth, GifFile->SHeight);
  	printf("\tColorResolution = %d, BitsPerPixel = %d, BackGround = %d.\n",
  	       GifFile->SColorResolution,
! 	       GifFile->SColorMap->BitsPerPixel,
  	       GifFile->SBackGroundColor);
  	if (GifFile->SColorMap)
  	    printf("\tHas Global Color Map.\n\n");
--- 135,141 ----
  	       GifFileName, GifFile->SWidth, GifFile->SHeight);
  	printf("\tColorResolution = %d, BitsPerPixel = %d, BackGround = %d.\n",
  	       GifFile->SColorResolution,
! 	       GifFile->SColorMap?GifFile->SColorMap->BitsPerPixel:0,
  	       GifFile->SBackGroundColor);
  	if (GifFile->SColorMap)
  	    printf("\tHas Global Color Map.\n\n");[/FONT]
```
Thanks!

---

