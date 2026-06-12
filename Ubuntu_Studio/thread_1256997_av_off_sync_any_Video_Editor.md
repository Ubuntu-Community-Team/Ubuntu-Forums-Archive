---
title: "a/v off sync any Video Editor"
date: 2009-09-03
forum: Ubuntu Studio
---

### Post by shane2peru on 2009-09-03
ok, here is the scoop.  I have an analog video camera.  I put it on to play and record the video through my tv card to my computer.  I have done up to 2.5 hours of video this way, and it works great.  a/v sync is fine.  However when I go to edit these videos, for example if I only take and cut it into two smaller segments (nothing fancy here) 20 minutes into the video the a/v is out of sync!  I have used kdenlive, cinelerra, and avidemux both give me the same results.  Gopchop keeps crashing when I try and load the file.  Pitivi also crashes not loading the clip.  This is really annoying.  I want to be able to clip the videos down to where I want them, and put them on a dvd.  I have already done this successfully for a few of them, but now I'm having all kinds of problems with a/v sync.  Any help would be greatly appreciated!  I'm working on Jaunty 64bit, updated, intel Pentium D (Duo? Dual processor) with 3Ghz.  I'm quite frustrated with this, and really looking for some answers.

Shane

---

### Post by shane2peru on 2009-09-03
There was a PiTiVi update today, and it works!!!  I only rendered in ogg format, but that is fine with me.  PiTiVi is very slow to work with compared to kdenlive.  But at least it works.  I think it is my encoding engine.  Apparently ffmepg is messing things up when I encode.  I have the latest ffmpeg installed, perhaps I will play around with kdenlive, and see if I can change it's encoder.  I know that PiTiVi uses gstreamer as it's backend.  I don't know if that is the difference, or it's encoder.  At any rate, I'm making forward progress, but still could use your help.  :D  

Shane

---

### Post by wildhostile on 2009-09-04
Hi shane2peru,

How do you capture your video? What format(videocodec, audiocodec) did you use?

---

### Post by shane2peru on 2009-09-05
> **wildhostile said:**
> Hi shane2peru,

How do you capture your video? What format(videocodec, audiocodec) did you use?

I spent some serious time mostly trial and error coming up with this line:
```

mencoder -tv norm=NTSC:driver=v4l2:width=720:height=480:input=$n:fps=30000/1001:alsa:adevice=plug.saa7134 tv:// -endpos $time -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf pp=lb/ha/va/dr,hqdn3d -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:acodec=mp2:abitrate=192:aspect=4/3 -o /home/$USER/$location/$videoname.mpg

```
to capture my video off my analogue camera.  I had some issues to overcome when capturing over my card, but now have it working great.  The video that I directly capture is fine, there are no issues with it's a/v sync.  It is only post editing and rendering that it becomes bad.

Shane

---

