---
title: "Problem with Stopmotion"
date: 2009-02-14
forum: Ubuntu Studio
---

### Post by Achernaries on 2009-02-14
Hi

I've installed Ubuntustudio 8.10 and I get the following errors when I try to export video from Stopmotion.

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
/home/richard/.stopmotion/packer/test/images/%06d.jpg: I/O error occured
Usually that means that input file is truncated and/or corrupted.

Any ideas what this could be?  The picture files load into Stopmotion okay and I am able to play the video in Stopmotion and save and reload the STO file.

Thanks

---

### Post by djbushido on 2009-02-14
Okay, are the pictures numbered sequentially?
if so, try this:
```
ffmpeg -r 20 -sameq -i %05d.png -s 1024x768 render.mp4
```
Some explanation - the "r" option is the frame rate. the -sameq specifies that the input files should be copied as is. the -s is the size of the output file. the "render.mp4" is the output filename. 
Now the fun part. The "%05d.png" specifies that it should use all files of type png that have five numbers in the name. So if it was 006.png, the line would actually be %03.png.
Um, you might also be able to use *.png.
Also also, the png can be changed to jpg, whatever.
Post back any problems.

On another note, look at installing avidemux.

---

### Post by Achernaries on 2009-02-16
Hi djbushido

I tried your suggestion and got the following:

richard@ubuntu:~/Pictures$ ffmpeg -r 20 -sameq -i *.JPG -s 1024x768 render.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
Input #0, image2, from '02984.JPG':
  Duration: 00:00:00.0, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 2592x1944 [PAR 0:1 DAR 0:1], 20.00 tb(r)
Unable to find a suitable output format for '02985.JPG'

Then I tried %50d.JPG and got the folllowing:

richard@ubuntu:~/Pictures$ ffmpeg -r 20 -sameq -i %05d.JPG -s 1024x768 render.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
%05d.JPG: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by djbushido on 2009-02-16
okay, this might sound annoying but will likely help. Try and build your own version of ffmpeg, as the repo one has nearly nothing "good" enabled. Or, you can just try a medibuntu one. See if that helps.

---

### Post by oooh on 2010-02-06
Hi all

I had the same problem when exporting:

"I/O error occurred
Usually that means that input file is truncated and/or corrupted."

Then I configured the ffmpeg script line in Stopmotion preferences, and changed the jpg to JPG. The case was screwing the script.

Now it flows fine :)

Hope it helps !

---

### Post by gnarly_buttons on 2010-06-17
I think the jpg to JPG is the key for me.  Thank you for mentioning it.

---

