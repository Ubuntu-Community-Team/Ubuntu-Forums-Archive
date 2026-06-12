---
title: "Wine &amp; 64bit"
date: 2009-11-26
forum: Wine
---

### Post by yester64 on 2009-11-26
Hi,
i just reinstalled my system and i wonder if i should use Wine from the software center or just build it.
The reason why i am asking myself this question is, that i read on winehq that 32bit support (32bit libs) are not build in. Meaning you can't run some apps.
I tried the most reason version under 9.10 and i got steam running but wasn't able to install any of my purchased games. Steam just went black and frooze.
To my surprise on winehq is only a guide for 9.04 and the command posted there did not work.

```
CC="gcc-4.3 -m32" LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32" ./configure -v

```

This is from the section 
**[SIZE=1][COLOR=black]Building Wine on Ubuntu / Kubuntu 9.04 (Jaunty Jackalope) [/COLOR][/SIZE][SIZE=1][http://wiki.winehq.org/WineOn64bit#head-4238178f2b27d537ab5f90b4a165e5454454a2ed](http://wiki.winehq.org/WineOn64bit#head-4238178f2b27d537ab5f90b4a165e5454454a2ed)[/SIZE]**

Does someone use wine and has 9.10 64bit running and using steam?
If i can get that working i can finally ditch my windows.

Thx and happy TGD :) :popcorn:

---

### Post by yester64 on 2009-11-26
mm.. nevermind that no one has thought.
But i installed version 1.0.1 and with this version i can start the game within steam, but it crashes after a minute.
I have to update my videodriver, perhaps thats the problem now.

I wish i could find a thread where people had similar problems with 1.1.3, but it seem only on my computer. strange.

---

### Post by yester64 on 2009-11-26
its getting stranger and stranger.
now i updated wine to the current version. everything works, but i am still not able to play a game. If i enter css and login to a server, it freezes after a minute.
I have to see if cod4 maybe works.

---

### Post by beastrace91 on 2009-12-14
Wine64 is for running 64bit Windows applications. Not for installing on 64bit Linux if you want to run standard 32bit Windows applications.

Regards.
~Jeff

---

