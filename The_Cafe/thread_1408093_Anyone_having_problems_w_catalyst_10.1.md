---
title: "Anyone having problems w/ catalyst 10.1?"
date: 2010-02-15
forum: The Cafe
---

### Post by sandyd on 2010-02-15
I recently installed it onto ubuntu, and it seems... very.... very.... slow.....and laggy.
It seems like theirs an opengl driver problem.
In fact, I cant even scroll this very page without it lagging.

---

### Post by Kubunteando on 2010-02-21
I have been using catalyst 10.1 for a few weeks and in my case it is very stable. Well the scrolling in Firefox has always been slow...

I use Kubuntu Karmic 9.10 with the KDE4 effects on an AMD/ATI HD 4550.
Not noticed performance difference in the graphic card compared with the catalyst 9.12. But I have noticed that the catalyst 10.1 are the first ones that enable OpenGL 3.2 in my card, so there could be issues in the OpenGL.

A big performance issue I have noticed is that I cannot even start the game Dragon Age with Wine while it was working fine with 9.12. I have not installed again catalyst 9.12 to compare but I would not be surprised if there are OpenGL issues.

AMD catalyst drivers 10.1 and 10.2 are awful:
- 10.1 you cannot even install them in 64bit systems without using tricks
- 10.2 will hung just after logging in KDE4

So it seems that AMD is not testing the drivers properly, just they release them and let the customer test them:

Good HW + Crappy drivers = unhappy users

---

### Post by handy on 2010-02-21
At least, thankfully, AMD have released the tech' info' for their GPUs, which has helped the OSS drivers quality accelerate rapidly.

Kernel .34 is to have useful power management implemented for the ATi GPUs.  

As it is now, those using the git packages & kernel are getting vast improvements in 3D performance & some.

I think that most ATi GPU users should be able to happily kiss Catalyst goodbye before this year is out. :)

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

---

### Post by Nerd King on 2010-02-21
Agreeing with Handy, who is something of a local expert on such matters. The pace of development with the open-source drivers is excellent, and I'm presently using the latest stuff through the excellent xorg-edgers ppa and updated kernel courtesy of [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.8/) and get very impressive results. Overall the performance is snappy for productivity/compiz/kwin/linux games but a little slow and choppy when dealing with Wine. However, accuracy of graphical output is far superior to the closed drivers. Given the speed this has happened I think we can expect Wine gaming in the open drivers fairly soon, perhaps within the timescale suggested by handy.

---

### Post by handy on 2010-02-21
I'm no expert. :) 

I just keep loosely up to date with the progress of the OSS ATi GPU situation & to a lesser extent Catalyst.

All in all there is no stopping that train coming to pick up the ATi GPU users & give them a big OSS smile. :D

---

