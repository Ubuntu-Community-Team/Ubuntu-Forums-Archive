---
title: "Will a logical volume survive an OS reinstall?"
date: 2007-03-16
forum: Server Platforms
---

### Post by raexis on 2007-03-16
Supplemental data...
OS: Ubuntu Server 6.10 "Edgy Eft"

/dev/sda --> 200gb --> contains the OS

/dev/sdb --> 320gb --> storage drive, part 1 of logical volume
/dev/sdc --> 320gb --> storage drive, part 2 of logical volume, identical hardware to /dev/sdb

If I need to reload the OS, can I simply disconnect the drives containing the logical volume from the motherboard then reinstall the OS on /dev/sda, then reconnect the 2x320gb drives and expect the logical volume to be intact and useable? (factoring in a small bit of fstab foo naturally)

Thanks ~ Raexis

---

### Post by arsya on 2007-03-16
Hi,

I think during installation of the OS (Linux), it would detect pre-existing filesystem (including Logical Volume). If I'm not mistaken, I had this experience when I was playing with RedHat (RHEL 4). During installation, when you choose manually setup partition, it detect existing filesystem so you could choose which one to be reformatted and which one to be skipped (leave as it is).
It was sometimes ago, so I can not guarantee it's like that.
My suggestion is, you could tried to boot from the Linux installation CD, follow the step until the part for setup/manage partition. You could see whether it detect your Logical Volume or not. If it detects, you have to make sure you leave it as it is.
I am quite sure the Linux Installation will not write any changes within this part for manage partition, until you choose to save the change that you've made.

Hope it helps.

---

