---
title: "VMWare and VBox lock up physical machine"
date: 2010-01-19
forum: Virtualisation
---

### Post by tyler711 on 2010-01-19
Hello,
I'm running 9.10 32 bit.  I initially installed VMWare player to run an XP SP3 guest, but found that about 30% of the time, launching the VM would cause the system to hard lock (have to press the reset button).

So I installed the latest Virtualbox (closed source with USB).  XP installed, but I find that again, about 1/3 of the time, when I hit "Start machine", my computer locks up.

The lockup is nearly instant (before the VM starts loading the OS, just as it's "boot" screen starts).

I'm running a Core 2 quad q9550 with 4 GB ram.  The VM's only have 512 megs allocated I believe.

Any tips as to where to start looking for an answer?

Thanks,
Tyler

---

### Post by chuina on 2010-01-20
I saw a thread about one week ago with this problem.
He got the solution by changing the processor of VBox to 1.

[COLOR="Red"]Since I'm not an expert so you are on your own risk ![/COLOR]

If you think it is fine then in the VBox go to: **Machine>Settings>System>Processor** 
Move the bar to left (i.e. 1 CPU)
Click OK.

Try...

---

### Post by chipper_farley on 2010-01-20
I'd be careful changing the number of processors Windows expects...I'm pretty sure going up in processors is okay but going backwards will cause it to freak out.  Also, that can cause a reactivation of the OS due to "significant hardware changes" which could be a problem for you too.

I had a very similar problem as well.  I run numerous VBox machines and always had great success on 9.04.  When I went to 9.10, they would crash my system completely.  I actually have a thread out there about this somewhere but no one commented.  My solution was to go back to 9.04.  

Since that time, I've gotten a new computer and am running 9.10 on it with no problems whatsoever.  Because of that, I think there's some very low-level change between the two releases that is causing the problem, although who knows what it is.

My ultimate solution was to go back to 9.04...less than ideal for sure but it was either that or possibly spend the rest of my life trying to figure this problem out.

Hope this helps.

Good luck.

---

### Post by yavoh on 2010-01-25
I tried that, I still crash.  My pattern is slightly different though:

VBox always crashes.  No matter what.  Period.

VMWare Workstation doesn't crash the first few times on a fresh install.  After a while (perhaps after a reboot?  I'm not sure...) it will begin locking up immediately after I start loading a vm, whether from a state or a cold boot.

---

### Post by tyler711 on 2010-01-26
Well, I looked and both have 1 processor.  It's been behaving the past few days.  I can't seem to find a pattern.  But my VBox definitely works at least most of the time.

---

