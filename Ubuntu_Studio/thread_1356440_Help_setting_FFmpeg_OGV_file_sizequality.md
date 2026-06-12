---
title: "Help setting FFmpeg OGV file size/quality"
date: 2009-12-16
forum: Ubuntu Studio
---

### Post by JakeStone on 2009-12-16
Hello! I'm trying to use FFmpeg to fix this initial problem:
[http://ubuntuforums.org/showthread.php?t=1309006](http://ubuntuforums.org/showthread.php?t=1309006)

Essentially I have a bunch of AVI files I have recorded using CamStudio (a Windows screencapture program I'm using for video tutorials) and I'm trying to convert them to Firefox-capable OGV videos with FFmpeg.

The below seems to fix the sync problem I've been running into:
(this encodes video/audio separately then slaps them together)
```
ffmpeg -an -i file.avi -vcodec libtheora -f ogg video.ogv
ffmpeg -vn -i file.avi -acodec libvorbis audio.ogg
ffmpeg -i video.ogv -i audio.ogg -f ogg final.ogv
```The problem is that the video for a 5 min, 1280x768 file is about 47MB. Could be worse, but I know it could be much smaller, and I'm having trouble getting FFmpeg to behave and make a smaller file.

So far I've messed with the -b flag in the first command, but no matter what I set it to (200, 100, etc) I seem to get the same 46MB video.ogv instead. I don't care about encoding time, I just want to maximize quality/size. Two-pass encoding doesn't seem to change anything.  Any ideas?

---

