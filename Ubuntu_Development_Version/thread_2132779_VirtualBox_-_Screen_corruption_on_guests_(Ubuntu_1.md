---
title: "VirtualBox - Screen corruption on guests (Ubuntu 12.04, Win 7) -Intel sandy brige"
date: 2013-04-05
forum: Ubuntu Development Version
---

### Post by den_ on 2013-04-05
Hi,

I updated to 13.04 a couple of hours ago, and I am still trying to find some kind of solution to above mentioned problem. I had such problems before, but never with Ubuntu guest. 

I have tried everything what came to my mind, from recompiling guets additions, reinstalling VirtualBox from offical site and repositories, using xorg-edgers etc...

I have noticed some change in behaviour (less corruption, but it happens) when I put this:

Section "Device"
        Identifier "intel"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSection

in hosts (13.04) xorg.conf 

Does anyone has a solution or a suggestion for this problem?

If you need some more info, just say it...

Thanks

---

### Post by den_ on 2013-04-06
Couldn't figure out how to edit the subject. This is SOLVED.

It looks like some KDE libs were responsible for the problem. After I removed (complete remove with Synaptic.) nepomuk, and some nepomuk stuff (left over after playing with KDE a long time ago.) and bunch of kde libs. Unfortunatelly I am not sure what exactly was the reason, but I found in VirtualBox forums a similiar issue where QT was causing it...

Njaga njaga

---

### Post by den_ on 2013-04-06
No I was wrong, the corruption has nothing to do with QT or KDE, it is because of SNA. The reason why I didn't undertsand that immediately is because I had only restarded X, and for some reason a reboot is required.

So setting AccelMethod to uxa and rebooting solves this.

---

