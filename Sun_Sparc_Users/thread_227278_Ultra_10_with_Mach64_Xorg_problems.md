---
title: "Ultra 10 with Mach64 Xorg problems"
date: 2006-08-01
forum: Sun Sparc Users
---

### Post by Nostalos on 2006-08-01
After browsing through the forums, I did not find any others with similar issues so hoping someone might have an idea.

I currently have Ubuntu installed on my Ultra 10 (OBP_3.31.0,POST_3.1.0,OBDIAG_P2.9).  It took me some time to work through the install issue of not getting past the "Booting Linux" screen with the Creator3D card enabled.  To work around this I set the ATI Mach64 as the screen alias within nvram and have an up and running system.


My problem now is X on this box.  I have xubuntu-desktop installed and configured, however when using "startx"  or gdm  the system completely freezes, and I am at a lose as to explain why.  And when I say freeze, I mean a hard freeze.  The kernel locks and there is not response from the machine even on the network and have to power cycle.

Has anyone else encountered this?

---

### Post by choffee on 2006-08-15
It may be on no help but I have the same problem!

I don't really know what to do next, but I have logged a bug

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/56427](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/56427)

I will add some more info when I get a chance to put the box on the network.

Feel free to add you input there.

---

### Post by fajensen on 2006-08-23
You sure that be a Mach 64 card? 

lspci on my box says:

VGA compatible controller: ATI Technologies Inc 3D Rage Pro 215GP (                   
rev 5c)

---

### Post by netced on 2006-08-28
Same problem here on a U5 (440MHz, 512MB RAM, OBP 3.29). It is written "Rage pro turbo pci" on the video ship, lspci gives the same as Fajensen (the mainboard is a 375-0115, I have an old 375-0009 and the ship is different: "3D Rage II+DVD", maybe this is the reason why some U5/10 work and some other don't). Everything is OK till I try to install either xubuntu-desktop or kubuntu-desktop  (I tried both, each on a fresh install). The system hard-freeze once X is launched.

I think it's coming from Xorg since XFree worked like a charm on Debian with nearly the same configuration file...

---

### Post by netced on 2006-08-28
The bad new is that this problem is exactly the same on Debian Etch, I checked it and saw some discussions about it... No solution for the moment... ](*,) 

I tried to put another video card (a jurassik Matrox Mystique !), without more success (it has been detected, just not configured on the right PCI slot in xorg.conf, but after correcting this the system still hard-freeze when starting X). But on that point I'm not sure if I made it correctly. Does anyone put another video card (I mean not an offical Sun one) in his/her U5/10 and can explain me how to do this in the right way ?

---

### Post by Delta_Farce on 2006-08-29
Hi guys,

Have you tried the fix suggested [in this thread?]("http://ubuntuforums.org/showthread.php?t=233481")

It worked on my Sunblade 150 which runs on a Mach64. It has run kubuntu-desktop and now xubuntu-desktop.

Cheers,

Mark

---

