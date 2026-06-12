---
title: "Optimizing Ubuntu for running from USB"
date: 2017-04-25
forum: Ubuntu/Debian BASED
---

### Post by evil_genius2 on 2017-04-25
What can I do to maximize the optimization of the operating system to work with the USB-stick? I want performance such in Puppy Linux installed on USB-stick, it's very fast on old PC. Particularly interested in loading the system into RAM and writing on demand or when logging out.

Thank you in advance.
P.S. Sorry for my English.

---

### Post by howefield on 2017-04-25
Welcome to the forums.

Thread moved to the "*Ubuntu/Debian BASED*" forum for a better fit.

---

### Post by LastDino on 2017-04-25
As I've come to know; 

1. SSD would serve much better purpose than USB stick. 

2. If you really want performance like puppy, try with lighter version of Ubuntu, like Lubuntu as it comes with little to know extra packages.

Less package less hassle.

That's probably it.

---

### Post by C.S.Cameron on 2017-04-26
When booting your persistent flash drive press Shift then F6, then Esc. After -- type <space toram>, that is:
```
 toram
```
See if that helps, (I think you need more RAM than with Puppy).

(If you made the drive with UNetbootin, I recall press F6 at the boot screen).

---

