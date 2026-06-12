---
title: "ffmpeg error with wmv"
date: 2009-11-26
forum: Ubuntu Studio
---

### Post by BoobsLover on 2009-11-26
I'm trying to convert a wmv to avi,but i continue to get this error:

```
root@anon007:/media/Local Disk/atorrents/vids# ffmpeg -i video basics 10 .wmv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:19:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Strap: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```
What can i do?
I also like to split the file after a certain duration ,but don't know if i can do it with ffmpeg.In MKV if possible.

I've tried already to do the same with MKV files creator ,but it fails .Also tried using Avidemux but it screws the audio somehow.

---

### Post by ilil on 2009-11-26
I heard sometimes mencoder is better, sometimes ffmpeg is ...
Try mencoder then

---

### Post by FakeOutdoorsman on 2009-11-26
> **BoobsLover said:**
> I'm trying to convert a wmv to avi,but i continue to get this error:

```
root@anon007:/media/Local Disk/atorrents/vids# ffmpeg -i video basics 10 .wmv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:19:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Strap: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```
What can i do?
I also like to split the file after a certain duration ,but don't know if i can do it with ffmpeg.In MKV if possible.

I've tried already to do the same with MKV files creator ,but it fails .Also tried using Avidemux but it screws the audio somehow.

Try putting the file name in "quotes":
```
ffmpeg -i "video basics 10 .wmv"
```

If that doesn't work, then perhaps FFmpeg is telling the truth and your file is corrupt.  Also, why are you logged in as *root*?

If you want to split the file, use the *-ss* (time offset) and *-t* (length) options.  This example will skip the first 15 seconds of the input and create a 5 second long output:
```
ffmpeg -ss 15 -t 5 input.wmv -acodec copy -vcodec copy output.mkv
```

---

### Post by BoobsLover on 2009-11-26
> **FakeOutdoorsman said:**
> Try putting the file name in "quotes":
```
ffmpeg -i "video basics 10 .wmv"
```

If that doesn't work, then perhaps FFmpeg is telling the truth and your file is corrupt.  Also, why are you logged in as *root*?

If you want to split the file, use the *-ss* (time offset) and *-t* (length) options.  This example will skip the first 15 seconds of the input and create a 5 second long output:
```
ffmpeg -ss 15 -t 5 input.wmv -acodec copy -vcodec copy output.mkv
```

Actually i just renamed the file eliminating the spaces and it worked.Thanks!

---

### Post by BoobsLover on 2009-11-26
> **ilil said:**
> I heard sometimes mencoder is better, sometimes ffmpeg is ...
Try mencoder then
Tried mencoder,and the problem with it is that even if i set to copy all the values,somehow the converted file ends up being much bigger in size than the original.

---

