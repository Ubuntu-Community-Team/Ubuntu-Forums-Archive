---
title: "BSoD?"
date: 2008-12-13
forum: The Cafe
---

### Post by CJ Master on 2008-12-13
Hello,

I assume that Ubuntu has it's own BSoD, if so what is it like?

---

### Post by CholericKoala on 2008-12-13
Kernel Panic

---

### Post by chris4585 on 2008-12-13
kernel panics are bad mmmmmmkay?

[http://en.wikipedia.org/wiki/Kernel_Panic]("http://en.wikipedia.org/wiki/Kernel_Panic")

---

### Post by starcannon on 2008-12-13
As mentioned, Kernel Panic, I will say I haven't had a Kernel Panic in years, and never had one while running Ubuntu.

---

### Post by FuturePilot on 2008-12-13
Out of the 2 years I've been using Ubuntu, I've only had 1 kernel panic ever. It was nothing special really. It just kind of froze and some of the LEDs on the keyboard were blinking. There wasn't any kind of error screen or anything. I guess if you happen to be on a tty when it happens you'll see some interesting looking error.

---

### Post by OutOfReach on 2008-12-13
Kernel Panic, definately. I've never had one and not expecting one soon. :)

---

### Post by RiceMonster on 2008-12-13
Never had a kernel panic.

Had a BSoD once on windows.

---

### Post by Maverick321 on 2008-12-13
I had one kernel panic, but it was due to a overheating cpu. Well it was more than one but all from the same cause.

---

### Post by Eisenwinter on 2008-12-13
I have never had a kernel panic. I've had BSOD's on windows though.

---

### Post by fiona-conn on 2008-12-13
I've had it happen.

It's called a segfault.

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

In my case, I was running Second Life, at the time, alongside Emesene and XChat. The entirety of my desktop, Emesene, XChat, AWN, all froze up and wouldn't respond to my clicking. Only thing that remained running was SL, but trying to shut down the program, it was slow and eventually unresponsive.

I hit ctrl alt backspace, which exited me out of the segfault to the login screen, where I relogged in, and had to use the kill -9 command on an SL process that had remained running in the background. -.-

Not fun.

---

### Post by Eclipse. on 2008-12-13
> **fiona-conn said:**
> I've had it happen.

It's called a segfault.

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

In my case, I was running Second Life, at the time, alongside Emesene and XChat. The entirety of my desktop, Emesene, XChat, AWN, all froze up and wouldn't respond to my clicking. Only thing that remained running was SL, but trying to shut down the program, it was slow and eventually unresponsive.

I hit ctrl alt backspace, which exited me out of the segfault to the login screen, where I relogged in, and had to use the kill -9 command on an SL process that had remained running in the background. -.-

Not fun.

Seg Faults are not the same as BSoDs.Seg faults is just a problem with a single program.

I have lots BSoDs and only a few kernel panics.One was caused with hardy just after the first alpha (self explanatory) the rest was hardware faults with an old nvidia card.

---

### Post by Newuser1111 on 2008-12-13
> **CJ Master said:**
> Hello,

I assume that Ubuntu has it's own BSoD, if so what is it like?Kernel Panic.

I think I might have had 3 so far.(Ever since I joined these forums.)

---

### Post by Potency on 2008-12-13
Just wondering... but what steps would you take to resolve a kernel panic? Would you just boot from a cd or what?

---

### Post by Newuser1111 on 2008-12-13
> **Potency said:**
> Just wondering... but what steps would you take to resolve a kernel panic? Would you just boot from a cd or what?From booting to hard drive. It would get Kernel Panic on startup.
Restarting the computer fixes the problem.

---

### Post by mips on 2008-12-13
[IMG]http://upload.wikimedia.org/wikipedia/commons/4/4c/Guru_meditation_error.gif[/IMG]

From the Amiga days :)

---

### Post by init1 on 2008-12-13
I rarely get BSODs, but sometimes Ubuntu will crash and I'll have to restart.

---

### Post by fiona-conn on 2008-12-13
> **Eclipse. said:**
> Seg Faults are not the same as BSoDs.Seg faults is just a problem with a single program.

I have lots BSoDs and only a few kernel panics.One was caused with hardy just after the first alpha (self explanatory) the rest was hardware faults with an old nvidia card.

o.O Really? I was told by another Linux user at the time of having the crashes I'd described that it'd been a segfault, and that it's considered the Linux equivalent of a BSOD.

---

### Post by FuturePilot on 2008-12-13
> **Potency said:**
> Just wondering... but what steps would you take to resolve a kernel panic? Would you just boot from a cd or what?
Usually just a hard reboot.

> **fiona-conn said:**
> o.O Really? I was told by another Linux user at the time of having the crashes I'd described that it'd been a segfault, and that it's considered the Linux equivalent of a BSOD.
What you described does indeed sound like a segfault, but it's not the same as a kernel panic. A segfault is usually just a single application crashing, while a kernel panic is the entire kernel crashing.

---

### Post by Potency on 2008-12-13
Thanks... just so i can be prepared if it ever happens to me.

---

### Post by linuxguymarshall on 2008-12-13
I want a Brown Screen of Death for Ubuntu.

---

### Post by lisati on 2008-12-13
Had a few BSODs on XP, some fixed by reseating a PCI card in its socket, some seemed to be related to some kind of "alergy" to (or incompatibility with) SP3

Had a kernel panic once or twice, about the same time the BSOD in Windows (assorted tables related to the MBR seemed to be messed up)

---

### Post by Chame_Wizard on 2008-12-13
1 Kernel panic and that was last year :lolflag:.

---

### Post by -grubby on 2008-12-13
I've had many Kernel Panics, mostly on Arch because of some weird hardware incompatibility. None so far on my current install of Ubuntu, which has been running since August this year.

---

### Post by happysmileman on 2008-12-13
Think I've only had one on Gentoo (built kernel wrong :P), not as pretty as a BSOD.

I decided to make it pretty by (instead of actually fixing the problem) finding the function for it and throwing in a load of printk()'s to make ASCII art and rebooting....

After that it was the most awesome crash ever

> **fiona-conn said:**
> I've had it happen.

It's called a segfault.

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

...

As other have said a segfault is different to a kernal panic, but a segfault can cause a kernel panic depending on what it happens in, a segfault in some key part of the kernel or an important driver I think would cause it, or a seg fault while booting could cause important things to not be set up right?

---

### Post by Grant A. on 2008-12-13
Chances are on Ubuntu it would be an Orange Screen of Death. The Blue Screen of Death is reserved for Kubuntu.

---

### Post by securitynut on 2008-12-13
Never had a kernel panic and don't want one either. I've had many a BSoD on windows. (reason for getting Ubuntu).

---

### Post by zmjjmz on 2008-12-13
I used to get kernel panics every other time I started my MacBook in Gutsy.
This was before suspend/resume worked, and my battery had this weird issue where it would die immediately if unplugged.

This is entirely my fault because I spilled seltzer on it.

---

### Post by MaxIBoy on 2008-12-14
I got a kernel panic when I did a botched job creating an Ubuntu remaster. Other then that, I've only gotten the occasional driver crash.

---

### Post by 3rdalbum on 2008-12-14
> **happysmileman said:**
> As other have said a segfault is different to a kernal panic, but a segfault can cause a kernel panic depending on what it happens in, a segfault in some key part of the kernel or an important driver I think would cause it, or a seg fault while booting could cause important things to not be set up right?

A "segfault" is a "segmentation fault". Apparently it happens when a program tries to access memory that does not belong to it. So, a segfault by nature cannot happen within the kernel, as the kernel can access all memory.

A minor kernel problem is called an "Oops", and sometimes an oops can cause a panic. Sometimes a segfaulting program can cause a panic via proprietary graphics drivers, but then the proprietary graphics drivers cause panics of their own.

---

### Post by Barrucadu on 2008-12-14
I've never had a kernel panic I didn't cause myself (I wanted to know what would happen if I killed init)

---

### Post by EnGorDiaz on 2008-12-14
never had one in windows 

or a kernel panic in ubuntu

---

### Post by MttJocy on 2008-12-14
Only time I had one of those was when removing the monitor cable from the graphics card without realizing someone had borrowed the cards mounting screw felt the card slide out of the motherboard followed by a segfault in compiz and a kernel panic, presumably trying to write to the now none existent memory addresses on the grapics card..

---

