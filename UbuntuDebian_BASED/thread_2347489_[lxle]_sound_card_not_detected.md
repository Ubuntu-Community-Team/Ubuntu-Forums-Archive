---
title: "[lxle] sound card not detected"
date: 2016-12-25
forum: Ubuntu/Debian BASED
---

### Post by tbouillaud on 2016-12-25
Hello everyone, 

I am new to Linux and recently installed LXLE eclectica 16.04.1 64bits on a ASUS E200HA notebook. Sorry if this is in the wrong place, but LXLE forums don't seem to be open to registration so this is the only place I could think of to post this.

I've spent a lot of time trying to figure this out by googling but to no success. 
My problem is that I have no sound at all. When I open up pavucontrol, only "dummy output" shows up under output devices. "cat /proc/asound/cards" tells me that no soundcard is detected.

So far I've tried:
1) What was suggested in this (very old) thread
 [https://ubuntuforums.org/showthread.php?t=1316634](https://ubuntuforums.org/showthread.php?t=1316634)
ie reinstalling alsa-base and pulse-audio but that doesn't do it, and I don't get what the other posts are saying (don't even know what a kernel is..)
2) installing xfce4-mixer, but it has so so many dependencies that I don't have, that i've already installed a good dozen of packages and I don't see the end of it, without even knowing if that will solve my problem in the end.

I'm probably not seeing some obvious solution. I'd really appreciate if someone here could tell me which direction to head, thanks in advance !

---

