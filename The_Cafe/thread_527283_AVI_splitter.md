---
title: "AVI splitter"
date: 2007-08-16
forum: The Cafe
---

### Post by modefied-version on 2007-08-16
Hii,

    I want to split one  AVI file into few pieces with same extension i.e AVI. How I can do that? I've used the split command, but then the individual splitted files dont have the same extension. Please tell me how to do it.

---

### Post by MonkeyBoy on 2007-08-16
Avidemux is your friend.  Amen.

---

### Post by modefied-version on 2007-08-16
I've  installed Avidemux. But I'm not getting how to split the AVI file using it. and one more thing, whenever i'm trying to open avi file in  avidemux, it's giving me "VBR time map"....what I've to do?

---

### Post by MonkeyBoy on 2007-08-16
If I remember correctly it does that if you have an AVI with a badly compressed audio track.  You need to experiment with different time offsets and check the results to see if the sound remains in sync for the whole video.

---

### Post by MonkeyBoy on 2007-08-16
Actually forget that.  If it gives you that message, tell it to build a time map then check that it has done the audio sync properly.  Once it had done that you can use the bar below the screen to select half of your video then save it.  Repeat for the other half and you should have 2 halves of an AVI video.

---

### Post by kinematic on 2007-08-16
Open the run command box (Alt>F2) and use this command
```
avidemux --autosplit ***
```
you can fill in any desired size after autosplit, then open the avi and save it. Avidemux will now split it at the size you specified.

And build VBR time map is needed for an avi with MP3 variable bitrate to keep everything in sync.

---

### Post by COKEDUDE on 2012-04-16
This is a good guide for avidemux. 

[http://linuxpoison.blogspot.com/2009/06/how-to-cutsplit-video-using-avidemux.html](http://linuxpoison.blogspot.com/2009/06/how-to-cutsplit-video-using-avidemux.html)

---

### Post by CharlesA on 2012-04-16
Back to sleep you go..

---

