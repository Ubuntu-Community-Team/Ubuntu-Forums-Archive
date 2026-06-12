---
title: "Ffmpeg question"
date: 2009-03-16
forum: Ubuntu Studio
---

### Post by cd-r80 on 2009-03-16
ffmpeg -i video.mp4 -sameq video.avi. What I should add to line if I want to have avi video playable in standart Divx player?

---

### Post by cd-r80 on 2009-03-16
quite dead here. I ment "standalone player". ffmpeg -i video.mp4 video.avi. I cannot play that avi on My Phil*** 3040. What codec or options add?

---

### Post by inobe on 2009-03-16
[http://ffmpeg.mplayerhq.hu/faq.html#SEC23](http://ffmpeg.mplayerhq.hu/faq.html#SEC23)

theres the facts :)

edit" i will try to see if i can put a command together "no guarantee" though i will certainly try

---

### Post by cd-r80 on 2009-03-16
I have read things from there and tried some, but no success. I installed HandBrake & trying with that.

---

### Post by FakeOutdoorsman on 2009-03-16
Try this:
```
ffmpeg -i video.mp4 -sameq -vcodec mpeg4 -vtag xvid -acodec libmp3lame -ab 128k video.avi
```
If the player has any bitrate limitations:
```
ffmpeg -i video.mp4 -b 756k -vcodec mpeg4 -vtag xvid -acodec libmp3lame -ab 128k video.avi
```
You will need the** libavcodec-unstripped-51** package to enable restricted encoders in FFmpeg (Intrepid only).

---

### Post by inobe on 2009-03-16
> **FakeOutdoorsman said:**
> Try this:
```
ffmpeg -i video.mp4 -sameq -vcodec mpeg4 -vtag xvid -acodec libmp3lame -ab 128k video.avi
```
If the player has any bitrate limitations:
```
ffmpeg -i video.mp4 -b 756k -vcodec mpeg4 -vtag xvid -acodec libmp3lame -ab 128k video.avi
```
You will need the** libavcodec-unstripped-51** package to enable restricted encoders in FFmpeg (Intrepid only).

that worked' very nice, thanks for sharing

```
:~/Videos$ ffmpeg -i beyonce.mpeg -sameq -vcodec mpeg4 -vtag xvid -acodec libmp3lame -ab 128k beyonce1.avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpeg, from 'beyonce.mpeg':
  Duration: 00:03:23.6, start: 0.236800, bitrate: 1947 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x240 [PAR 200:219 DAR 880:657], 104857 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 224 kb/s
Output #0, avi, to 'beyonce1.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 352x240 [PAR 200:219 DAR 880:657], q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 6103 fps=159 q=0.0 Lsize=   47578kB time=203.6 bitrate=1914.0kbits/s    
video:44057kB audio:3183kB global headers:0kB muxing overhead 0.717106%
```

and properties say **XVID MPEG-4**

---

### Post by andrew.46 on 2009-03-17
Hi inobe,

> **inobe said:**
> ```

Input #0, mpeg, from 'beyonce.mpeg':
  Duration: 00:03:23.6, start: 0.236800, bitrate: 1947 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x240 [PAR 200:219 DAR 880:657], 104857 kb/s, 29.97 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 224 kb/s
Output #0, avi, to 'beyonce1.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 352x240 [PAR 200:219 DAR 880:657], q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: libmp3lame, 44100 Hz, stereo, 128 kb/s

```

I recently did a little work on mpeg4 conversion for[ a little media player I own]("http://www.andrews-corner.org/iRiverX20.html"). Would you be interested to try the strategies mentioned on this page:

[LIST=1]
[*]Two pass encoding
[*]Manually specify the encoding options
[/LIST]

The encoding options I mention are pretty much drawn straight from the FAQs:

[http://ffmpeg.mplayerhq.hu/faq.html#SEC26](http://ffmpeg.mplayerhq.hu/faq.html#SEC26)

All the best,

Andrew

---

### Post by cd-r80 on 2009-03-17
I have VBR sound. Is it easy convert to CBR with ffmpeg ? I do it Now first in Avidemux. But options for ffmpeg would be nice. VBR makes problems in my player. AC3 would be also better I think. ( I don't know much about converting!).

---

### Post by inobe on 2009-03-18
> **andrew.46 said:**
> Hi inobe,



I recently did a little work on mpeg4 conversion for[ a little media player I own]("http://www.andrews-corner.org/iRiverX20.html"). Would you be interested to try the strategies mentioned on this page:

[LIST=1]
[*]Two pass encoding
[*]Manually specify the encoding options
[/LIST]

The encoding options I mention are pretty much drawn straight from the FAQs:

[http://ffmpeg.mplayerhq.hu/faq.html#SEC26](http://ffmpeg.mplayerhq.hu/faq.html#SEC26)

All the best,

Andrew



i will have a look, thanks

---

