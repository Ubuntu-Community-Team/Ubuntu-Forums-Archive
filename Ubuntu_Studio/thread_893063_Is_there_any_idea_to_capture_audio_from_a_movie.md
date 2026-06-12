---
title: "Is there any idea to capture audio from a movie?"
date: 2008-08-17
forum: Ubuntu Studio
---

### Post by Kelen.Chang on 2008-08-17
I'm a new guy of ubuntu, some times i wanna capture whole or part of audio from a movie, is there any suggestion for this?:guitar:

---

### Post by pytheas22 on 2008-08-17
It depends on what kind of video you're dealing with--a video embedded in a website, a DVD or a video file on your computer.  For files on your computer, I think avidemux can usually extract audio:
```

sudo apt-get install avidemux
```

I'm not positive, but I also believe that you can use Audacity:
```

sudo apt-get install audacity
```

---

### Post by Kelen.Chang on 2008-08-18
Usually, i often capture it from video files. movie formats including *.rmvb ; *.avi ; *.mkv ; like that. 
However, what a bout "mencoder" with that?

---

### Post by JEDIDIAH on 2008-08-18
> **Kelen.Chang said:**
> Usually, i often capture it from video files. movie formats including *.rmvb ; *.avi ; *.mkv ; like that. 
However, what a bout "mencoder" with that?

If you are interested in dumping the entire audio track to a file, then that's a pretty simple option. Beyond that and you probably want something
more along the lines of avidemux.

---

### Post by pytheas22 on 2008-08-18
mencoder is a command-line tool that you could use, but if you're just trying to do something simple and basic, I'd go with avidemux.  It's pretty intuitive and there are guides on the Internet for using it, but if you need help on exactly what to do, let us know.

Another option that I just thought of is [VLC]("http://www.videolan.org/vlc/download-ubuntu.html"), which can do simple extraction of audio from a video file and save it into an mp3 (or other) file.  Go to File>Wizard>Transcode/Save to File and you can open up a video file, and then choose to extract only the audio.  VLC (which is really only supposed to be for playing media files, not working on them) doesn't give you many options at all, but if you just need something simple, it gets the job done.

Also by the way I checked and I was wrong about Audacity--I couldn't find any way to make it extract audio from video.

---

### Post by Johann-1.0 on 2010-01-09
[http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html/comment-page-1#comment-12274](http://www.ubuntugeek.com/how-to-rip-dvd-audio-to-mp3-or-ogg.html/comment-page-1#comment-12274)

---

