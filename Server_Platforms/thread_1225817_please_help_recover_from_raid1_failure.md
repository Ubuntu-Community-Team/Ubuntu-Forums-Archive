---
title: "please help recover from raid1 failure"
date: 2009-07-29
forum: Server Platforms
---

### Post by dbutcher on 2009-07-29
Hi all,
I could really use some guidance on this problem.
I have a server running 6.06LTS.  There are 2 300GB Sata hard-drives (sda and sdb), with 3 partitions on each drive.  The partitions are mirrored as raid1 as follows:
sda1 + sdb1 = md0 = /boot (ext3)
sda2 + sdb2 = md1 = none (swap)
sda3 + sdb3 = md2 = / (ext3)

Recently, sda failed and I set out to replace it using the following tutorial: [http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array]("http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array")

However, after removing sda from the array, and replacing it with a new drive, I am unable to boot.  My system hangs on the splash screen at the step "mounting the root filesytem"

I can only get the system to boot by reinstalling the defective drive, even though I do not reconfigure it back into the raid array.

As of right now, my server is running.  But no raid protection, and the remaining good drive is the same vintage as the one that failed.

Any advice on how I should proceed?

Cheers,
Dave

---

### Post by samosamo on 2009-07-29
I looked at the tutorial you used and they left out the steps required to fix a BOOTABLE raid1.  Basically you need to install grub on the second hard drive.  Try reading about "bootable raid1 with grub"

Also, I want to mention that if it is an Intel controller, you must set the boot flag on the partition that has /boot (yep, Windows style).  This drove me crazy for years before I stumbled across this tip.  It probably doesn't affect you but I just want to spread the word.

---

### Post by dbutcher on 2009-08-02
Thanks samosamo.

I'm assuming that grub is already installed on the good drive, since the grub menu appears after a reboot.  However, all the options within grub refer to the raided partitions (root=/dev/md2) rather than the stand-alone (root=/dev/sdb3).  Do I need to change this?

As per my first post, I have removed sda from the active raid, following the instructions in the tutorial I referenced.  I thought this process went smoothly, but I'm confused by the results I'm seeing now:

```
dbutcher@linux07dec05:~$ cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 dm-0[1]
      292439104 blocks [2/1] [_U]

md1 : active raid1 sdb3[1]
      292439104 blocks [2/1] [_U]

md0 : active raid1 sdb1[1]
      96256 blocks [2/1] [_U]

unused devices: <none>
```

For md2, I thought it would show sdb2.  What is dm-0?


Thanks also for your clue about the boot flag.  I *do* have an intel controller, so I'm just looking into the flag option now.

Cheers,
Dave

---

### Post by samosamo on 2009-08-06
Yes, one of the changes you will have to make is "root=/dev/mdX" in the grub conf.  That's not all though.

dm-0 indicates a LVM volume.  I'm not sure how you managed that.  I have never used LVM so I can't help you further but at least you have something to google.

---

