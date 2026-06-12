---
title: "Installed Zorin 9 on old machine, runs slow and clunky"
date: 2014-11-27
forum: Ubuntu/Debian BASED
---

### Post by jesselashcraft on 2014-11-27
Greetings - I installed Zorin 9 Ultimate on an old laptop. 

2002 Mircron TransPort GX3
1 gig RAM with a 1 gig swap file
Processor: Mobile Intel® Pentium(R) 4 - M CPU 2.00GHz 
Graphics: R100 (RV200 4C57) x86/MMX/SSE2 TCL DRI2
32 bit
38 gig hard drive

I've turned off all the animations in Compiz. Clicked on the icon by my name on the log out screen and selected "Zorin Desktop No Effects" but
when I call up System Monitor, the CPU still idles at 100%. It looks like Gnome and Firefox are using all the CPU on the process page in
System Monitor.  

Is there anything else I can try or is it just the nature of the machine?

Thanks and Happy Turkey

---

### Post by mastablasta on 2014-11-27
try xubuntu.

it could be the GPU chip is not supported well. might try getting newer driver by PPA, though I doubt it would solve the issue.

is firefox running flash video?

---

### Post by Frogs Hair on 2014-11-27
Moved to ***Ubuntu/Debian Based.  ***

---

### Post by mörgæs on 2014-11-27
> **jesselashcraft said:**
> It looks like Gnome and Firefox are using all the CPU on the process page in System Monitor.

It's often like this. Applications like browsers are much more demanding than the operative system itself. A lighter browser could give a little improvement, but with an RV200 card you need to keep your expectations low. 

Disabling Flash as suggested above helps, but still you will notice that it is old gear. Lubuntu is worth trying.

---

### Post by mastablasta on 2014-11-28
actually I have an old chrunchband install and the card has only 32MB ram while the CPU has 1,2Ghz and the whole OS has 224 MB ram. the youtube flash videos work nicely in Chromium as long as they are not full screen and as long a I keep their quality low.

---

### Post by Rob Sayer on 2014-11-28
According to this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

your video card is in the "Supported, but Hardware is Too Old for Unity" category, which is not good in your case.  Apparently the Zorin DE uses compiz and is like Unity or Cinnamon.  You can turn off all the effects you like but it still needs graphics 3D hardware acceleration capability *just to run itself*.

In addition that's a single core cpu.  I actually tried Linux Mint 17 Cinnamon (also using compiz) on my 1Gb netbook via live USB boot a couple of days ago.  It also has a poorly supported video card with no 3D accel, but I knew that when I installed ubuntu on it and for what I want a netbook for it's OK.  It does have a dual core cpu.  The performance wasn't as bad as your experience but I'd still consider it unusable.

My suggestion is similar to what's already been suggested.  Try lubuntu.  If it works OK and you install it don't add conkys or eye candy at all.  Keep it ugly ... eye candy/effects will just slow it down.

If lubuntu doesn't work well do try crunchbang or another *really* light distro.

---

### Post by jesselashcraft on 2014-12-03
Thanks for the responses everybody.  We turned off the Flash and still have issues. 

Let me ask you this.  If my sister just wanted to use this old machine to play Shrek DVDs for the grandkids, are there things I can delete from 9 Ultimate to make it faster or is it just easier to start over with Lubuntu?  For example, Gnome seems to be using up all the CPU.  Can I modify that at all and still operate the system?

---

### Post by mörgæs on 2014-12-09
It's easier to start with Lubuntu, maybe a minimal install with only a few select applications if you want to get really light.

---

