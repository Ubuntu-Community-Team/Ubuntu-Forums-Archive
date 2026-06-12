---
title: "Encoding video"
date: 2009-09-25
forum: Ubuntu Studio
---

### Post by Vadi on 2009-09-25
Hi,  

Can anyone recommend me a format and settings for it to use for a video of an RTS game? I've been dabbling with h.264 and mencoder for a while, but its settings format is a bit hard to figure out - and either I get gigantic size with decent video, or crap video with a great size.

---

### Post by FakeOutdoorsman on 2009-09-25
I prefer FFmpeg.  If you're using Ubuntu Intrepid or Jaunty you have access to some powerful encoding presets, but you will need to enable restricted encoders.  This is easy to do and is explained here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Those using older versions of Ubuntu can still use the libx264 presets, but will have to compile FFmpeg and x264.  Some Intrepid or Jaunty users will also want to compile these because the repository versions, although fairly recent, are missing some new and important encoding features.  Compiling FFmpeg and x264 is probably easier than you think and I recommend this if you want the full potential of encoding to H.264 video:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

Preset usage examples are available in the link above.  I recommend the **one-pass CRF** example to start with.  Also, make sure to read the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

---

### Post by prabath_fun on 2009-09-29
Hi,
   I started with dvd::rip. But, As soon as I click encode, no action happens. I tried ripping DVD, I worked. Encoding to .avi is not working. Please help me to solve this.....
With advanced thanks,
Prabath

---

### Post by prabath_fun on 2009-10-03
I tried Acidrip and working well....
Prabath

---

