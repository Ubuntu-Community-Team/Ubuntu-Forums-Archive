---
title: "avidemux and k3b - fitting movie onto 1 CD problem"
date: 2008-08-06
forum: Ubuntu Studio
---

### Post by randytuggle on 2008-08-06
I have been trying to get avidemux to convert an AVI below 700mb into a VCD file--and THEN use k3b to burn the files onto a single CD. Each time is create a VCD type file with avidemux, it creates TWO files; one around 700mb in size,and another less than 200mb. How can I make avidemux create a working VCD image to burn with k3b so that I can burn a video onto a single CD? I do not want a SVCD (which did export fine) because SVCDs won't play on my home DVD player. Please help. I tried the tools menu and the calculator in avidemux with no luck...

---

### Post by MepisReign on 2009-07-16
Well, this is Old, but I have the same problem, any suggestions?

Greetz

Found This:

How can I set the target filesize (e.g. 700 MB) in Avidemux?

If you want to encode your video to a specific filesize, e.g. 700 MB to fit on a CD-R, you need to use the "2 Pass" encoding mode. The 2-Pass mode is available for Xvid and x264 as well as for the MPEG-1/MPEG-2 encoders. It will give you maximum quality for a given filesize. In order to use the 2-Pass mode, choose "Two pass, final/video size" in the video encoder's "Configure" dialog. Then enter the desired size (in MBytes) in the edit box below. But take care: This value applies to the video size only, it does not take the audio size into account! Hence the size entered in the "Configure" dialog will not equal the total size of your output video, unless there is no audio stream in your file. In order to set up the target filesize properly, please use the "Calculator" tool! In the Calculator window choose your output container (e.g. AVI), choose your target media (or custom size) and enter the audio bitrate you have selected. Finally press the "Apply" button, before you close the Calculator window! Now the video encoder has been configured according to your desired total filesize and you can save your video.

Source: [http://forum.doom9.org/archive/index.php/t-126164.html](http://forum.doom9.org/archive/index.php/t-126164.html)

---

