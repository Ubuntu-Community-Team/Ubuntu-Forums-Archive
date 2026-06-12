---
title: "any Hd-converter for ubuntu!?"
date: 2009-05-17
forum: Ubuntu Studio
---

### Post by KanineN on 2009-05-17
Hello!

I'm searching for a HD-converter to ubuntu. I have a .mkv file and I want to play it on my ps3. I have searched this forum and google but with no good results. I have ffmpeg and memcoder but I can't find any options there were I can convert HD-material. 


I want it to be without any loss of quality!

---

### Post by J03y on 2009-05-17
Hello, I'm searching for the same thing. I even made a thread here, but I just got 1 reply: [http://ubuntuforums.org/showthread.php?t=1089898]("http://ubuntuforums.org/showthread.php?t=1089898") 

If you find any working hd video converter for ubuntu let me know, :)

---

### Post by luctor on 2009-05-18
Have you tried Handbrake ?
[http://handbrake.fr/](http://handbrake.fr/)

They have debs for ubuntu 8.10 (32 and 64 bit) but they work fine on my Jaunty box

---

### Post by FakeOutdoorsman on 2009-05-26
I use a compiled FFmpeg to convert 1080i and 720p video from a Panasonic HMC150 to various formats.  I haven't had any issues, but I also haven't converted very much footage yet.  I wrote a guide that describes how to install and use recent FFmpeg:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

I don't have a PS3, but I believe it requires level 4.1 H.264.  Perhaps something like this:
```
ffmpeg -i input.mkv -acodec libfaac -ab 192k -ac 2 -vcodec libx264 -vpre hq -maxrate 62500K -bufsize 78125K -level 41 -threads 0 -crf 26 output.mp4
```

Maybe the video in your mkv is already good enough.  Show the output of:
```
ffmpeg -i your.mkv
```

---

### Post by Puzzlenoise on 2009-05-26
I always use Handbrake, did a well job for me. ^^

---

