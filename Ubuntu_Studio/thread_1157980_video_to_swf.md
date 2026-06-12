---
title: "video to swf ?"
date: 2009-05-13
forum: Ubuntu Studio
---

### Post by nacho32 on 2009-05-13
are their any programs that will covert-encode a video file to a swf and have the player built in for the web like a youtube video ?

---

### Post by lukeiamyourfather on 2009-05-13
Why not just upload it to Vimeo or YouTube? The only place I've seen a feature like that is in Flash from Adobe, last time I used it was Flash 8 and the video had to be converted to a proprietary format to work. Cheers!

---

### Post by FakeOutdoorsman on 2009-05-13
FFmpeg from Jaunty Jackalope can do this just fine.  This example will create a 640x480 sized H.264 video with stereo audio:
```
ffmpeg -i input.avi -acodec libfaac -ab 96k -ac 2 -vcodec libx264 -vpre hq -crf 28 -s 640x480 -threads 0 ffmpegoutput.mp4
```
Older Ubuntu versions will need to compile FFmpeg, but it's easy:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Also, make sure to read the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

Then run the outputted video from FFmpeg through qt-faststart (part of the FFmpeg package) so the video can play before being completely downloaded:
```
qt-faststart ffmpegoutput.mp4 newoutput.mp4
```
Or you can use MP4Box (part of the **gpac** package in the repository):
```
MP4Box -add ffmpegoutput.mp4 newoutput.mp4
```
Lastly, you can use the free (for non-commercial use) [JW Player](http://www.longtailvideo.com/players/jw-flv-player/) or [FlowPlayer](http://flowplayer.org/) on your web server to play these videos like any other video site.

---

