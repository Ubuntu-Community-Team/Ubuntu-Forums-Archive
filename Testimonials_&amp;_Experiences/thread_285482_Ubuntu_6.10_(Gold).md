---
title: "Ubuntu 6.10 (Gold)"
date: 2006-10-26
forum: Testimonials &amp; Experiences
---

### Post by rbalfour on 2006-10-26
Just finished the core setup of 6.10

WoW! To use a catchpharse "I'm Lovin' IT!"

Decided this time on a clean install, the installer went GREAT.
Love that the Network Manager now has VPN options.
The boot splash is awesome.
I am sure over the next few days, there will more great new little features (No not the Micro$oft features)

To all that made this happen.. 

[CENTER][SIZE="7"]A
BIG
THANK YOU!
U ROCK![/SIZE]
[/CENTER]

---

### Post by TheMono on 2006-10-26
Heavily seconded. I upgraded with a little trepidation that there might be troubles with wireless - none. Works a treat.

Beryl works straight away, I add the repo, install, done.

Plus I can´t even tell that I´m using anything other than original init, which means upstart is doing its job, because frankly I don´t want to know!

Edgy is awesome.

---

### Post by Monstroxus on 2006-10-27
Can you give a very brief and simple instruction how to install and run it? (beryl) Thanks! (I am a newbie)

---

### Post by .t. on 2006-10-28
Assuming you're on Edgy, and using the nVidia drivers, an ATi Radeon with the
open source driver, or an Intel integrated chip:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Information about ATi/nVidia cards and Edgy:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/GCDrivers](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/GCDrivers)

The Beryl Project Wiki is a good source of information.

---

### Post by gerowen on 2006-10-28
I know I've said this in other topics, but newbies can be easily discouraged so I'll say it here too.  Make absolutely sure that you know the PCI address of your graphics card.  X failed to start on my LiveCD and I was an Ubuntu n00b, and I spent "hours" trying to figure out what was going on, including removing my nvidia card and everything.  I had to reconfigure Xorg and set it to the correct PCI adderss so it would use my nvidia card instead of trying to use my on-board card.  To reconfigure Xorg easily, including changing the PCI address, run this if your X fails to start and you're booted to a command line:

```
sudo dpkg-reconfigure xserver-xorg
```

Edit:  If you do not know the PCI address of your card, and you have a Windows installation, go to your device manager and right click your graphics card and go to properties.  Somewhere in there it will show the PCI address as a little note.

---

