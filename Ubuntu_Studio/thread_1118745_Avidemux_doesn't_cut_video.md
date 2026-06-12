---
title: "Avidemux doesn't cut video"
date: 2009-04-07
forum: Ubuntu Studio
---

### Post by Pasdar on 2009-04-07
In Avidemux I open a video file, I select the piece of video that I want to save in a seperate file. I have both video and audio set to Copy. However, when I save the file it saves the exact same file from beginning to the end again. It just ignores what I selected. Has anyone else experienced this problem or am I doing something wrong?

---

### Post by Pasdar on 2009-04-07
I found out what I did wrong. You should just open up the file and select a piece of video you want with selection begin and selection end. You should not cut out everything else and attempt to select the only part that is left.

---

### Post by lovinglinux on 2009-04-07
> **Pasdar said:**
> I found out what I did wrong. You should just open up the file and select a piece of video you want with selection begin and selection end. You should not cut out everything else and attempt to select the only part that is left.

Please notice that Avidemux only cut between [keyframes](http://en.wikipedia.org/wiki/Keyframe), which means you can't cut the movie at a random place. This is fine most of the time, but when you want a fine control of the cutting frame, it might be a problem. Then you need to use the next/previous keyframe buttons to select the exact place of cutting. If you don't use them, you might get an output with a few additional frames or a few missing.

---

### Post by Califord2008 on 2009-04-07
And could you tell us little more about the video clips you cut ... AVIdemux 
cannot output WMV video. So you can't leave video as Copy if you want ... 
instead AsfBin doesn't have a preview screen so I had to use AviDemux

---

### Post by FakeOutdoorsman on 2009-04-08
You can also use FFmpeg if you prefer command-line:
```
ffmpeg -ss 00:03:24:00 -t 12 -i inputvideo.mp4 -acodec copy -vcodec copy output.mp4
```
The *-ss* option tells FFmpeg where to start the cut: hours:minutes:seconds:frames.  The *-t* is the length of your resulting encode in seconds, so in this example it will start 3 minutes 24 seconds into the original video and end 12 seconds later.

---

