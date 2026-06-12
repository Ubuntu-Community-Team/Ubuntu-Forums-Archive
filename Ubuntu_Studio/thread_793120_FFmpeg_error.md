---
title: "FFmpeg error"
date: 2008-05-13
forum: Ubuntu Studio
---

### Post by ryn0 on 2008-05-13
Hi people.
Have been trying to convert some pictures into a mp4 file. This is what i get:

nizze@nizze:~/Skrivbord/images$ ffmpeg -f image2 -i img%d.jpg /tmp/a.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
img%d.jpg: I/O error occured
Usually that means that input file is truncated and/or corrupted.
nizze@nizze:~/Skrivbord/images$

I/O error? I mean, that is the official FAQ way of making things...

---

### Post by FakeOutdoorsman on 2008-05-14
Are your images in a sequence?  You can use gprename or a similar program to rename your files.  The easiest way for ffmpeg is to just use numbers and then use the appropriate "%d":
> 00n.jpg = %03d.jpg
000n.jpg = %04d.jpg
Here's a quick script that will rename all images into a sequence like 0001.jpg.  I'm not 100% sure it will do it in proper order, so backup first.  It will also not work on files with spaces in the file name and some other characters:
```
ls *.jpg | nl -nrz -w4 | while read a b; do mv "$b" $a.jpg; done
```
Also make sure there are no missing images from the sequence.  For example, if 0018.jpg is missing, then it will stop encoding at that missing frame.

You can control the frame rate (-r) and bitrate (-b) easily.  -f image2 might be unneeded.  You also don't need to dump your final movie to /tmp:
```
ffmpeg -r 15 -b 800k -i %04d.jpg a.mpg
```

---

### Post by ryn0 on 2008-05-15
Thanks for the help mate :D

---

### Post by hydrox24 on 2011-11-12
Thanks for this, really helped me in making a time-lapse movie.

---

