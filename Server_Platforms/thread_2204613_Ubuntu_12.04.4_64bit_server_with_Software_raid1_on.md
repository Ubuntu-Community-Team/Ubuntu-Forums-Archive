---
title: "Ubuntu 12.04.4 64bit server with Software raid1 on a UEFI bios for NAS (02-09-2014)"
date: 2014-02-09
forum: Server Platforms
---

### Post by george28 on 2014-02-09
This post is for everybody who is struggling to set up the new ubuntu server with software raid on a new machine with UEFI based boot style for NAS purposes.

My issue was:
After installing ubuntu I get stuck at a very simplified version of a GRUB prompt, not being able to boot into the server.

Solution:
I tried everything to set it up with UEFI without luck. You have to turn off UEFI in your bios and choose legacy boot. In my bios I have two different settings I had to change.
Then boot up and from the boot menu select legacy boot from DVD drive. You will see that the ubuntu installer looks different from when you tried installing it with UEFI.
When you get to the partitioning part this is what I recommend: select the first hard drive and get rid of all existing partitions. The easiest way is to set up a new partition table by selecting the header and answering yes. Do this for the second hard drive as well. Once done, create 4 partitions on both hard drive. You don't need this many but this is my setup. BOOT, SWAP, ROOT, HOME. The easiest way to find out what size swap partition you need is to select free space and choose auto partition it and then you can see the size . Then you can delete all partitions again. So create a 250MB partition first. Then the suggested size swap. Then 10 GB for root and finally the rest of the space for home. Do it identically for both. Then select Configure software raid. In there accept default values and choose raid 1 if you want mirroring. Create raid arrays for matching partitions. So sda1 with sdb1 , sda2 with sdb2, etc. Select proper filesystem and mount points for newly created raid partitions. Once again: 250MB Boot with ext4 filesystem, 4.2GB (or else) swap with swap designation, 10 GB root with ext4, and the rest space for home with ext4. Say finish and continue installation in a regular way. Everything should be fine now.

---

