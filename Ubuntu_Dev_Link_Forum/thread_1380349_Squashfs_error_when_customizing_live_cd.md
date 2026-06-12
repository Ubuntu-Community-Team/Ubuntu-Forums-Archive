---
title: "Squashfs error when customizing live cd"
date: 2010-01-13
forum: Ubuntu Dev Link Forum
---

### Post by the_real_fourthdimension on 2010-01-13
Hey All

I'm following this guide to customizing a live cd: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
I get to this step:
Extract the SquashFS filesystem
```

sudo unsquashfs mnt/casper/filesystem.squashfs
sudo mv squashfs-root edit

```
And I'm told that the filesystem is too new for squashfs to support.  I'm running 9.10 and the image I'm working with is also of 9.10.  I've just updated all my programs.
If anyone knows how to solve this, I'd appreciate it.
Thanks.

---

### Post by nilarimogard on 2010-01-13
I think you will find [this]("http://www.webupd8.org/2010/01/web-based-ubuntu-and-debian-custom.html") a lot easier to use.

---

### Post by the_real_fourthdimension on 2010-01-13
Thanks a ton!  I'll give that a shot.

---

