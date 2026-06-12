---
title: "[SOLVED]Issue with performing fsck on LVM"
date: 2011-06-02
forum: Server Platforms
---

### Post by hawk2010 on 2011-06-02
Hi all,

I'm on Ubuntu 10.04 Server LTS and got three VG's that requires to run fsck. I know that you have to perform fsck on single user mode by removing quiet and adding

init=/bin/bash rw to the end. But then again when I type mount my vg's are mounted. How can I get the vg's not to get mounted so i can do the fsck on the vg.

Thanks

SOLVED IT

On grub i pressed "e" and  removed quiet and then included init=/bin/bash rw


then I umounted the root and the var VG's and type fsck -fy /dev/mapper/lvxxxx

---

