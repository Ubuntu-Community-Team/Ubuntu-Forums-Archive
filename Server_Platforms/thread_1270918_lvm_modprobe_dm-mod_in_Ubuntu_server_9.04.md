---
title: "lvm modprobe dm-mod in Ubuntu server 9.04"
date: 2009-09-20
forum: Server Platforms
---

### Post by ene_dene on 2009-09-20
I've installed ubuntu server 9.04. And recently added two more disks, I formated them in to use for LVM.
However when I follow the instructions how to setup these two disks to lvm I need to enable this module:
```
lvm modprobe dm-mod
```
which results in:
```
FATAL: Module dm_mod not found.
```
Is there a fix for this, or is there a new method for this version of ubuntu?

---

### Post by ene_dene on 2009-09-20
Curious, I didn't need that module after all... Sorry for bother.

---

### Post by zivley on 2009-11-05
That's because since 9.04 the module is built INTO the kernel so no need to load it

---

