---
title: "[SOLVED] program to resize xvid videos"
date: 2008-08-09
forum: Server Platforms
---

### Post by Jordanwb on 2008-08-09
I have several videos using xvid on my server (episodes of M*A*S*H). I want to resize them down to 320X240 for my mp3 player. Since it's silent I can run it overnight and it won't bother me. Any package I could use to do this?

---

### Post by Vivaldi Gloria on 2008-08-09
> **Jordanwb said:**
> I have several videos using xvid on my server (episodes of M*A*S*H). I want to resize them down to 320X240 for my mp3 player. Since it's silent I can run it overnight and it won't bother me. Any package I could use to do this?

Both mencoder and ffmpeg can do that. There are also scripts around for particular mp3 players.

---

### Post by Jordanwb on 2008-08-09
I installed mencoder and it's dependancies.

Let's say I want to scale the file "/var/www/downloads/jordanwb/Season\ 3/3x18\ -\ House\ Arrest.avi" down to 320X240. How would I do that? In the man page there's over 6000 lines, so ...

---

### Post by Vivaldi Gloria on 2008-08-09
> **Jordanwb said:**
>  How would I do that?

I don't know. This script

[http://goondy.free.fr/d2/](http://goondy.free.fr/d2/)

is for cowon D2 which is also 320x240. May be you can learn from it.

I suggest you search a mencoder or ffmpeg script for your player. Much easier than to learn the settings.

---

### Post by Jordanwb on 2008-08-09
See the thing is is that my mp3 player doesn't support MSC or MTP. Now I did find a package for MTP support, I tried to compile it and it said it needed some other package I downloaded it and tried to compile it, it failed.

You know my mp3 player came with a program to convert videos to the proper resolution. I guess for simplicities sake, I'll use it.

---

### Post by Vivaldi Gloria on 2008-08-09
> and tried to compile it, it failed.

You can ask about your compiling problem here:

[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

> You know my mp3 player came with a program to convert videos to the proper resolution. I guess for simplicities sake, I'll use it.

When you said server I assumed that you only have command line. If you have a desktop environment then there are a lot of gui frontends to ffmpeg and mencoder: iriverter, winff, mediacoder (with wine), avidemux, etc. Start by trying iriverter.

---

### Post by Jordanwb on 2008-08-09
> **Vivaldi Gloria said:**
> When you said server I assumed that you only have command line.

You assumed correctly.

---

### Post by Dedoimedo on 2008-08-10
Hello,
I've worked with ffmpeg, it does its work well.
Try it, see if it fits your needs.
Dedoimedo

---

### Post by Jordanwb on 2008-08-10
The other guy suggested ffmpeg. I like your page on Hillbilly physics regarding time travel:

> If we accept the Big Bang theory as true or at least plausible

---

### Post by FakeOutdoorsman on 2008-08-10
FFmpeg from the Ubuntu repository hasn't been configured to support restricted formats such as mp3, xvid, aac, etc.  You'll either have to use a third-party repo, such as [Medibuntu]("http://medibuntu.org"), or [compile ffmpeg]("http://ubuntuforums.org/showthread.php?t=786095") yourself if you want to use those formats.  Since portable players can be picky, I recommend finding a video that already works and copying the codecs and other settings that it uses.  You can find these settings like this:
```
[frink@hedron ~]$ ffmpeg -i highfive-ipod.mp4 
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'highfive-ipod.mp4':
  Duration: 00:01:55.74, start: 0.000000, bitrate: 730 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 640x480, 29.97 tb(r)
    Stream #0.1(und): Audio: libfaad, 48000 Hz, mono, s16
```
If you just want to resize the video:
```
ffmpeg -i inputvideo.avi -s 320x240 -vcodec xvid -acodec copy outputvideo.avi
```
You can add the "-b" option to control bitrate, otherwise it will use the default "-b 200k".

---

### Post by Jordanwb on 2008-08-10
Ok thanks.

---

