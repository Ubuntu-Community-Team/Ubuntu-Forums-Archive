---
title: "hardy - ffmpeg - no audio after convert to .flv"
date: 2008-06-05
forum: Ubuntu Studio
---

### Post by timcredible on 2008-06-05
I've been using this to convert files on gutsy:

```
ffmpeg -i DSCF1234.AVI -s 480x360 -sameq -ar 11025
```

and it worked fine.  However, I try the same thing in hardy and I get no audio.  I'm assuming I'm missing a codec package, but which one?  I have lame installed.  Thanks.

---

### Post by Creative2 on 2008-06-06
turn medibuntu repository 
upgrade ffmpeg

or if you want compile... remember flv "formats" is made with 

flv video codec 
mp3 audio codec 

so i think you need of mp3lame

i use this for my flv 

ffmpeg -i INPUT -b 600k -r 30 -ab 128k -ar 44100 -s 640x480 -ac 2 -y OUTPUT

---

### Post by timcredible on 2008-06-06
i couldn't find mp3lame at medibuntu, or anywhere else.  so i did an upgrade on ffmpeg and all it's libraries, and now it works.  thank for the reply.

---

### Post by gene6482 on 2008-07-25
I've been trying to get this to work and can't.  I guess I'm doing something wrong.

---

### Post by warp99 on 2008-07-28
> **timcredible said:**
> i couldn't find mp3lame at medibuntu, or anywhere else ...

The library libmp3lame is supplied with package 'liblame0' in the ubuntu multiverse repositories.

---

### Post by Creative2 on 2008-07-28
-.-'' FFMPEG installed from mebibutnu repository can handle flv video...
with this

ffmpeg -i INPUT -b 600k -r 30 -ab 128k -ar 44100 -s 640x480 -ac 2 -y OUTPUT

1 add medibuntu repository 
2 reinstall ffmpeg
3 use that commandline
4 problem solved

if you have still problem you can always compileffmpeg or use mencoder 

mencoder  INPUT -oac lavc -ovc lavc -of lavf -lavcopts vcodec=flv:vbitrate=700:acodec=libmp3lame:abitrate=128 -ofps 30 -srate 44100 -vf scale -zoom -xy 320 -o /tmp/OUTPUT.flv

---

### Post by aloa on 2010-02-25
10x for info .. working great :)

---

