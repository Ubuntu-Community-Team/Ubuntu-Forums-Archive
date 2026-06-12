---
title: "FreeBSD speed compared to Linux?"
date: 2005-08-11
forum: The Cafe
---

### Post by Kimm on 2005-08-11
Hi,

I downloaded the freeBSD live CD yesterday to try it out (FreeSBIE I belive it was called). When the download was complete I burnt it to a disk and rebooted the computer. I noticed that the OS on the CD seemed to be faster then the one installed on my HD, although, the CD had XFCE4 whilst I use gnome on linux. but I never used to notice a differnace between the two. The only downside was that FreeBSD didnt seem to find my graphics card and I couldnt configure my network in XFCE.

So,

Does anyone know, is FreeBSD faster then Linux... or is it just me? :-P

---

### Post by nocturn on 2005-08-11
In my experience it is somewhat faster yes.  But hardware support is not so good (graphics cards, USB2, ...).

---

### Post by nocturn on 2005-08-11
Another drawback of FreeBSD is its lack of binary (security) updates.
Most advisories require you to recompile programs or the base system, something that is much more difficult and time consuming then aptitude update && aptitude upgrade...

---

### Post by drummer on 2005-08-11
[QUOTE=Kimm]Hi,

I downloaded the freeBSD live CD yesterday to try it out (FreeSBIE I belive it was called). When the download was complete I burnt it to a disk and rebooted the computer. I noticed that the OS on the CD seemed to be faster then the one installed on my HD, although, the CD had XFCE4 whilst I use gnome on linux. but I never used to notice a differnace between the two. The only downside was that FreeBSD didnt seem to find my graphics card and I couldnt configure my network in XFCE.

So,

Does anyone know, is FreeBSD faster then Linux... or is it just me? :-P[/QUOTE]
 If you mean more responsive, xfce is much, much lighter on resources than gnome is. I've used that live CD as well, but never installed BSD to a hdd. BSD and linux both have unix roots and the speed of each would depend more on the DE, services and packages they run, rather than the general 'one is faster than the other'. For example, Slackware is much faster on older hardware than say Fedora.. both linux distros. The above (freeBSD vs. Linux) is an unfair comparison to me, mostly because of the different desktop environment.

---

### Post by Kimm on 2005-08-11
I dont think you quite understand. I am quite used to using XFCE, as I was using it as me DE not at all to long ago, I made the switch back to gnome perhaps a week ago. This is why I was so suprised when I booted the CD up.

> 
BSD and linux both have unix roots and the speed of each would depend more on the DE, services and packages they run, rather than the general 'one is faster than the other'.


yes, perhaps, they buth have UNIX roots, but none of the code in the both OS's is the same, thus, they work differently.

---

### Post by nocturn on 2005-08-11
BSD and Linux are both Unix derivates, but BSD is actually genetic Unix (sharing code with the original).  Linux was re-engineered from the ground up.

There are very major differences between the 2 systems, making it difficult to compare them (such as different filesystems etc.)

---

### Post by luca_linux on 2005-08-11
I'm currently running Ubuntu and FreeBSD in dual-boot and I really like both of them. They are really different and both of them have the pros and the cons. For example FreeBSD's sysctl is really useful, you can edit kernel parameter without rebooting, in real time; but FreeBSD hardware support is not like Linux's. Even if FreeBSD 6.0 has great improvements in this way.

---

### Post by Kimm on 2005-08-11
ok,

I'm acctually quite interested in trying out FreeBSD, but as the live CD doesnt seem to  support my graphics card atleast I think I'll wait untill I get my new computer :)

---

### Post by agger on 2005-08-11
[QUOTE=luca_linux]I'm currently running Ubuntu and FreeBSD in dual-boot and I really like both of them. They are really different and both of them have the pros and the cons. For example FreeBSD's sysctl is really useful, you can edit kernel parameter without rebooting, in real time; abut FreeBSD hardware support is not like Linux's. Even if FreeBSD 6.0 has great improvements in this way.[/QUOTE]
 My experience is - as discussed in this thread:

[http://www.ubuntuforums.org/showthread.php?t=56047](http://www.ubuntuforums.org/showthread.php?t=56047)

that FreeBSD is better on low-end hardware. With FreeBSD, I can and do run GNOME on my old IBM Aptiva 450 MHz+ 128 Megs RAM, which is not possible with Ubuntu.

FreeBSD is rather different to configure from Linux, however, but as soon as you run GNOME
you can make the user interface identical provided you can get all the same software.

The more important (very considerable - these are totally different operating systems) differences can be tucked away "under the hood" for most users, I believe.

I think it's safe to say that FreeBSD performs quite a lot better for low-end configurations, where the differences are likely to be insignificant for state-of-the-art hardware.

---

### Post by -Rick- on 2005-08-11
Things I noticed that where better for me:
- Booting is faster(FreeBSD: ~50 sec, ubuntu: 80 sec)
- Starting kde is slightly faster
- Disk IO seems a bit faster
- KDE's Arts seems to work much better.

I have to agree you really need to read the manual when upgrading the base system, updating self installed packages('ports') is quite easy though.

As for hardware support...everything works for me with 7.0-CURRENT ("Everything" is amd athlon xp 1800, 5 button PS/2 mouse, nvidia ti4800, realtek ethernet, linksys USB WLAN).
I wouldn't know about any other gfx cards...but isn't that mainly an X thing aswell?

FreeBSD works indeed OK on old hardware, my mother's comp(Celeron 400 mhz, 64 mb ram, nvidia tnt2) is running fine with freebsd.

---

### Post by az on 2005-08-11
It is different, but it is still unix based.  So the end result is that you should be able to take the source code and do 
./configure
make
make install
and you should be able to install software.  Where it gets messy is things like hardware drivers (wireless, video, usb, anything).  

As for binary updates, well there is a debian port to freebsd.  I think you can install it with the crosshurd package.  Then, when something is updated in Debian, you get it on you system - whether it is a linux or a BSD system;  it's debian.

The caveat is that the package has to build on your port, so not all packages that are in Debian are in the BSD port.

---

