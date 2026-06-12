---
title: "sfill still crashes with glibc."
date: 2010-03-01
forum: Security
---

### Post by Krovas on 2010-03-01
I'm trying to wipe an old thumb drive down for later sale, but sfill always eventually explodes:

```
Creating /media/disk/oooooooo.ooo ... **************************************
 Wiping inodes ...*** glibc detected ***
 sfill: free(): invalid next size (fast): 0x0000000000609450 ***
Aborted

```

Is there an updated version of sfill, or an alternative blank-space wiping utility available?

---

### Post by rookcifer on 2010-03-01
Just use shred.  It works fine for wiping whole drives.

```
sudo shred -vfz /media/disk
```

---

### Post by FuturePilot on 2010-03-01
Looks like it's a bug that's been around for awhile [https://bugs.launchpad.net/ubuntu/+source/secure-delete/+bug/327114]("https://bugs.launchpad.net/ubuntu/+source/secure-delete/+bug/327114")

> **rookcifer said:**
> Just use shred.  It works fine for wiping whole drives.

```
sudo shred -vfz /media/disk
```

Except shred destroys data. Sfill overwrites free space as to securely erase any previously un-securely deleted files.

---

### Post by mkvnmtr on 2010-03-01
I have used sfill quite a bit with out that problem. I use -v which you must have used and also -l. That just uses wipe to make two passes. That is enough to delete everything. It still takes a very long time. Maybe trying to wipe 35 times is what is giving you the error.

---

