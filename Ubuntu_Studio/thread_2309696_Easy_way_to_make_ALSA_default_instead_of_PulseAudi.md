---
title: "Easy way to make ALSA default instead of PulseAudio?"
date: 2016-01-12
forum: Ubuntu Studio
---

### Post by marseille2 on 2016-01-12
PulseAudio on Trusty 14.04 is a lot of work. It flakes on me so much, I've been searching through tutorials about making ALSA default. The problem is... they're all out-dated. Is there a reliable and trustworthy way to do this?
----

UPDATE: I think I found an alternative using snd-aloop ([ALSA Loopback]("http://www.alsa-project.org/main/index.php/Matrix:Module-aloop")). It's a little rough since I'm still sorting out the .asound file ... but so far, dropping pulseaudio (didn't uninstall, just completely disabled at start-up), seems to have ended some distortion I got when playing/recording in a modular format (single apps, instead of a full blown DAW). 


BTW ... I'm not sure if snd-aloop is part of Ubuntu 14.04, since I've made a lot of changes to the original OS and added outside repos ... but I did find it in my 3.19.x kernel. I just upgraded to  4.2.0-25-lowlatency, hoping to resolve some power problems, and the loopback module is still there and working. 


If anyone is interested, I figured out how to see if I had the module, and load it at [link]("http://confoundedtech.blogspot.com/2012/08/building-installing-alsa-loopback.html").

---

### Post by jejeman on 2016-01-13
Does setting 
```
autospawn = no
```
in
```
 ~/.pulse/client.conf
```

And killing the daemon don't work?

---

### Post by yoshii on 2016-01-14
I vaguely remember experimenting with a Lubuntu v14.04.x installation where I made sure that PulseAudio wasn't installed.  
For a while it was just ALSA, but it was still a bit frustrating to use for some reason which by now I've forgotten.  I actually ended up manually installing PulseAudio into Lubuntu.  

But it did remind me that you could remove PulseAudio entirely, and then just install all of the ALSA stuff and make sure to re-install anything else that might accidentally get removed when removing PulseAudio.  I would try that.

---

### Post by marseille2 on 2016-01-15
Hmmm... this one is a true puzzle. Is there another option?

---

