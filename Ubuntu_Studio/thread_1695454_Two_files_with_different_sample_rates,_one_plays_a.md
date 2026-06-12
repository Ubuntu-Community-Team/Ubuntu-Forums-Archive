---
title: "Two files with different sample rates, one plays at wrong speed"
date: 2011-02-25
forum: Ubuntu Studio
---

### Post by halfpower on 2011-02-25
I've installed the ALSA drivers for my Emu-1212m.  My sound card is running, but when I load two files with different sample rates, one of them plays at the wrong speed.  Is there a way to fix this?  I never seemed to have this problem in windows.

---

### Post by zipperback on 2011-02-25
How are you playing the files? 


> **halfpower said:**
> I've installed the ALSA drivers for my Emu-1212m.  My sound card is running, but when I load two files with different sample rates, one of them plays at the wrong speed.  Is there a way to fix this?  I never seemed to have this problem in windows.

---

### Post by halfpower on 2011-02-25
I've tried playing them with "Movie Player" and "Audacious (GTKui)."

---

### Post by cchhrriiss121212 on 2011-02-26
The Emu ALSA driver has some issues with sample rates. 
What I would do is use pulse configuration to set a global sample rate, shown here:
[http://ubuntuforums.org/showthread.php?p=6225657]("http://ubuntuforums.org/showthread.php?p=6225657")

---

### Post by halfpower on 2011-02-27
I actually disabled or removed pulse when I was trying to run some other audio software.  Would the resampling be done on the soundcard?

---

### Post by cchhrriiss121212 on 2011-02-27
I think all the emu cards have a default internal rate of 48kHz which is why many people have speed/pitch issues.
Have you tried adjusting alsamixer? Type it in from a terminal and press f5 to see all your available settings, there should be one for sample rate in there somewhere.

---

