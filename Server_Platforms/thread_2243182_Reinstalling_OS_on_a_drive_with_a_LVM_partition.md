---
title: "Reinstalling OS on a drive with a LVM partition"
date: 2014-09-07
forum: Server Platforms
---

### Post by SquALeD on 2014-09-07
Hi there

Recently had a drama with my 12.04 server which is now going to need a full reinstall of the operating system. The OS is on a partition on a 1TB disk that has the rest of the disk integrated with other disks via LVM.

When I try to reinstall Ubuntu it gives me the warning that the disc is part of a LVM group which is good as I really don't want to lose the data. I can't seem to work out how to install the OS on this disc without wiping the LVM partition. Ive tried manual partitioning and guided but no joy...

Is there an easy way to reinstall ubuntu on a disk that has an lvm partition on it?

Can anyone help?

I did search but didn't really find anything I could understand lol - apologies if there is a thread...or if someone could point me in the right direction, 

thanks a lot people in advance

---

### Post by nerdtron on 2014-09-07
The default ubuntu installer can't scan and activate LVM partitions. You need to install the LVM2 packages first.
See [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

