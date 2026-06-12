---
title: "A WORKABLE DVD burning program - does it exist?"
date: 2009-08-03
forum: Ubuntu Studio
---

### Post by dkolars on 2009-08-03
Attempting my 1st attempt at burning a DVD from files on my hard drive:  .avi from my digital camera, .wmv from another DVD, .flv from YouTube.

I've tried Brasero, GnoneBaker, & K3B -- none of them will burn a DVD... I get error messages of all kinds, way too many to remember... If needed, I could cut and paste all of them...  and they span the gamet from "File not found" to "Unable to open directory xxx", etc.  :confused:

Suffice it to say, that after Windows, I'm really surprised at the lack  :(  of decent programs for DVD buring in Linux...  This is one area where the developers would do good to take note of what the Windows people are doing, as there are a plethora of wonderful programs for that platform...

Will be re-booting back into Win XP to burn my DVD's and CD's -- altho' I havn't tried CD's in Ubuntu yet, but reading the newsgroups and forums,  :frown: I think I'll just do it in Windows!!

---

### Post by SuperSonic4 on 2009-08-03
DeVeDe for creating an ISO or CUE file from video files like avis

K3b for burning ISO or CUE images made by DeVeDe

---

### Post by wsonar on 2009-08-03
I use k3b for burning DVD data DVD's all the time never a problem

Are you trying to make a DVD video DVD?

---

### Post by juancarlospaco on 2009-08-03
K3B or Brasero 
*or layer 8*

---

### Post by wojox on 2009-08-03
Never a problem with Brasero. Picking the right project correct.

---

### Post by dkolars on 2009-08-03
Yes, I'm trying to make a Video DVD... would like one with titles on opening screen, my choice of background, etc.

I put 8 files into K3b... 7 .avi (6 from my camera, 1 from YouTube), and 1 .mp4 (from You Tube).  The initial screen that comes up has both the AUDIO_TS & VIDEO_TS directories shown, but no indication as to where they are, or what is to be done with them... I tried putting my files in the same dir. as them and also inside the VIDEO_TS subdir...  same results!

Here's what I get from K3b:

The error message that is flashed up on the screen says:

* The project does not contain all necessary DVD files
* The resulting DVD will most likely not be playable on a HiFi DVD
X Cannot determine size of resulting image file

Debugging output:

System
-----------------------
K3b Version: 1.0.5
KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-14-generic
Devices
-----------------------
TSSTcorp CDRWDVD TS-H493B D200 (/dev/sr0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R]

HL-DT-ST DVD+-RW GSA-H73N B103 (/dev/sr1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]
SONY DVD RW DRU-510A 1.0d (/dev/sr2, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite]
K3bIsoImager
-----------------------
mkisofs print size result: 0 (0 bytes)

Used versions
-----------------------
mkisofs: 1.1.9

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-dkolars/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
/usr/bin/genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-dkolars/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid MVI_0002 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-dkolars/k3bOwxK1b.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-dkolars/k3bHoLLna.tmp -dvd-video -f /tmp/kde-dkolars/k3bVideoDvd0 

===================

As to Brasero... phooey...  I put the 8 files into it, and after 20 minutes of the lil' clock spinning as it tried to determine the size of the image file, I closed it.  Strange, since it told me that the duration of the DVD was going to be 40:18...  again, I say, phooey...

Next try, DeVeDe...  after supper... must keep strength up... must fight computer to the death (again)...

---

### Post by dkolars on 2009-08-03
> **SuperSonic4 said:**
> DeVeDe for creating an ISO or CUE file from video files like avis

K3b for burning ISO or CUE images made by DeVeDe
==========================

Are you saying that I need to create the ISO file with one program and then create the DVD with another?  NOT an option...  ](*,)  I'm waaay too busy for that kind of set-up...

---

### Post by Grishka on 2009-08-03
try [2ManDVD](http://2mandvd.tuxfamily.org/).

---

### Post by dkolars on 2009-08-03
> **Grishka said:**
> try [2ManDVD]("http://2mandvd.tuxfamily.org/").

Nope, won't install:  "broken pipe."  Tried both i386 versions...  Thanks for the link.
dk  [www.davekolars.com](www.davekolars.com)

---

### Post by Stochastic on 2009-08-04
> **dkolars said:**
> ==========================

Are you saying that I need to create the ISO file with one program and then create the DVD with another?  NOT an option...  ](*,)  I'm waaay too busy for that kind of set-up...


That sounds pretty petty.

DeVeDe is the method that consistently turns out great Video DVD ISOs for me.  I then burn them with GnomeBaker.

Unix and the derivative operating systems have all been built on the idea of multiple programs that each do one task really well.  If you're too busy to integrate these programs as you see fit, maybe a *nix system isn't right for you.  (just a thought)

---

### Post by kayosiii on 2009-08-04
K3B will create working video DVD but will not magically do the format conversion on your video files for you. You will need to have the VOB,IFO etc files needed that will go directly onto the disk. DeVeDe or QDVDAuthor can be used to generate files that will work. They may or may not however be able to read your source files... in which case you will need to do another conversion.

original file -> (possible conversion) -> DVD Image -> K3B

---

### Post by dkolars on 2009-08-04
> **Stochastic said:**
> That sounds pretty petty.

DeVeDe is the method that consistently turns out great Video DVD ISOs for me.  I then burn them with GnomeBaker.

Unix and the derivative operating systems have all been built on the idea of multiple programs that each do one task really well.  If you're too busy to integrate these programs as you see fit, maybe a *nix system isn't right for you.  (just a thought)

 You could very well be right... I did the DeVeDe/K3b last night... 29 minutes to burn the ISO file for 40 min of video... then I started K3b and don't know how long it took as I went to bed...  I'm a retired IT guy (NT 4.0 - 37 computers on 3 different networks)... Now I make spinning/weaving supplies, ukuleles, guitars, repair instruments, and play in 4 groups, on the road 3-4 weekends a month... also working on a book... So, I don't need to be sitting at the 'puter piecing things together... I need to be able to start it and then go be at the lathe or the like...  So, I'm thinking that Windows is still the way to go for DVD's..  I love Ubuntu for everything else, however...  Set up my system with a dual boot when I installed Ubuntu, so I have the easy option.  Thanks... dk   [www.davekolars.com](www.davekolars.com)

---

### Post by alphacrucis2 on 2009-08-04
> **dkolars said:**
> You could very well be right... I did the DeVeDe/K3b last night... 29 minutes to burn the ISO file for 40 min of video... then I started K3b and don't know how long it took as I went to bed...  I'm a retired IT guy (NT 4.0 - 37 computers on 3 different networks)... Now I make spinning/weaving supplies, ukuleles, guitars, repair instruments, and play in 4 groups, on the road 3-4 weekends a month... also working on a book... So, I don't need to be sitting at the 'puter piecing things together... I need to be able to start it and then go be at the lathe or the like...  So, I'm thinking that Windows is still the way to go for DVD's..  I love Ubuntu for everything else, however...  Set up my system with a dual boot when I installed Ubuntu, so I have the easy option.  Thanks... dk   [www.davekolars.com](www.davekolars.com)

I use qdvdauthor to create the DVD menus and import and convert the video clips into VOBs. At that point I use K3b to burn those files output from qdvdauthor as a DVD video project. On my laptop it takes about twelve minutes for K3b to burn a 4GB DVD. The authoring step is about the same once I have set up the menus. The extra step is actually quite useful because you can open up a player such as VLC and open the qdvdauthor output folder as though it were a disk and check that the DVD menus are working correctly before you burn a dud. There's nothing more annoying than burning a DVD +/-R and finding that you screwed up the menus or something when you play it in your DVD player.

---

### Post by wkulecz on 2009-08-05
> The extra step is actually quite useful because you can open up a player such as VLC and open the qdvdauthor output folder as though it were a disk and check that the DVD menus are working correctly before you burn a dud. There's nothing more annoying than burning a DVD +/-R and finding that you screwed up the menus or something when you play it in your DVD player.

If only it were that simple.  I still run into issues where the menu stuff is fine on one DVD player and not another.  Playback on the computer is in general much more forgiving than random DVD player firmware :(

--wally.

---

