---
title: "OK I am trying FreeBSD out on my EM64T dual-core computer"
date: 2006-06-05
forum: The Cafe
---

### Post by RAV TUX on 2006-06-05
so I burned 3 CD's of the latest stable release

6.1 

2 intstall CD's 

1 CD titled "Boot Only"

my question is: is the "Boot Only" CD like a linux "Live" CD or Ubuntu "Desktop" CD?

---

### Post by RAV TUX on 2006-06-05
[quote=yozef]so I burned 3 CD's of the latest stable release

6.1 

2 intstall CD's 

1 CD titled "Boot Only"

my question is: is the "Boot Only" CD like a linux "Live" CD or Ubuntu "Desktop" CD?[/quote]

What is even more confusing is the Gentoo CD I just burned:

Titled "Live CD i686 installer 2006.0"

---

### Post by drogoh on 2006-06-05
[QUOTE=yozef]so I burned 3 CD's of the latest stable release

6.1 

2 intstall CD's 

1 CD titled "Boot Only"

my question is: is the "Boot Only" CD like a linux "Live" CD or Ubuntu "Desktop" CD?[/QUOTE]

There is only one ISO you really need.  "disk1" is the installer with some packages to get you going.  "bootonly" will boot you into the installer and that's it, only good if you're doing a net install.  "disk2" is just KDE/Gnome packages.  You don't really need disk2 because the packages are now out of date and you can install them from ports anyway.

---

### Post by RAV TUX on 2006-06-05
[quote=drogoh]There is only one ISO you really need.  "disk1" is the installer with some packages to get you going.  "bootonly" will boot you into the installer and that's it, only good if you're doing a net install.  "disk2" is just KDE/Gnome packages.  You don't really need disk2 because the packages are now out of date and you can install them from ports anyway.[/quote]

thanks for the reply so if I just want to give it a try I should use the "boot only" CD.

---

### Post by drogoh on 2006-06-05
[QUOTE=yozef]thanks for the reply so if I just want to give it a try I should use the "boot only" CD.[/QUOTE]

No, my recommendation is "disk1".  It has everything you need to get up and running without requiring a network connection during install.

---

### Post by RAV TUX on 2006-06-05
[quote=drogoh]No, my recommendation is "disk1".  It has everything you need to get up and running without requiring a network connection during install.[/quote]

But I don't want to do an Install I just want a live CD?

---

### Post by briancurtin on 2006-06-05
im pretty sure the sites of both gentoo and freebsd cover this information...

---

### Post by RAV TUX on 2006-06-06
[quote=yozef]What is even more confusing is the Gentoo CD I just burned:

Titled "Live CD i686 installer 2006.0"[/quote]

I'm using the Gentoo live CD with success.

---

### Post by jdong on 2006-06-06
[QUOTE=yozef]But I don't want to do an Install I just want a live CD?[/QUOTE]

FreeBSD does not have any official LiveCD's, at least with any more than /bin/sh and a few other commands :).

If you love sitting at a terminal using ancient implementations (kidding, relax) of Linux commands, try recovery mode on disc1.

Else, look at PC-BSD, DesktopBSD, Frenzie, or FreeSBIE, all of which are liveCD's based on customized FreeBSD. No, FreeBSD does not look like any of these distributions out-of-the-box, but it gets you a look at FreeBSD :)

---

### Post by RAV TUX on 2006-06-06
[quote=jdong]FreeBSD does not have any official LiveCD's, at least with any more than /bin/sh and a few other commands :).

If you love sitting at a terminal using ancient implementations (kidding, relax) of Linux commands, try recovery mode on disc1.

Else, look at PC-BSD, DesktopBSD, Frenzie, or FreeSBIE, all of which are liveCD's based on customized FreeBSD. No, FreeBSD does not look like any of these distributions out-of-the-box, but it gets you a look at FreeBSD :)[/quote]

I've tried PC-BSD in the recent past very impressive if you like a KDE desktop.

---

### Post by bluevoodoo1 on 2006-06-06
[QUOTE=jdong]If you love sitting at a terminal using ancient implementations (kidding, relax) of Linux commands, try recovery mode on disc1[/QUOTE]

HAHAHA! I've just spent some time today [trying] to set up FreeBSD with VMware, and then I ran out of room. But you are very correct--it's quite archaic,.

---

### Post by azazel- on 2006-06-07
DesktopBSD is much better than PC-BSD in the long run.

---

### Post by jdong on 2006-06-07
[QUOTE=bluevoodoo1]HAHAHA! I've just spent some time today [trying] to set up FreeBSD with VMware, and then I ran out of room. But you are very correct--it's quite archaic,.[/QUOTE]

I did not appreciate how easy to use the Linux CLI was until I set up my first BSD box.

---

