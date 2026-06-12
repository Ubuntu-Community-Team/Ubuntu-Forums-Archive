---
title: "Recovering a mdadm raid after a stupid mistake"
date: 2013-01-30
forum: Server Platforms
---

### Post by acontant on 2013-01-30
Hi everyone

I have a raid 1 on my server looking like this:

md0 /boot on sda1 and sdb1
md1 swap  on sda2 and sdb2
md2 /     on sda3 and sdb3

Yesterday, sdb failed and I replace it with a new disc with no part at all. Like always, I previously ran a **dd if=/dev/zero of=/dev/sdb count=1 bs=512** on the new disk just to make sure it was with no part at all on another machine.

My first mistake is because I was too lazy to partition the new disk and add it to the raid I simply did **dd if=/dev/sda of=/dev/sdb count=1 bs=512**.I know this is risky since I'M cloning the part and the superblock but I did this 5 or 6 time in the pas with no problem at all.

My second mistake is what killed the raid. Instead of attaching sdb right away **(mdadm /dev/mdX -a /dev/sdbY)**, I rebooted the machine. The system got all mixed up and booted but it's booting on sda mainly but cat /proc/mdstat show that my raid is clean.... on sdb. Impossible to attach sda anymore, says device is busy. Worst, if i try to reboot the machine while sdb is remove, it won't boot because sda is mounted in read only and fail booting rigth after the warning.

Is there a way to force mdadm to boot on sda and not sdb ? changing a UUID in mdadm.conf or something ? 

Thank you very much!

---

### Post by SaturnusDJ on 2013-01-31
> **acontant said:**
> Hi everyone

I have a raid 1 on my server looking like this:

md0 /boot on sda1 and sdb1
md1 swap  on sda2 and sdb2
md2 /     on sda3 and sdb3

Yesterday, sdb failed and I replace it with a new disc with no part at all. Like always, I previously ran a **dd if=/dev/zero of=/dev/sdb count=1 bs=512** on the new disk just to make sure it was with no part at all on another machine.

My first mistake is because I was too lazy to partition the new disk and add it to the raid I simply did **dd if=/dev/sda of=/dev/sdb count=1 bs=512**.I know this is risky since I'M cloning the part and the superblock but I did this 5 or 6 time in the pas with no problem at all.

I've done this before also, no problem, but that might have been because I didn't boot in between.
Did you check the partitions where the same?
I found out I need to do more in order to have the partition layout mirrored. Part 1, step 1 @ [http://ubuntuforums.org/showthread.php?t=1636977](http://ubuntuforums.org/showthread.php?t=1636977)

> 
My second mistake is what killed the raid. Instead of attaching sdb right away **(mdadm /dev/mdX -a /dev/sdbY)**, I rebooted the machine. The system got all mixed up and booted but it's booting on sda mainly but cat /proc/mdstat show that my raid is clean.... on sdb. Impossible to attach sda anymore, says device is busy. Worst, if i try to reboot the machine while sdb is remove, it won't boot because sda is mounted in read only and fail booting rigth after the warning.

Is there a way to force mdadm to boot on sda and not sdb ? changing a UUID in mdadm.conf or something ? 

Thank you very much!

Best thing to do is use a live cd.Ccarefully look how to get the array back in sync, then fix the configuration files using chroot.

---

### Post by acontant on 2013-02-06
Hi SaturnusDJ

Thank you for your answer. I'll try it out but I was not able to go on site yet. I had another idea. I'll try adding a third disk since mdadm think there is only sdb on the mirror. I think it might worth to try to add sbc to the mirror and then, once the rebuild is complete, remove sda and sdb and boot only to sdc. If it's working, I'll be able to only add one disk back to the mirror. 

If this solution fail, I'll go with the live CD option.

I'm pretty sure the dd is not what caused the error, because it worked in the past for me as well. I'm pretty sure the reboot was the real mistake here...

Have a nice one

---

### Post by darkod on 2013-02-06
That's why you should NEVER be lazy, especially when we are talking about spending 5mins to create new partitions. There are tutorials to copy partition table with sfdisk but I wouldn't even do this.

Print the list of partitions of sda with parted, and create the same or similar on sdb. You need like 3mins having all data in front of you. Not you'll spend much more time trying to sort this out, plus your data is in danger.

Copying can often go wrong especially because of UUIDs.

I wonder if you zero the MBR on sdb again, will that make the system run fine degraded with only sda. After all, sda is fine including partition table and UUID. It should work with only sda.

Trying to use sda in read-only seems to be creating the issue, but you can always work in live mode, or try to remount as read-write. You can try working from live mode, creating a new blank partition table on sdb, creating the partitions, and try to add them to mdadm.

---

