---
title: "[IDEA] Same disc text-mode install"
date: 2007-12-01
forum: Ubuntu Brainstorm
---

### Post by phrostbyte on 2007-12-01
Instead of having an alternate disc, how about have an option on the initial Ubuntu boot menu:

[Ubuntu Logo]

Start or install Ubuntu
Text-mode install
Check CD integrity
Memory test
Boot from first hard disc

Choose text-mode install will launch a debian-like text mode installer.

This has the advantage of not requiring separate LiveCD and alternate install discs.

---

### Post by smartboyathome on 2007-12-01
The downside to this is that the alternate cd uses packages included with it to install Ubuntu, while the livecd just copies the system from the CD. There definately wouldn't be enough room for both (especially since both are full CDs, anyway).

---

### Post by nitestick on 2008-01-02
i'm no dev but surely a text mode installer could be created/reworked to install from the live filesystem rather than from packages? if i had the know how i'd definitely give it a crack but i just don't.

---

### Post by smartboyathome on 2008-01-02
> **nitestick said:**
> i'm no dev but surely a text mode installer could be created/reworked to install from the live filesystem rather than from packages? if i had the know how i'd definitely give it a crack but i just don't.

I don't know if it can, but it would have to mount the squashfs filesystem (which isn't all that convienient with it). I would say leave it as it is now (the disk DOES have safe graphics mode, if that doesn't work, then I guess you will have to use the alternate cd). Personally, I think the way the alternate CD does it is good (reduces space so you can have more packages), but a graphical interface for it would be nice. :)

---

### Post by FuturePilot on 2008-01-02
I think there's something like this. If you press F6 at the initial screen and add
```
only-ubiquity
```
to the end of the line it will boot into the installer only.

---

