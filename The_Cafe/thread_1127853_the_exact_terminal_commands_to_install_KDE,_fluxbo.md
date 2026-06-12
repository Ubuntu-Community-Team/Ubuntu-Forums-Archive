---
title: "the exact terminal commands to install KDE, fluxbox, or GNOME on freebsd"
date: 2009-04-16
forum: The Cafe
---

### Post by Dustin2128 on 2009-04-16
what are they? I'm a complete noob to freebsd, so just say exactly what I have to punch in

---

### Post by chucky chuckaluck on 2009-04-16
you might want to try a freebsd forum.

---

### Post by rucadulu on 2009-04-16
Switch to PC-BSD it is based on freeBSD but much easier to learn and use.

---

### Post by yabbadabbadont on 2009-04-16
[http://www.freebsdmadeeasy.com/tutorials/freebsd/set-up-xorg-on-freebsd.php](http://www.freebsdmadeeasy.com/tutorials/freebsd/set-up-xorg-on-freebsd.php)

Someone needs to learn how to use Google...  :P :D

---

### Post by init1 on 2009-04-17
> **yabbadabbadont said:**
> [http://www.freebsdmadeeasy.com/tutorials/freebsd/set-up-xorg-on-freebsd.php](http://www.freebsdmadeeasy.com/tutorials/freebsd/set-up-xorg-on-freebsd.php)

Someone needs to learn how to use Google...  :P :D

Google isn't always a good alternative to experience though. 
I think he's looking for instructions on FreeBSD's package manager.

---

### Post by yabbadabbadont on 2009-04-17
> **init1 said:**
> Google isn't always a good alternative to experience though. 
I think he's looking for instructions on FreeBSD's package manager.

The tutorial to which I linked gives the proper commands to use ports.  (which is the only package manager one should use on a BSD system... ;))

---

### Post by Skripka on 2009-04-17
> **chucky chuckaluck said:**
> you might want to try a freebsd forum.

Or come on O'er to nOOST.

---

### Post by Methuselah on 2009-04-17
IIRC

cd /usr/ports/x11-wm/fluxbox
make install clean

builds from source, assuming you installed the ports collection.
If not you'd have to use portsnap first.

Alternatively:

pkg_add -r fluxbox

installs a binary package

After that you have to add a exec /usr/bin/fluxbox to your .xinitrc after which fluxbox will be used when you invoke startx.

It's a while since I've done it but the above is generally correct.
Unlike most linux distributions FreeBSD has a huge and rather extensive online handbook.
That's part of the reason I learned it first despite the fact that you have to do more configuration to get to a desktop.

Here's the section on Desktop environments:
[http://www.freebsd.org/doc/en/books/handbook/x11-wm.html](http://www.freebsd.org/doc/en/books/handbook/x11-wm.html)

---

