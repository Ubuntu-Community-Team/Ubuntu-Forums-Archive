---
title: "ppc issue"
date: 2005-02-13
forum: Ubuntu Backports
---

### Post by TravisNewman on 2005-02-13
Hey, when trying to use the backports on my mac, apt-get update gets 404'd on any backport repository, because it's trying to download

.... binary-powerpc/Packages.gz

when on your server it's actually

binary-ppc/Packages.gz

Is there anything you can do to fix this? I'd like to get freenx, and the kanotix repository doesn't have all the necessary mac packages.

---

### Post by rufius on 2005-02-13
[QUOTE=panickedthumb]Hey, when trying to use the backports on my mac, apt-get update gets 404'd on any backport repository, because it's trying to download

.... binary-powerpc/Packages.gz

when on your server it's actually

binary-ppc/Packages.gz

Is there anything you can do to fix this? I'd like to get freenx, and the kanotix repository doesn't have all the necessary mac packages.[/QUOTE]
 I'll let John know about it. Though I wasn't aware we had any backported packages for ppc?

---

### Post by jdong on 2005-02-13
Guess I shouldn't assume.... I'll fix that right now

---

### Post by jdong on 2005-02-13
Fixed.

---

