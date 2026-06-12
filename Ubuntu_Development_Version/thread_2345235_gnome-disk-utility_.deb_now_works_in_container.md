---
title: "gnome-disk-utility .deb now works in container"
date: 2016-12-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-12-02
A really weird thing... the devs said gnome-disk-utility would not work in containers as an xapp but it installed and is working. I noticed another starnge thing in that 'disks' has installed 'snaps' listed as loop devices.

It also detected USB as Device Block but cannot read the main data partition. maybe this can relate to bug I filed with unity8 not be able to read data from USB sticks.

to mods:

Please let this one ride. It may be a dupe of another bug I already filed but I am not sure at this point.

---

### Post by mc4man on 2016-12-02
Working would appear to be a bit of a misnomer. 

In the matter of snaps, loop device is correct.

---

### Post by ventrical on 2016-12-02
> **mc4man said:**
> Working would appear to be a bit of a misnomer. 

In the matter of snaps, loop device is correct.

uh... :) .. it is "appearing" then.

---

