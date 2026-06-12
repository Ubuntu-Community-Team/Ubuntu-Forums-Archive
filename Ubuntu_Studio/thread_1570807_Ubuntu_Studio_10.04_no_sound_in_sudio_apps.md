---
title: "Ubuntu Studio 10.04 no sound in sudio apps"
date: 2010-09-08
forum: Ubuntu Studio
---

### Post by lakicguitar on 2010-09-08
Hi,I'm a new guy here...I recently switched from Windows XP to Ubuntu Studio 10.04. I have a problem with ubuntu studio sound and production apps like GTick Hydrogen drum machine, gtclick and so on...they have no sound. I click play/start/whatever but there is no sound...When I play a song on youtube or in Audacious the sound works perfectly. Somebody help?

---

### Post by Pablo_F on 2010-09-09
You need to start the jackd daemon, which is the linux audio system used for music production (low latency, flexible virtual connections between jack-aware apps... For more and better info see [1]). Use the GUI, qjackctl, known as Jack Control in the sound and video menu.

You start the daemon by pressing the Start button. Note that once started, you won't have sound out of audacious unlees you choose "jack output plugin" in its preferences. Some apps are "jackified" by default but they also can use other sound servers, some others are the opposite (like audacious), some others only work with jack (like ardour)... 

A crucial point: Make sure you have properly set rtprio and memlock. Otherwise jackd won't start. If you don't know what I am talking about, open a terminal and copy this:

sudo dpkg-reconfigure -p high jackd 

Select YES (use the TAB key)

Then add your user name to the audio group:

sudo usermod -a -G audio yourusername

Reboot your computer.

Launch Jack Control and try again. 

BTW, I doubt you can have gtick working, but gtklick is a much better option (imho) and very jack friendly. 

Cheers! Pablo


[1] [http://jackaudio.org/](http://jackaudio.org/)

---

