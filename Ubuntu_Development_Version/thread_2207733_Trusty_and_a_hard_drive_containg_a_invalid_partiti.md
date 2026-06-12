---
title: "Trusty and a hard drive containg a invalid partition table"
date: 2014-02-25
forum: Ubuntu Development Version
---

### Post by Eromatic on 2014-02-25
If you have a hard drive that shows up under "sudo fdisk -l" as not containing a valid partition table, have you been able to live boot (through USB Flash) into Trusty with that hard drive connected to your computer? The current state of Trusty seems to have it that if your hard drive does not contain a valid partition table, that then you may not be able to install or try Ubuntu while that hard drive is connected to the computer. The user will instead be dropped into a initramfs busybox prompt with no suggested course of action.

This although being a known bug (perhaps only to the affected users), the issue has been around since Ubuntu 13.10. That bug report and other details on it can be found at: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1241589)

However, I see this as a show stopper for the LTS release as that this bug can prevent the normal install of Ubuntu for any of the affected users. There doesn't seem to be any "safe" working solution for a user to workaround this issue other than having to remove the affected hard drive from the computer. Granted though, I could imagine that such a workaround in having to physically remove the hard drive would be more of a chore for a laptop user to do, assuming that the drive is even removable at all. In then that later case where the drive is not removable, you would then have no choice but to start messing around with the partition on that affected hard drive. And should the course of action be determined to remove the affected hard drive from the computer, one must also take note in doing so could void any computer manufacturer warranty.


**TL;DR**

-The live USB install of Trusty should fail if the computer contains a hard drive without a valid partition table as seen by "sudo fdisk -l".
-Workarounds require either the physical removal of the affected hard drive, or to mess around with the hard drive partition in thus potentially destroying data.
-The issue has been around since the stable release 13.10.

---

