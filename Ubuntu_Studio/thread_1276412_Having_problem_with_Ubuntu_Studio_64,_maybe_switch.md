---
title: "Having problem with Ubuntu Studio 64, maybe switch back to 32?"
date: 2009-09-27
forum: Ubuntu Studio
---

### Post by Jestersage on 2009-09-27
In order to see whether Ubuntu Studio is ready for the (relatively) high end machines, I decide to install Ubuntu Studio Hardy (8.04) 64bit as a test.

I used two machines:
Machine a:
-Core 2 Duo
-2GB RAM
-Geforce 6 AGP (I think)

Machien B:
-A-64 3800+
-2GB RAM DDR
-Radeon 2600 PCI-E

So the problems that came up are:
a) Using a logitech webcam in Camorama automatically lock up 
b) Occasional lock up; more so with machine B. Commonly during synaptic or at add/remove
c) Have trouble getting a Netgear USB Wireless G stick recognized even though it works with normal machines (Hardy 32 generic)

Since it seems to be crashing as much as a Windows machine, should i reinstall with 32-bit? I need it to be as stable as possible.

Also, would you recommend using LVM or not? Thanks.

---

### Post by Stochastic on 2009-09-27
You may find that the realtime kernel in 9.04 does have some freezing issues (many reports of this mention network usage like synaptic add/remove).  A workaround for these freezes is to install the vanilla kernel (by installing the [linux]("apt:linux") package) and using it for all the tasks unless you're doing audio work - then boot back into the realtime kernel.  I'm not sure if 64 vs. 32 bit has any bearing on the freezing (I've seen many reports from both system types).

The good news is that 9.10 (which releases at the end of October) looks to have a very stable realtime kernel.  But DON'T GO INSTALLING THE DEVELOPMENT VERSION, it will break.  Wait until October 29th before using it on any production machine.

---

### Post by Jestersage on 2009-09-27
> **Stochastic said:**
> You may find that the realtime kernel in 9.04 does have some freezing issues (many reports of this mention network usage like synaptic add/remove).  A workaround for these freezes is to install the vanilla kernel (by installing the [linux]("apt:linux") package) and using it for all the tasks unless you're doing audio work - then boot back into the realtime kernel.  I'm not sure if 64 vs. 32 bit has any bearing on the freezing (I've seen many reports from both system types).

The good news is that 9.10 (which releases at the end of October) looks to have a very stable realtime kernel.  But DON'T GO INSTALLING THE DEVELOPMENT VERSION, it will break.  Wait until October 29th before using it on any production machine.

Thank you for your suggestion. However, due to the fact that we are selling these machines to clients who have not used computers before, not only is this solution (of selecting kernels) unusable, but also must be limited to 8.04 or 10.04 when it comes out.

Another method is to use 64 Studio, but the 2.1 is really outdated while 3.0, though Ubuntu based, could be buggy... right?

Lastly, does anyone have the repository address that contains linux-rt with PAE?

---

### Post by kayosiii on 2009-09-27
The 9.04 stock kernel actually really good latency wise. you could use in a production environment no hassles.

The stock kernel in 9.10 is a loooooooooooot worse - however the 2.6.29 based rt kernel at least is great.

---

### Post by Jestersage on 2009-09-28
So I guess I must use 9.04 instead of 8.04 LTS? Either that, or seems like everyone read the "8" as "9".

---

### Post by Stochastic on 2009-09-28
Wow, I totaly did read the 8 as a 9.  Sorry about that.  From both my experience and others reports, 8.04 was a stable RT kernel.  The problems you described fit identically with issues seen across the board on 9.04

I found 64Studio 2.1 to be very stable, though yes, some programs are getting quite stale in that release.  It still works like a rock *minus the bugs/glitches inherent in those older program versions.  I've yet to try the Beta 3.0 release (but wouldn't sell any beta software to customers if I were you) but it is based on 8.04 (with a different kernel and some newer applications).

Maybe 8.04 on a 32 bit system will play nicer for you.
Though it seems silly that you'd be willing to ship 8.04 software but not 9.10 software as the support for these editions expire at the same time. (in April of 2011)

---

### Post by Jestersage on 2009-09-29
> **Stochastic said:**
>   Though it seems silly that you'd be willing to ship 8.04 software but not 9.10 software as the support for these editions expire at the same time. (in April of 2011)

Well, I have to provide the unit at the first week of Oct.

In any case, I think I will do a test type with 32 bit kernel for now. In that light, how does a 2.8 Gz P4 with 1Gb of RAM sound (for audio production, no pun intended)? Or should I up the RAM to 2Gb to have smoother operation?

---

