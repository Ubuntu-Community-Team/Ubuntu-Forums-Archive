---
title: "Hulu interface not responsive"
date: 2009-12-04
forum: System76 Support
---

### Post by echo314 on 2009-12-04
Hi, using a Wildebeest with 64bit Ubuntu. 

Hulu videos play fine, but I cannot use any buttons (to pause/make full screen/change quality). The buttons are just non-responsive, but if I hover over a button it will light up like normal. Tried youtube, that worked fine. This is after the one big update session after booting up for the first time and restarting.

EDIT: huh, youtube does not respond either. Plays fine, so I guess this is a flash problem.

---

### Post by marshmallow1304 on 2009-12-05
What flash are you using?  I am using the alpha 64-bit plugin from [here]("http://labs.adobe.com/downloads/flashplayer10_64bit.html"), and I've had no problems with Hulu or YouTube.

---

### Post by sudo on 2009-12-06
My flash is flaky too.  Work-around: Right click and keep the right button down.  Now click as needed with the left.  Kludgy, but effective....

---

### Post by echo314 on 2009-12-06
Sudo,

I followed the instructions at [http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html](http://helpforlinux.blogspot.com/2009/11/i-cannot-click-on-flash-in-ubuntu.html) which fixed the problem. I don't know how it works though, so gedit at your own risk.

---

### Post by thomasaaron on 2009-12-07
sudo apt-get install libadns1 

That should fix the flash clicking problem.

---

### Post by luopio on 2010-05-05
same problem. libadns1 didn't help. running 10.04 64bit. I can watch vimeo perfectly, but youtube normal or embedded does not work, meaning i can watch the videos but get no reaction from the ui.


[EDIT]*but the right-click-hold-left-click hack works.. [/EDIT]

---

### Post by Cygnia on 2010-05-05
How did you all get Hulu to work on 64 bit? I haven't been able to use Hulu except in the Desktop client for months. I'm still getting the incompatibility error message on every attempt to play a video. I'm using fresh-installed Lucid with the official 64 bit flash plugin.

---

### Post by marshmallow1304 on 2010-05-05
> **Cygnia said:**
> How did you all get Hulu to work on 64 bit? I haven't been able to use Hulu except in the Desktop client for months. I'm still getting the incompatibility error message on every attempt to play a video. I'm using fresh-installed Lucid with the official 64 bit flash plugin.

It's a Flash and/or Hulu issue.  I've seen that many other people, including myself, have the same problem.  There hasn't been much of a fuss about it though, probably because Hulu Desktop works really well.

---

