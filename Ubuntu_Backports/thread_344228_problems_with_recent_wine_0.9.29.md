---
title: "problems with recent wine 0.9.29"
date: 2007-01-22
forum: Ubuntu Backports
---

### Post by komuta on 2007-01-22
Doesn't everyone else have problems with this version ? I checked the forum since the update, but can't find any information about wine bugging. Nevertheless, I double checked today on my edgy installation at work : same results. I can't launch ANY application with wine 0.9.29. Can't even launch winecfg, I got only the window outline without any content. And even after having killed the window, the wineserver remains.
Anyone encounter the same problems ? Is this update definitely buggy ?

---

### Post by buMPer on 2007-01-27
> **komuta said:**
> Doesn't everyone else have problems with this version ? .............. Is this update definitely buggy ?

I've read a lot about improvements for wine-0.9.29.  But for some reason, hardly ever worked for AMD64 x2 or any AMD64 arch.  i'm not sure if it's the 2.6.17-generic kernel or the latest wine.  i tried upgrading my kernel to 2.6.19.2 but the NVIDIA video card seems to have an issue with the latest kernel.  the only reason i'm hanging on to WinXP is CS:Source.  it's like choosing between "the devil and the deep blue sea".  

anyway, try this [[COLOR="Blue"]_HOWTO_[/COLOR]]("http://wiki.winehq.org/WineOn64bit") if you have AMD64.  


peace!

---

### Post by jasonxh on 2007-01-28
> **komuta said:**
> Doesn't everyone else have problems with this version ? I checked the forum since the update, but can't find any information about wine bugging. Nevertheless, I double checked today on my edgy installation at work : same results. I can't launch ANY application with wine 0.9.29. Can't even launch winecfg, I got only the window outline without any content. And even after having killed the window, the wineserver remains.
Anyone encounter the same problems ? Is this update definitely buggy ?

exactly the same thing with me.

---

### Post by komuta on 2007-01-29
> **buMPer said:**
> I've read a lot about improvements for wine-0.9.29.  But for some reason, hardly ever worked for AMD64 x2 or any AMD64 arch.  i'm not sure if it's the 2.6.17-generic kernel or the latest wine.  i tried upgrading my kernel to 2.6.19.2 but the NVIDIA video card seems to have an issue with the latest kernel.  the only reason i'm hanging on to WinXP is CS:Source.  it's like choosing between "the devil and the deep blue sea".  

anyway, try this [[COLOR="Blue"]_HOWTO_[/COLOR]]("http://wiki.winehq.org/WineOn64bit") if you have AMD64.  

I do have an AMD64 x2 machine, but I use the x86 arch on Ubuntu. Besides, I've got the very same bugs with this version of wine on the computer at my work, which is a simple Pentium 4.

---

### Post by ukrudl3r on 2007-03-06
> **komuta said:**
> .... I can't launch ANY application with wine 0.9.29. Can't even launch winecfg, I got only the window outline without any content. And even after having killed the window, the wineserver remains.
Anyone encounter the same problems ? Is this update definitely buggy ?

Exact same behavior on openSUSE 10.2, 32-bit running on AMD64.  Setup with winetools on two different nvidia based systems... and different version of wine.  HELP!

:confused:

Worked in the past on one of the systems with SUSE 10.1 (32-bit).

---

### Post by jasonxh on 2007-03-07
Well, my problem was eventually solved by "pkill scim". Seems like another software that conflicts with scim...

---

