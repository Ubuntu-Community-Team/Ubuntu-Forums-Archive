---
title: "HDD detected in Wine, but not Ubuntu"
date: 2010-03-07
forum: Wine
---

### Post by Bill D on 2010-03-07
Hello, I am running Ubuntu 9.10x64 on an external hard drive. I have Windows 7 x64 installed on a 320 GB internal SATA drive. I want to access the internal drive via Ubuntu, but it doesn't show up anywhere, except under Wine "Browse C:\ Drive". I find this very peculiar as my computer is less than a year old. Has anybody else had any problems like this one?
-Bill

---

### Post by gsmanners on 2010-03-07
I think you're confusing the Wine "C:" drive with your device. Wine doesn't use actual Windows installs (very much discouraged), but rather makes a new folder in your home partition.

---

### Post by Bill D on 2010-03-07
That may be possible, but I used a computer in the local shop to format the new hdd into C:\ and Z:\ partitions, and put the HDD back into my laptop...both of which show up in wine including all Windows programs installed to the C:\ drive. The HDD does not show up under Places or in the /media folder.

---

### Post by gsmanners on 2010-03-08
Wine cannot use a drive that isn't mounted for Linux.

---

