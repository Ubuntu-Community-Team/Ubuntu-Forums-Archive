---
title: "[Elementary OS] No OS found on bootloader( assumed to be grub2)"
date: 2014-12-23
forum: Ubuntu/Debian BASED
---

### Post by zayce2 on 2014-12-23
Boot repair paste: [http://paste2.org/VmABNJdj](http://paste2.org/VmABNJdj)
Laptop model: Acer Aspire 4752G (Dual booting Win7 and elementary OS)

1)Installed elementary OS from a live USB.
2) Manually partitioned / and swap
3) Restarted and said no OS found
4) Used live USB to use boot repair
5) Boot repair said purge cancelled
6) I am sad, can't installed this for 3 days

---

### Post by slickymaster on 2014-12-23
*Moved to the ***Ubuntu/Debian BASED*** sub-forum*

---

### Post by ibjsb4 on 2014-12-24
I do not read those boot scripts well, but I do not see the bootloader either.

Since this is a fresh install, I think the easy fix is just reinstall and this time (before the install) delete both linux partitions (sda5 and sda6) with gparted on the live installer.  Note*  this will make your system un-bootable until elementary is reinstalled.

Then install and use the option to install to largest free space instead of manual partition.  It will then auto build the partitions and filesystem.

Maybe someone else will verify that I am reading the boot script right, but this is what I make of it.

---

