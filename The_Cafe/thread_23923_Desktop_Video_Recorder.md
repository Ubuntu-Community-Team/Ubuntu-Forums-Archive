---
title: "Desktop Video Recorder"
date: 2005-04-04
forum: The Cafe
---

### Post by superhac007 on 2005-04-04
Does linux have a desktop video recorder?  What I mean is there a utility that will allow you to record a video of your desktop.  I am looking for a way to do visual demonstrations of applications with voice annotated audio.


Thanks!

---

### Post by bored2k on 2005-04-04
>    xvidcap is a tool that captures movement on a selected area of  an  X11
       screen  to files. These files may be a number of individual image files
       (one for each frame captured) or video files encoded on-the-fly through
       FFMPEG’s  libavcodec. You select between the two alternatives by speci&#8208;
       fying a corresponding output filename, ref.  "--file"  in  the  OPTIONS
       paragraph.   On-the-fly  encoding  will  also allow you to record audio
       along with the video. Recording to individual frames may be more conve&#8208;
       nient  if  you wish to preprocess the images before encoding, or if you
       need other video codecs xvidcap does not support. Individual images can
       later be encoded with tools like ffmpeg, mencoder, or transcode.

                   [...]

       The utility comes with two  alternative  GUIs:  An  Xt-based  front-end
       (xvidcap)  and  a GTK2-based one (gvidcap). gvidcap is maintained some&#8208;
       what better, esp.  in  terms  of  user-friendliness.  However,  xvidcap
       should  always  provide the same basic functionality. Keep in mind that
       GUI layouts and behaviours will differ.

       [CENTER]After recording the video, what you would want is robust application to     manipulate Flash application and audio. Last time I did that I worked with Swish, but that is not Linux based.[/CENTER]

[CENTER]Read my signature (below)[/CENTER]

---

### Post by Electron100 on 2009-01-02
recordmydesktop or gtk-reordmydesktop worked very well for me.

Istanbul I could not get to work properly

xvidcap always seemed to fail its target framerate and capture something ridiculously awful like 2fps (no matter what format and codec I tried).

The fact that I'm using compiz may have affected xvidcap and Istanbul. recordmydesktop detected that I was using compiz and may have done something special to compensate, I don't know

---

### Post by mips on 2009-01-02
> **superhac007 said:**
> Does linux have a desktop video recorder?  What I mean is there a utility that will allow you to record a video of your desktop.  I am looking for a way to do visual demonstrations of applications with voice annotated audio.


Thanks!

What DE are you using?

---

### Post by %hMa@?b&lt;C on 2009-01-02
gtk-RecordMyDesktop is pretty nice.

---

