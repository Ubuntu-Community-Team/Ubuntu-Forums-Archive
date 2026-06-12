---
title: "can't hardcode subtitles using avidemux"
date: 2009-01-22
forum: Ubuntu Studio
---

### Post by pytheas22 on 2009-01-22
I'm trying to use avidemux to hardcode subtitles into an .avi file.  I can go to Video>Filters and select a subtitle file without a problem, and the subtitles then appear successfully in the output preview (see attached screenshot, with original video on top and output below).

However, when I press the 'Save' button in the upper-left of the main avidemux window, the file that gets created doesn't contain the subtitles--it just creates a copy of the original video.  (When I press the 'Save' button within the 'Video Filter Manager' window that I used to load the subtitle file, nothing happens.)  What am I doing wrong that's preventing the subtitles from being encoded into the output video?

Thanks in advance for any help.

---

### Post by pytheas22 on 2009-01-22
Figured it out...the problem was that I had both audio and video set to 'copy'.  Apparently that doesn't work; I needed to choose a specific video output format in order for the subtitles to be encoded.  I chose the same format that the input video was in, Xvid/MPEG-4, and it worked fine.

---

### Post by dakur on 2009-03-23
Hi,

When I add .srt and save as an mpeg, then I user Nero to create A VIDEO_TS to burn on a DVD.  Subtitles are ok, but picture is shaky. If I create the VIDEO_TS without the subtitles, picture is OK.

Any ideas ?

---

### Post by pytheas22 on 2009-03-23
> When I add .srt and save as an mpeg, then I user Nero to create A VIDEO_TS to burn on a DVD. Subtitles are ok, but picture is shaky. If I create the VIDEO_TS without the subtitles, picture is OK.

I've never used Nero, so I'm afraid I can't offer much advice.  Maybe saving in a different format than mpeg would help?  But that's just a guess.

---

