---
title: "Ffmpeg Screencasts Out of Sync ;_;"
date: 2011-01-17
forum: Ubuntu Studio
---

### Post by cessusbangy on 2011-01-17
I'm using Virtual Box OSE to emulate Wine (latest version), I'm using the ffmpeg -x11 grab script... but always when I view my video, the video is quicker than the sound?

If it helps, I'm trying to record Fallout 1 & 2 in 640x480 res.

System specs:
Intel Core i7 Duo 3.1ghz
6GB Ram
1GB Nvidia Geforce GT220

Virtualbox:
Max processor used, 128mb of video card used.

Perhaps there is a -noskip option for ffmpeg? I'm dying to find one... thanks in advance.

*EDIT* I also would not mind a script to record from pulse AND my v4l2 webcam... if that is possible...
*EDIT* My Youtube Channel is RetroLPer, after about 4 minutes it goes out of sync, and forces me to alter speed of video and produce some ugly results... while my voice is STILL desynced :O

---

### Post by hgernhardt on 2011-01-18
Just out of curiosity:  Have you tried looking at the [FONT="Courier New"]-vsync[/FONT] parameter of ffmpeg?  

I'm experiencing a similar issue where screencast frames will significantly lead audio, then later on will sync back up.  I haven't tried the [FONT="Courier New"]-vsync[/FONT] parameter yet, and I'm fairly certain [FONT="Courier New"]-async[/FONT] won't do the thing right for me.

Thanks,

Henry

---

### Post by hgernhardt on 2011-01-18
double-post

---

### Post by AutoStatic on 2011-01-18
PulseAudio is the drawback here probably as it allows for higher latencies. If you really want everything perfectly in sync you'll have to use JACK.

[http://wiki.linuxaudio.org/wiki/screencasttutorial](http://wiki.linuxaudio.org/wiki/screencasttutorial)

---

### Post by FakeOutdoorsman on 2011-01-18
> **cessusbangy said:**
> I'm using the ffmpeg -x11 grab script...

What's the "ffmpeg -x11 grab script"? Can you show your ffmpeg command and the complete output?

---

### Post by cessusbangy on 2011-01-19
Thank you all for your input :3
I'll definently try these methods...

---

### Post by dartttt on 2011-01-19
You need to find the exact time difference between audio and video streams. Once you do that use -itsoffset switch. For example if the difference is of 3.500 seconds, then add this at the end of command, -itsoffset 3.500

---

