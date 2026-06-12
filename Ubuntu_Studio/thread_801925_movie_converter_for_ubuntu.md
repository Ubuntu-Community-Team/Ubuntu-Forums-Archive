---
title: "movie converter for ubuntu"
date: 2008-05-21
forum: Ubuntu Studio
---

### Post by DaF101 on 2008-05-21
Hello everyone
Just wondering if there is a media converter or mover converter for Ubuntu. If anyone one knows and where I can download it from it will be much appreciated :)
:popcorn:

---

### Post by lisati on 2008-05-21
A discussion can be found ar [http://www.linuxquestions.org/questions/linux-software-2/linux-video-converter-314501/]("http://www.linuxquestions.org/questions/linux-software-2/linux-video-converter-314501/")

---

### Post by aeiah on 2008-05-21
to convert fom dvd to avi i use acidrip

for avi to dvd i use a script i made based on ffmpeg commands

for general conversion i use mencoder and ffmpeg, which are both command line. winff is a gui for ffmpeg which you may like:

[http://www.winff.org/](http://www.winff.org/)

---

### Post by aeiah on 2008-05-21
by the way, have you installed the video and audio codecs yet? because what you cant read, you cant convert. you'll still need the codecs you asked about in your previous post

---

### Post by Creative2 on 2008-05-22
fuoco tools [http://ubuntuforums.org/showthread.php?t=776412](http://ubuntuforums.org/showthread.php?t=776412)
winff
media movie converter
pytube
mm others kdenlive 
blender ;D
mm

---

### Post by prabath_fun on 2010-07-27
Hi,
   I am getting following as message when I start encode with Winff.. Kindly help me solve this...



FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1
Input #0, mpeg, from '/host/Movies/Thiruvanamalai/VIDEO_TS/VTS_03_1.VOB':
  Duration: 00:35:24.03, start: 0.316978, bitrate: 4044 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 8000 kb/s, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 0 channels, s16
Unknown encoder 'libx264'

---

### Post by prabath_fun on 2010-08-07
Finally,
   I got very good video converter "Avidemux". I used the same and converted some videos which are mp4 and DVD files to avi files and played in DVD player without any problem..
  Thousands+++++++  thanks to developers......

---

### Post by LuridCinema on 2010-08-07
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

The ABOVE Will give you everything you need for ffmpeg  . Your errors you posted earlier showed you did not have x.264 installed. Follow the instructions on the link above and you will be on your way. I encode to MP4 using the below:

```
ffmpeg -i INPUT.mov -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -wpredp 0 -s 1280x720 -crf 24 -threads 0 OUTPUT.mp4
```just change the file type for the input if using another format

---

### Post by dirtrider1 on 2011-05-06
For converting AVI to DVD I use ManDVD or Devede both of these program's are specifically designed for this purpose and are very easy to use. For converting DVD to AVI there are a number of programs that can do this including Acidrip,Handbrake,Dvdrip and many other's. Not to mention there are Command line option's as well that are more complex but offer more feature's like Ffmpeg and Mencoder.

---

### Post by JohnAStebbins on 2011-05-06
> **dirtrider1 said:**
> For converting AVI to DVD I use ManDVD or Devede both of these program's are specifically designed for this purpose and are very easy to use. For converting DVD to AVI there are a number of programs that can do this including Acidrip,Handbrake,Dvdrip and many other's. Not to mention there are Command line option's as well that are more complex but offer more feature's like Ffmpeg and Mencoder.
HandBrake does not do AVI output.  It supports mp4 and mkv only.

---

