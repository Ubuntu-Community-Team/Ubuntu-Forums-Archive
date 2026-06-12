---
title: "Terminal-only Linux for old machine"
date: 2009-10-31
forum: The Cafe
---

### Post by HyperHacker on 2009-10-31
Can anyone suggest a Linux distro that I can burn to a CD and install on the hard disk of an old machine (Pentium ~200mhz), which will just boot up to a terminal? The only one I've found is TTYLinux which hangs at "generating DSS host key". All the other "minimal" distros still seem to have X and a lot of other things I don't need that just take forever to start up.
All I need is a terminal where I can run a small program (run from USB stick, or written and compiled on the machine itself) to play with the parallel port.

---

### Post by Icehuck on 2009-10-31
> **HyperHacker said:**
> Can anyone suggest a Linux distro that I can burn to a CD and install on the hard disk of an old machine (Pentium ~200mhz), which will just boot up to a terminal? The only one I've found is TTYLinux which hangs at "generating DSS host key". All the other "minimal" distros still seem to have X and a lot of other things I don't need that just take forever to start up.
All I need is a terminal where I can run a small program (run from USB stick, or written and compiled on the machine itself) to play with the parallel port.


Debian,Slackware.

---

### Post by miegiel on 2009-10-31
I run debian without X on a 450MHz PII, you get to choose whether you want X (or the gnome desktop, not really sure about the exact choice) or not during installation.

---

### Post by Xbehave on 2009-10-31
there is ubuntu-server, i would go with debian though

---

### Post by MelDJ on 2009-10-31
Minix? 
[http://www.minix3.org/](http://www.minix3.org/)

---

### Post by Xbehave on 2009-10-31
> **MelDJ said:**
> Minix? 
[http://www.minix3.org/](http://www.minix3.org/)
That's not even linux, you may as well suggest BSD or solaris.

---

### Post by MelDJ on 2009-10-31
> **Xbehave said:**
> That's not even linux, you may as well suggest BSD or solaris.

my bad ;)

---

### Post by hellion0 on 2009-10-31
INX, perhaps?

I use Ubuntu Minimal, with only the "cli" system installed along with some CLI apps like cplay, irssi and mc.

---

### Post by prshah on 2009-10-31
> **HyperHacker said:**
>  an old machine (Pentium ~200mhz), which will just boot up to a terminal? 

I suggest microcore linux; only 7mb (terminal) or 10mb (with GUI) yet fully functional and modern distro. see [http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

---

### Post by -grubby on 2009-10-31
I'd suggest Arch, but there aren't any official i586 builds

---

### Post by HyperHacker on 2009-11-01
> **prshah said:**
> I suggest microcore linux; only 7mb (terminal) or 10mb (with GUI) yet fully functional and modern distro. see [http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)Micro is the one without X? I don't see any installation instructions for that version. Can run it from CD but it'd be a shame to let that hard disk go to waste. :P Thanks for the suggestion.

---

### Post by clonne4crw on 2009-11-01
My vote for Debain. Comes with lots of stuff, and X if you want it to.

---

### Post by dragos240 on 2009-11-01
You know. X can run on a system with only 16MB of ram. Works fine. I should know. I got linux on my dreamcast.

---

### Post by -grubby on 2009-11-01
> **dragos240 said:**
> You know. X can run on a system with only 16MB of ram. Works fine. I should know. I got linux on my dreamcast.

But he didn't mention how much ram he had?

---

### Post by cariboo on 2009-11-01
The Ubuntu alternate install CD type **cli** at the prompt.

---

### Post by HyperHacker on 2009-11-01
Pretty sure it has 64M RAM. Thing is I don't want to wait for a desktop environment, firewall, SSH etc to start up when all I need is a command line for 10 minutes on a machine that's not connected to a network. I'll look at Debian.

---

### Post by cariboo on 2009-11-01
Slap a network card in the thing, it's pretty useless without one. :)

---

### Post by HyperHacker on 2009-11-01
Not if it can display a terminal and compile C. Especially if it can read a USB stick. I'm pretty sure it has one anyway if I need it.

---

### Post by steev182 on 2009-11-01
No network card? Whack Windows 98 on there ;)

---

### Post by dragos240 on 2009-11-01
> **-grubby said:**
> But he didn't mention how much ram he had?

True. he didn't. But windows 98 takes 64mb of ram. And this takes 16. I'm saying that it should work on his computer.

---

### Post by marshag63 on 2009-11-01
+1 for INX.  It has a menu system built in for you to mount USB/drives/networks and share files plus tons of other great stuff from internet radio and playing CDs to office apps and even a console game or two, plus tutorials for beginners.  

But if you want a setup where you want to think through each step (script and program writing), a cli-ubuntu install (from the alternate CD) or debian are the way to go.

Good luck!

MarshaG.

---

### Post by HyperHacker on 2009-11-01
Is INX supposed to be able to run on 64MB of RAM? It's running out of memory during startup.

---

### Post by marshag63 on 2009-11-02
Not sure about that - its based from ubuntu 8.04.  If you can find a way to make a 300 mb or so swap partition, that will help a lot.  (I know DamnSmallLinux boots on 64 mb, then use fdisk to make a swap partition).  I don't know that I would use  DamnSmallLinux for your project either.  I've only installed INX on a USB key - I know there are extra steps to getting it on a hard drive.

Let us know how it turns out.

P.S. See this links also (particularly "Install an Ubuntu Command Line System" section:  [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

and maybe 

Then, [http://inx.maincontent.net/devel/unstable/](http://inx.maincontent.net/devel/unstable/)   >  inx unstable 1.15 if you feel brave to try this:  [http://lists.inx.maincontent.net/pipermail/inx-inx.maincontent.net/2009-August/000286.html](http://lists.inx.maincontent.net/pipermail/inx-inx.maincontent.net/2009-August/000286.html)  (see step 2).



MarshaG.

---

### Post by HyperHacker on 2009-11-03
Well I think the machine in question is just fried. Everything I try takes about 10 minutes to boot up, then either hangs or panics. I'm using Microcore on a different machine and it looks like it'll do the job. :) Thanks for the info.

---

### Post by marshag63 on 2009-11-03
Can you boot microcore on it and then make a swap partition (don't forget to turn swapon) - sounds like what is needs - at least 300 MB, then you should be able to proceed with CLI ubuntu or Debian.

MarshaG.

---

### Post by HyperHacker on 2009-11-03
Can't boot anything. Running a memory test on it. Runs awfully slow too...

---

### Post by prshah on 2009-11-04
If you have an old CDROM drive, I suggest you check the max supported speed, and then burn the CD at about half (or lower) of the max supported speed.

When working with old drives, I tend to forget that my current drives burn CDs at full speed (52x) which then cannot be read reliably by the older drives (Eg, a Creative 8x). Typically, I burn CDs for this Creative drive at 4x.

---

### Post by HyperHacker on 2009-11-04
It's a 52x, which seems to be reading just fine. They all end up saying out of memory or APIC resources can't be allocated.

Looking at the results, it might be some kind of timer/CPU clock problem. The test isn't showing any errors, but its elapsed time is only about 90 seconds, and I'm sure it's been running for at least 20 minutes. O.o
It doesn't seem to be running hot, but this does match up with the horribly slow (failed) bootups I saw, so hmmm.
It does look like it's counting at the right speed, but only updating the display every several seconds (sometimes 5, sometimes 10). The test also seems to be running very slowly.

---

### Post by prshah on 2009-11-04
> **HyperHacker said:**
> but its elapsed time is only about 90 seconds, and I'm sure it's been running for at least 20 minutes. 

In that case you might consider checking / replacing the CMOS battery. It's a small, coin-shaped, 3v, CR2032 battery. You can check the battery with a digital multimeter, or just replace it.

Note that I've never seen a case of a motherboard malfunctioning in this fashion due to the CMOS battery; Many Intel original desktop motherboards stop working (dead) if the battery is back, but come back to life within minutes when the battery is replaced, but I've never seen this kind of failure, so it may not be related to the battery at all.

---

