---
title: "Are there any video sharing websites that can take a .ogv file?"
date: 2009-03-10
forum: Ubuntu Studio
---

### Post by dweebazoid on 2009-03-10
Or do I have to convert to avi/flv?

I'm doing a few screencasts using recordmydesktop and have a very sharp recording in .ogv format.  When I run ffmpef -i myfile.ogv myfile.avi, the result is a massive loss in quality.  

So I'd much rather serve a straight .ogv file.

I guess I could just upload the file to my server and let people view it in firefox but this requires me to host gigabytes worth of stuff but since I'm using Heroku.com, I don't get all that much space.  

I'm looking to put my files on a video sharing site.  Does anyone know of any that let you upload .ogv?  

Failing that, which format is the best to convert my .ogv into in terms of quality retention?  

Is there a better utility that ffmpeg?  

Does anyone do screencasts and serve straight .ogv files or do you all convert first?

.ogv does run well in firefox although I'm not sure if there are any dependencies.  would anyone have any advice?

---

### Post by andrew.46 on 2009-03-11
Hi dweebazoid,

> **dweebazoid said:**
> I'm doing a few screencasts using recordmydesktop and have a very sharp recording in .ogv format.  When I run ffmpef -i myfile.ogv myfile.avi, the result is a massive loss in quality.

The FFmpeg defaults are obviously not being kind to you :-). Can you run:

```
ffmpeg -i myfile.ogv
```

and then post the command and full terminal output in a message here? This will show information about your version of FFmpeg and the exact contents of your .ogv file. 

> Is there a better utility that ffmpeg?  

No :-). But you will have to do a little research and decide exactly what format you wish to convert your files to. I'm afraid I don't know a lot about video sharing websites but I am sure others can guide you with this.

All the best,

Andrew

---

### Post by dweebazoid on 2009-03-11
Hi there,

thanks for your reply,

here's the output from ffmpeg -i out.ogv

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
[theora @ 0xb7e7f2f0]Theora bitstream version 30201
[theora @ 0xb7e7f2f0]560 bits left in packet 81
[theora @ 0xb7e7f2f0]7 bits left in packet 82
Input #0, ogg, from 'out.ogv':
  Duration: 00:16:20.5, start: 0.000000, bitrate: 952 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1024x768 [PAR 1:1 DAR 4:3], 15.00 tb(r)
    Stream #0.2: Audio: vorbis, 48000 Hz, stereo, 499 kb/s
Must supply at least one output file

________________________________________________

interestingly there is the line:

   Stream #0.0: Invalid Codec type -1

I'll look into that one

Steve

---

### Post by andrew.46 on 2009-03-11
Hi dweebazoid,

> **dweebazoid said:**
> ```
   Stream #0.0: Invalid Codec type -1
``` 

I bumped into that one a while ago. It is an extra stream in an ogv file that is designed to carry so-called 'skeleton' meta-data. FFmpeg, and I believe most media players, ignore this stream.

So you have theora video and ogg vorbis sound in an ogv container. The million dollar question is what you want to convert this to :-). For a straight copy [my favourite wiki page]("http://en.wikipedia.org/wiki/Comparison_of_container_formats") tells me that avi does not support vorbis sound and mp4 does not support theora video while my favourite container Matroska holds everything. You may have some transcoding ahead of you.

It will be not much help to you but if you were interested in experimentation you could test the wiki page by copying your file to a matroska container:

```
ffmpeg -i out.ogv -vcodec copy -acodec copy -f matroska test.mkv
```

And this will test if I am talking crap or not as the audio and video quality should be the same as the original as you have simply exchanged containers. FFmpeg will hopefully remap the streams as well and drop away the skeleton meta-data stream.

I note as well that you are using the Intrepid FFmpeg which may limit your options a little. Have you considered adding a libavcodec-unstripped-51 or [compiling a newer version]("http://ubuntuforums.org/showthread.php?t=786095")?

BTW welcome to the confusing world of multimedia formats :-).

Andrew

---

### Post by linuxisevolution on 2009-03-11
Welcome to the world of confusing media formats(darn someone beat me to it..).


I believe YouTube accepts that format. Could you also please give us a link so we could see?:D

---

### Post by FakeOutdoorsman on 2009-03-11
If whatever site doesn't accept ogv, then first try the easiest option before any encoding by just renaming it to ogg.  I don't know if it would work, but it's worth a try.

---

### Post by dweebazoid on 2009-03-13
Hey thanks everyone,

I've tried a few things out and managed to significantly improve my output file by following some of hte links you guys provided.

I spent some time messing about with switches and got a pretty good version of my video last night - still not as good as the original but I'm on the right lines

fwiw I set a really high bit rate - like 45000 - how high do you guys go when doing this sort of thing?  i will experiment a bit more tonight and might try for even higher as I just need the code on screen to be a teensy bit less pixelated 

but yeah, thanks for all your help, 

steve

---

