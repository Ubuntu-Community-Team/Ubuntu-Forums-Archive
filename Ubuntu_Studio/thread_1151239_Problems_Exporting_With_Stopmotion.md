---
title: "Problems Exporting With Stopmotion"
date: 2009-05-06
forum: Ubuntu Studio
---

### Post by higashi on 2009-05-06
I've been having a LOT of bad luck when it comes to animation. Especially the exporting part...

I decided i want to try stopmotion animation, so i installed the stopmotion program.

When previewing my animation, it seems a little too zoomed in and seems to move a little too slow (it stays at pretty much the same speed even after i change the FPS) but i figured that it would look better once i export it and watch it on movie player.

Unfortunately, once i try exporting it, it only allows me to save it as .sto (yes, i did make sure to press export and not save as). 

How can i export it to a video format? Also, is there a way to make my previewed animation look better?

PS: are there any other (better) programs i can use for making stopmotion animations? (that preferably handle sound...)

---

### Post by kayosiii on 2009-05-07
from memory an STO is a tar.gz or similar file that contains a folder full of images...
you can decompress it and put the images in as a sequence to any video editor that supports that function. (I use Cinelerra)

Just checked and to confirm - an STO is really a Tar file (no compression). Dolphin (KDE filemanager) seems to open it seamlessly. If your filemanager doesn't do that for you rename your file.sto to file.tar :) (and back again if you want to use it with stopmotion)

---

### Post by higashi on 2009-05-09
but i don't WANT a sequence of images. Thats what i started off with. I thought that stopmotion was so that i can put a sequence of images together and make them into a video... Whats the point if i put in a sequence of images and get stuck with the same sequence? O.o

I'm not sure i understand... what exactly is stopmotion for?

---

### Post by emergingtechnologies on 2009-06-15
Higashi,

While I am having the same problem with trying to turn my .sto into a .mpg, I can answer one of your questions:

Yuo write about your images "it seems a little too zoomed in" -- this is a simple problem of file resolution.  Stopmotion does not account for the resolution of the images you bring in.  It will simply try to animate them.  Which is probably good but it doesn't allow us to see what is going on.  To solve this problem I used GIMP to reduce my images.  My original images were way to big and I reduced them all to 25% of what they had been and the animation worked great.

MY PROBLEM: 

This is the error I received when I tried to turn what I have into an .mpg:

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
/home/madoc/.stopmotion/packer/firefighteranimation1/images/%06d.jpg: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

I truly hope some knowledgeable person will be able to shed some light.

Thanks,
Chris

---

### Post by kayosiii on 2009-06-17
My version of Stopmotion has two export options file->export.
There is video export and a cinelerra export. From memory the video export function is not that good. Which is why I still reccomend loading the images as a sequence into a video editor and doing your final encode from there. Off the top of my head I know that LiVES, Blender and cinelerra all support loading image sequences. I haven't tried the direct cinelerra export from stopmotion.

---

