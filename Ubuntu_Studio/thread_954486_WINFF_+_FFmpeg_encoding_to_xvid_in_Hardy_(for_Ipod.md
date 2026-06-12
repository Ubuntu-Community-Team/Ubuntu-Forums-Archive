---
title: "WINFF + FFmpeg encoding to xvid in Hardy (for Ipod Touch)"
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by dredwerker on 2008-10-21
Hi all,

I had winff working and I have updated with all the latest updates and it no longer works.

I have the medibuntu repository version of ffmpeg.

ffmpeg-v produces:

> ffmpeg -v
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg: missing argument for option '-v'

My preset command line from - XviD for Ipod (16:9 Anamorphic) - looks thus:

> r 29.97 -croptop 58 -cropbottom 62 -vcodec libxvid -s 640x272 -aspect 2.35 -maxrate 1500k -b 1250k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libfaac -ar 48000 -ab 80k -ac 2

from this I get unknown codec libxvid.

If I change libxvid to xvid I get a step further to libfaac I get unknown codec libfaac.

 What do I need to do get past this bit?


Tia
Dred

---

### Post by FakeOutdoorsman on 2008-10-21
You're on the right track.  WinFF presets are designed for newer versions of ffmpeg than what Medibuntu offers, which is actually quite old.  Change "libxvid" to "xvid" and "libfaac" to "aac".

---

### Post by dredwerker on 2008-10-23
> **FakeOutdoorsman said:**
> You're on the right track.  WinFF presets are designed for newer versions of ffmpeg than what Medibuntu offers, which is actually quite old.  Change "libxvid" to "xvid" and "libfaac" to "aac".

Thanks for the quick response - I havent been near my box to test this. I suspected it was something like this but I couldnt find it on google.

Next stop recompilation - I didnt want to do that as I would prob get into some other strife. Part of the reason I don't run gentoo ;)

Hope this helps someone else too :)

---

### Post by FakeOutdoorsman on 2008-10-23
> **dredwerker said:**
> Next stop recompilation - I didnt want to do that as I would prob get into some other strife. Part of the reason I don't run gentoo ;)
If you want recompile take a look at:
[HOWTO: Compile the latest ffmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

---

