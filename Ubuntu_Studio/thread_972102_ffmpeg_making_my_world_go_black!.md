---
title: "ffmpeg making my world go black!"
date: 2008-11-05
forum: Ubuntu Studio
---

### Post by disabled_20220313 on 2008-11-05
Hi,

I have been trying to create a movie from a set of jpegs for the psat three days and I'm getting no where.

I have a set of images that I have taken over time of a chemical reaction. I am trying to use ffmpeg to join them into a movie. 

I am using the command 

```
ffmpeg -r 10 -b 1800 -i %d.jpg test.mp4
```

All this does is produce a blank movie of a length dependant on the frame rate I set.

I thought there may be some compression going on, as the images I have are very dark. So I tried it on a set of holiday snaps (random images), and I got the same result.

I have tried using mencoder, and "convert". Mencoder won't play ball either, and convert just chews up my RAM and swap space for no apparent reason.

I was hoping to produce a lossless file to begin with, then re-encode to a lossy format to check I don't loose any detail from the image.

Any chance of some help?

Ciarán

---

### Post by FakeOutdoorsman on 2008-11-06
Did you read this?
[3.2 How do I encode single pictures into movies?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC14")

> First, rename your pictures to follow a numerical sequence. For example, img1.jpg, img2.jpg, img3.jpg,... Then you may run:

  ffmpeg -f image2 -i img%d.jpg /tmp/a.mpg

Notice that `%d' is replaced by the image number.

`img%03d.jpg' means the sequence `img001.jpg', `img002.jpg', etc...

The same logic is used for any image format that ffmpeg reads. 

Perhaps you need to tell ffmpeg what kind of file the input is with "-f image2".  Does the ffmpeg output give you any errors?

---

### Post by disabled_20220313 on 2008-11-06
Hi, 

Thanks for the reply. I started using the command from the ffmpeg FAQ and got some results.

I seem to have found a bizarre bug, where opening the file in Totem first gives a black screen, and then visual garbage in VLC. If you open with VLC first, no problem....

My next problem is that it compresses the video quite heavily. I'd prefer it to output to a lossless format first, and that I'd choose to re-encode from there.

This is the output I get from the terminal after successfully running the program.

```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, image2, from '%03d.jpg':
  Duration: 00:00:09.9, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: mjpeg, yuvj422p, 1590x1193, 10.00 fps(r)
File 'i.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'i.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 1590x1193, q=2-31, 200 kb/s, 10.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=   99 q=31.0 Lsize=     882kB time=9.9 bitrate= 729.8kbits/s    
video:874kB audio:0kB global headers:0kB muxing overhead 0.906266%

```

I suspect the "yuv420p" bit is what causes the compression.

Does anyone know a way I can get a full quality output?

Ciarán

---

### Post by disabled_20220313 on 2008-11-06
Progress! 

It seems there is a -qscale option. This is a VBR parameter, that alters the quality of your output it seems.

-qscale = 1, seems to be the highest setting and gives me what I want.

---

### Post by disabled_20220313 on 2008-11-06
Progress! 

It seems there is a -qscale option. This is a VBR parameter, that alters the quality of your output it seems.

-qscale = 1, seems to be the highest setting and gives me what I want.

I'm still interested in getting a completely lossless output though. Any suggestions?

Ciarán

---

### Post by FakeOutdoorsman on 2008-11-06
You can use an encoder such as ffv1, ffvhuff, or huffyuv to create a lossless intermediate output.  I haven't used these before, so I can't say which is "best".  I believe x264 has lossless capability as well, but I haven't looked into that yet:
```
ffmpeg -f image2 -i img%d.jpg -vcodec ffv1 output
```

---

