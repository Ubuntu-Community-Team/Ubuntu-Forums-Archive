---
title: "Take Apple Quicktime MOV video, extract sound to MP3"
date: 2009-04-01
forum: Ubuntu Studio
---

### Post by jw29 on 2009-04-01
Hello,

I'm looking for a way to extract the audio from a Quicktime .MOV video file and save it as an MP3.

I don't care of it's a command line tool, GUI, anything -- whatever works, and is easiest.

Thanks!

---

### Post by rylleman on 2009-04-01
Alright, in the terminal;

**ffmpeg -i input.mov output.mp3**

You might want to set bitrate, then instead use something like;
[B]
ffmpeg -i input.mov -ab 192k output.mp3[/B]

---

### Post by jw29 on 2009-04-01
Worked great!  Thanks!

---

### Post by FakeOutdoorsman on 2009-04-01
If you don't have the **libavcodec-unstripped-51** package installed (also part of the ubuntu-restriced-extras metapackage), encoding to mp3 and other restricted codecs will be unavailable.  Jaunty users can install **libavcodec-unstripped-52**.  Hardy users can install FFmpeg from the [Medibuntu](http://medibuntu.org/) repository.  Intrepid and Jaunty users will also need to tell FFmpeg to use libmp3lame, or it will encode your resulting mp3 file as *MPEG-1 Audio Layer II* (.mp2):
```
ffmpeg -i input.mov -acodec libmp3lame output.mp3
```

---

### Post by kenai- on 2009-04-02
> **rylleman said:**
> Alright, in the terminal;

**ffmpeg -i input.mov output.mp3**

You might want to set bitrate, then instead use something like;
[B]
ffmpeg -i input.mov -ab 192k output.mp3[/B]

I tried this out and it didn't work for me. After extracting the audio from mov to mp3, the mp3 file doesnt work and the size of the file is 0byte. I have ffmpeg installed as well as libavcodec-unstripped-51.

What do you guys think the problem is? Except for the fact that I'm a total newbie. :)

```
ffmpeg -i test-grej-hannas-kamera.MOV -ab 192k Extracted-audio.mp3
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test-grej-hannas-kamera.MOV':
  Duration: 00:03:56.7, start: 0.000000, bitrate: 2130 kb/s
    Stream #0.0(eng): Video: mjpeg, yuvj420p, 640x480 [PAR 0:1 DAR 0:1], 15.03 tb(r)
    Stream #0.1(eng): Audio: pcm_u8, 11025 Hz, mono, 88 kb/s
Output #0, mp2, to 'Extracted-audio.mp3':
    Stream #0.0(eng): Audio: mp2, 11025 Hz, mono, 192 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
[mp2 @ 0xb7d9b2f0]Sampling rate 11025 is not allowed in mp2
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by FakeOutdoorsman on 2009-04-02
FFmpeg is still encoding to mp2 because you didn't tell it to use libmp3lame (it's very annoying that it does that). Try this:
```
ffmpeg -i test-grej-hannas-kamera.MOV -ab 192k -acodec libmp3lame Extracted-audio.mp3
```
I updated my example above as well.

---

