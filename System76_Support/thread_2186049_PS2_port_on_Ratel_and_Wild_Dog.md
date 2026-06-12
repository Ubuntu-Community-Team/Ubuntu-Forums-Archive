---
title: "PS/2 port on Ratel and Wild Dog"
date: 2013-11-05
forum: System76 Support
---

### Post by Skaperen on 2013-11-05
The image of the back ports for Ratel and Wild Dog show a single PS/2 port with dual color for both keyboard AND mouse.  How does that work?  Is a splitter provided or available?  Or does it have to be bought separately?

---

### Post by isantop on 2013-11-07
I think it works for *either* mouse or keyboard, not both at once. Older ports used to only work for one or the other, not either. 

I'd recommend USB anyway; it's much more flexible and can be hotplugged.

---

### Post by Skaperen on 2013-11-07
> **isantop said:**
> I think it works for *either* mouse or keyboard, not both at once. Older ports used to only work for one or the other, not either. 

I'd recommend USB anyway; it's much more flexible and can be hotplugged.

I didn't know about this kind of PS/2 connection until a couple days ago.  Apparently it started when laptops were cutting space needed.  But indeed it is a way to connect both keyboard and mouse at the same time.  I have a box like that here and have been using it for keyboard only.  I went to Amazon and searched for "PS/2 splitter" and found a couple of them.  I ordered the one from StarTech.  It not only works, but the boot probe is faster.

For a laptop, I'd most likely be using the integrated keyboard, but an external mouse has convenient.

For desktops, I have KVM switches based on PS/2.  A few years ago I tested USB for input and could notice the lag in the mouse actions.  That may have been due to USB 1.0 protocol operating.  I don't know if any will use faster USB.  But PS/2, though technically slow, does not lag from protocol negotiations.  So I will want PS/2 on desktops, but now I know the single connector should work.  I suggest you get one of those splitters and actually test it on your machines so the support department will know.

PS/2 hot plugs just fine.  There is a slight risk to hotplugging PS/2.  If the contacting of the pins generates noise that looks like a keyboard power off button sequence, it may power off the computer (if the motherboard chipset implements it ... probably most still do).  And yes, I have had it happen, once (out of a thousands of replug actions I've done on PS/2).

---

