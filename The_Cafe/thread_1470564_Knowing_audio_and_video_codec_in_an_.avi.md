---
title: "Knowing audio and video codec in an .avi"
date: 2010-05-02
forum: The Cafe
---

### Post by praveesh on 2010-05-02
I have a video player (hardware not a software). It can play some avi files . Is there a way to know which video and audio codecs are present in the video file ? . If I know, I can convert my video collection to that format and play in the video player . 
Please help.

---

### Post by ve4cib on 2010-05-03
ffmpeg will give you that information:

```
$ ffmpeg -i file.avi
...
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
```

---

### Post by tom.swartz07 on 2010-05-03
> **ve4cib said:**
> ffmpeg will give you that information:

```
$ ffmpeg -i file.avi
...
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
```

+1 for ffmpeg. Its a little difficult to understand at first, because of all of the arguments you need to get a decent output, but it is very good at what it does.


Also, if you need a program to convert stuff, I hear Handbrake is really good: [http://handbrake.fr/](http://handbrake.fr/)

---

### Post by praveesh on 2010-05-03
Thank you I'll try .

---

### Post by praveesh on 2010-05-03
> **tom.swartz07 said:**
> +1 for ffmpeg. Its a little difficult to understand at first, because of all of the arguments you need to get a decent output, but it is very good at what it does.


Also, if you need a program to convert stuff, I hear Handbrake is really good: [http://handbrake.fr/](http://handbrake.fr/)

that link of handbreak is not working
Edit : now it works . I don't know why it didn't work earlier .

---

### Post by handy on 2010-05-03
> **praveesh said:**
> that link of handbreak is not working

The handbrake address is correct, so there is something else stopping you.

---

### Post by NightwishFan on 2010-05-03
Edit, oops you use KDE. +1 ffmpeg then.

---

### Post by Judo on 2010-05-03
There are many ways to see these things:

VLC - Tools > Codec Information
SMPlayer : Options > View info and properties
MediaInfo: It's a standalone program that does nothing but display this information.  There are DEBs on its website.

Those three should be easier to understand, compared to ffmpeg.

---

### Post by praveesh on 2010-05-03
> **Judo said:**
> There are many ways to see these things:

VLC - Tools > Codec Information
SMPlayer : Options > View info and properties
MediaInfo: It's a standalone program that does nothing but display this information.  There are DEBs on its website.

Those three should be easier to understand, compared to ffmpeg.

Thanks .

---

### Post by praveesh on 2010-05-03
> **NightwishFan said:**
> Edit, oops you use KDE. +1 ffmpeg then.

I use kde . I find it very interesting , professional and easy to use .

---

### Post by NightwishFan on 2010-05-03
No denying! KDE 3.5 made me switch to Linux full time. I am a Gnome user now though, but I still recommend KDE. VLC is great too, and now it is QT4 based.

---

