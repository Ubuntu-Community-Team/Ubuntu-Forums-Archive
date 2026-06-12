---
title: "mainactor opensource"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by Cresho on 2009-01-31
Hi!

I was about to purchase Mainactor for my linux box but apparently, they decided to release it as open source or so I think they did decide to release it as open  source.

Can anybody give me any idea what's going on?

---

### Post by Cresho on 2009-02-01
I recently found the program as a download.  Too bad!  The deb file for 32bit works flawlessly on linux.  to date, it is the ultimate video editor.  The demo works fine.  you can test all the paramaters.  With high definition videos, you will need to convert to mp2 with winff and here are the paramaters.  the problem with the demo is it leaves a watermark on the video.
make sure you use .mpg as an extention
-vcodec mpeg2video -r 59.94 -s 1280x720 -b 16000K -acodec mp2 -ab 192k -ar 48000 -ac 2

I use a xacti hd video recorder.   I convert the files with MP4Cam2AVI_v2.79 and creates a few files which then i use deshaker in virtualdub under wine which i then use winnff with the above parameters to convert further.  I then import them into mainactor and can do some beautiful work.

but in reality, all you need is winff convert to mp2 for use in mainactor.  i use mp3cam2avi and virtualdub as an added step to deshake the video.



It be really great to read on updates on where the source of the software is heading.

---

### Post by cotcot on 2009-02-01
Mainactor stopped its support for the linux version.

There are other good editors supporting mp4 : Blender VSE ; Cinelerra (cinelerra-4 works fine).

---

### Post by Cresho on 2009-02-01
cinelerra and blender works fine as well butt.....

cinelerra can't handle transitions of h.264 codecs well or I probably need to play with it more.


blender cannot do 720@59.94fps correctly.  It does and it doesnt.  well you get the idea.  I get audio vs video missing frames.  I currently am using 2.48 and here is a screenshot of what i do with it.  another thing is that it only allowes around ...300000 frames and at 59.94fps, i get around 30 minutes when I have around 2 hours of video which i want to edit.

[http://forums.steves-digicams.com/forums/attachment.php?id=130257](http://forums.steves-digicams.com/forums/attachment.php?id=130257)

---

