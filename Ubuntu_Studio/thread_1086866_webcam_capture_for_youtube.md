---
title: "webcam capture for youtube"
date: 2009-03-04
forum: Ubuntu Studio
---

### Post by heiowge on 2009-03-04
I currently use Ubuntu Hardy, but flip back to XP for a variety of things that I just can't get the same level of functionality under linux.

I am slowly reducing the list and spending less and less time in XP, but there is one area that has really caused problems.

I use windows movie maker to capture youtube vids using my webcam and headset mic.  I can't seem to get anything close with linux.  Cheese is choppy, when it works.  mplayer seems to be command line only, and the rest of the programs recommended don't seem to offer any sort of webcam capture (Avidemux etc.)

Any suggestions?

I need easy GUI capture (start, stop, pause will do me nicely) and easy export to a format that will play fine on youtube (mov, wmv or even mpg), without any choppiness or audio time lag.

PS.  Please don't suggest any options extoling the virtues of command line capture as being really easy.  Been there, tried it.  I still get better functionality in XP.  Sorry.

---

### Post by skullmunky on 2009-03-06
just capture from the command line, it's really easy.  (jk)

Try VLC.  

1. Media->Convert/Save
2. Capture Device Tab
3. enter /dev/video0 and /dev/audio for the devices
  * note there may be more you have to do to get the audio included, not sure here ... 

4. click Convert/Save
5. Check the "File" option, browse, choose a file to save it as 
6. Experiment with different output codecs / options to get good quality.  The format kind of doesn't matter that much because YouTube converts what you upload, so you just need to have it at initial decent quality.  This will take some experimentation, although I get great results from the H264 encoder.

---

### Post by ace214 on 2009-03-07
I can never get the resolution to work right with VLC. Even when I manually input 1600x1200, which my camera supports, it records at a very, very low resolution (160x120).

---

### Post by skullmunky on 2009-03-07
@ace214: can you get HD resolution playing back with Cheese, etc.?  I'm curious, I've never used a webcam above 640x480.

---

### Post by ace214 on 2009-03-07
> **skullmunky said:**
> @ace214: can you get HD resolution playing back with Cheese, etc.?  I'm curious, I've never used a webcam above 640x480.
Yeah, it works fine with cheese.

---

