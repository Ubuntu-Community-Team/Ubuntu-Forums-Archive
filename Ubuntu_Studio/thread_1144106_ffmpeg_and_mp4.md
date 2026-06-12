---
title: "ffmpeg and mp4"
date: 2009-04-30
forum: Ubuntu Studio
---

### Post by odror on 2009-04-30
OS: Mythbuntu 9.04 64bit

It looks like the distrop version of ffmpeg comes without mp4 support. I am guessing that --enable-libfaac is not enabled during compilation. I think that this is a bug. Is there an alternate source for ffmpeg. What is the simplest way to fix it without changing the installation integrity.

ffmpeg -v :

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

---

### Post by unutbu on 2009-04-30
Uninstall your current version of ffmpeg.

See the Comprehensive Multimedia & Video Howto resolution: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Near the beginning in Part I, the guide shows how to enable the medibuntu repository. Then install ffmpeg again.

---

### Post by odror on 2009-04-30
I did install the Medbuntu version I am still having problems

ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 5 ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -threads 4 -title "test" /tmp/vid/tmp.mp4

I get the following error:
ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 5 ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -threads 4 -title "test" /tmp/vid/tmp.mp4
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, nuv, from '/tmp/vid/test.nuv':
  Duration: 55:35:55.20, start: 0.739000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 1920x1088, PAR 136:135 DAR 16:9, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unable to find a suitable output format for 'ffmpeg'

---

### Post by FakeOutdoorsman on 2009-04-30
> **unutbu said:**
> Uninstall your current version of ffmpeg.

See the Comprehensive Multimedia & Video Howto resolution: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Near the beginning in Part I, the guide shows how to enable the medibuntu repository. Then install ffmpeg again.

Medibuntu has not provided a FFmpeg binary since Hardy Heron.  It is now recommended to install the unstripped FFmpeg libraries that are in the Ubuntu multiverse repository:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Alternatively you could compile FFmpeg yourself, but this is less important with Jaunty as the FFmpeg revision in the repository is quite recent compared to earlier Ubuntu versions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by FakeOutdoorsman on 2009-04-30
> **odror said:**
> I did install the Medbuntu version I am still having problems

ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 5 ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -threads 4 -title "test" /tmp/vid/tmp.mp4

...

Unable to find a suitable output format for 'ffmpeg'
Looks like you have two FFmpeg commands mashed together.  Try this:
```
ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -threads 4 -metadata title="test" /tmp/vid/tmp.mp4
```

---

### Post by odror on 2009-04-30
Ok That was my mistake, 

Also should I cancel the medibuntu subscription?

But I am still having a problem, now I have this error:

ffmpeg: unrecognized option '-title'


 ffmpeg -i /tmp/vid/test.nuv -ab 128k -ac 2 -s 480x360 -vcodec mpeg4 -b 378k -flags +aic+mv4 -trellis 1 -mbd 2 -cmp 2 -subcmp 2 -g 250 -maxrate 512k -bufsize 2M -threads 4 -title test /tmp/vid/tmp.mp4
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, nuv, from '/tmp/vid/test.nuv':
  Duration: 55:35:55.20, start: 0.739000, bitrate: 127 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 1920x1088, PAR 136:135 DAR 16:9, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
ffmpeg: unrecognized option '-title'

---

### Post by FakeOutdoorsman on 2009-04-30
The command I provided earlier should fix the title error.  There is no need for Medibuntu unless you want some other packages that the repository supplies.

---

### Post by unutbu on 2009-04-30
> **FakeOutdoorsman said:**
> Medibuntu has not provided a FFmpeg binary since Hardy Heron. 
Oops! You are right. Thanks for the correction.

---

