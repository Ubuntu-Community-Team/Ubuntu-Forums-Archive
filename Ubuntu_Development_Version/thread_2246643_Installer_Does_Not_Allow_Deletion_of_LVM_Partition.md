---
title: "Installer Does Not Allow Deletion of LVM Partitions"
date: 2014-10-02
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2014-10-02
I did an install of today's daily on a Fedora system that had used LVM.  The installer ('Something Else') would not let me delete or otherwise manipulate the LVM entries, which were grayed out. 

I used parted to remove them and rebooted the install image. Gparted through errors and complained.

Something new? Or, something that's been around for a while?

---

### Post by jerrylamos on 2014-10-04
On development ubuntu's, I do Not trust install's partition manipulation.  I've a Win7 hard drive as well and have bruises from install and grub screwing up the wrong hard drive and wrong partition.

I invariably use Gparted to work with partitions and then just choose whichever (of many) for the installer.

---

