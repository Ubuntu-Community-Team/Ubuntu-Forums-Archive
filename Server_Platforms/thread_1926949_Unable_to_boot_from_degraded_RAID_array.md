---
title: "Unable to boot from degraded RAID array?"
date: 2012-02-17
forum: Server Platforms
---

### Post by sailor420 on 2012-02-17
I have a home server running 10.04 configured with an mdadm-based RAID array. The boot and /home partitions are both on RAID-1 arrays, and I have a large data partition on RAID-5. There are three disks, with a partition from each disk making up each mdadm array--so three arrays (two RAID-1, one RAID-5), each with three disks, /dev/sda, sdb, and sdc.

Recently, /dev/sda failed, and mdadm kicked it out of the array correctly. I replaced the drive, and am now trying to boot, but when I do, I get an error "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key." It seems that this is likely a message from my ASUS BIOS.

It seems to me that this is likely due to a missing boot loader. Am I correct in this? I'm guessing that since /dev/sda is likely what the system is trying to boot off of and since it is now a blank drive until I can boot to rebuild the array, that the machine can't boot. Oddly, I swear I remember installing GRUB to all of the disks and making sure they were bootable.

I'm tempted to change the boot order in the BIOS and see if that works, but I'm worried that doing this might somehow corrupt the now degraded RAID-5 partition (not sure why... but I'd rather not do something I don't fully understand the implications of).

How should I go about fixing this? Any help is greatly appreciated.

---

### Post by pgf1234 on 2012-02-17
It sounds like the new drive did not sync properly. You could try booting with something like Clonzilla and cloning the good drive onto the new one.

---

### Post by sailor420 on 2012-02-17
Thanks. Guess I should clarify a bit--the new drive is totally bare, there is nothing on it. I literally put it in the machine with the intention of formatting, partitioning, and then adding to the array, but after physically installing the disk and booting, it won't boot.

---

### Post by sailor420 on 2012-02-18
Marking this solved--looks like the issue was simply the BIOS not properly failing over to the second drive. Manually forced it, then repaired the RAID array and reinstalled GRUB to sda.

Thanks!

---

