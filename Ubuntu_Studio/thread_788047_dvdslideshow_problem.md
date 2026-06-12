---
title: "dvdslideshow problem"
date: 2008-05-09
forum: Ubuntu Studio
---

### Post by gerben1 on 2008-05-09
Hi, 
I am trying to make a simple picture DVD slide show, without any music. I am getting an error when dvdslideshow tries make a silent audio file as you can see below:

Error in console output:
```

...
[dvd-slideshow] No audio files passed.  Using 0:1:0.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:1:0.000
sox soxio: Failed reading `/dev/zero': unknown file type `raw'
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:1:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
cat: /home/gerben/dvd-slideshow_temp_13985/audio1_????.raw: No such file or directory
sox soxio: Failed reading `-': unknown file type `raw'
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see [dvd-slideshow] No audio files passed.  Using 0:1:0.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:1:0.000
sox soxio: Failed reading `/dev/zero': unknown file type `raw'
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:1:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
cat: /home/gerben/dvd-slideshow_temp_13985/audio1_????.raw: No such file or directory
sox soxio: Failed reading `-': unknown file type `raw'
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/gerben/dvd-slideshow.log for details
[dvd-slideshow] cleanup...
 for details
[dvd-slideshow] cleanup...

```

error in /home/gerben/dvd-slideshow.log:

```

[dvd-slideshow] No audio files passed.  Using 0:1:0.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:1:0.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:1:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
[dvd-slideshow] Creating ac3 audio...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
/home/gerben/dvd-slideshow_temp_13985/audio1.wav: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/gerben/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

```

Does anybody know how I can get this working?

---

### Post by nhdezoito on 2008-05-30
Hi,

I also got the same problem. If you find a solution please let me know.

Thanks.

---

### Post by gerben1 on 2008-05-30
I found out how to solve it in the end, it is in another thread, but anyways to get dvdslideshow working, just run these 2 commands in the console:
```

sudo apt-get install libsox-fmt-all
sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow

```
The first command will install all sox libraries, it is only about 1 Mb in total, and the second command does the necessary text replacement in the dvd-slideshow script.

see this thread:
[http://ubuntuforums.org/showthread.php?t=788085](http://ubuntuforums.org/showthread.php?t=788085)

---

### Post by nhdezoito on 2008-05-30
Thanks

---

### Post by dhughes on 2008-06-13
Thanks gerben1

 I was going in circles trying to figure out why ffmpeg wasn't working,I thought I messed up the install but even using a LiveCD ffmpeg failed.

 Anyway  I just tried it and it seems to have worked, no errors at the end of the slideshow creation anyway.

---

### Post by Rhubarb on 2008-08-17
Thank you so much gerben1!
I re-compiled ffmpeg in the hope that mandvd would work, you post fixed my problem perfectly.  Thanks again :D

---

