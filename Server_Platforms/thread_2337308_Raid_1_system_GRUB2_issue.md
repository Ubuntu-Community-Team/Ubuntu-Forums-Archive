---
title: "Raid 1 system GRUB2 issue"
date: 2016-09-16
forum: Server Platforms
---

### Post by Leechpool on 2016-09-16
Hi,
My main desktop/server has two drives a and b.
Raid 1 is configured on them (i.e. mirrored). There are three Raid partitions md0, md1 and md2 containing Ubuntu 12.04, data and swap. So system is on a Raid partition.
mdadm informed me all three of the a drive partitions had failed.
I ran CLI query to check grub was present in mbr of a and b, finding that it was. (It basically dumped the mbr through a pipe to a grep looking for “grub” and found it in both cases).
I believe it is GRUB2.
I slid in a new drive in slot c and copied mbr and partition table from a to c.
I slid in a new drive in slot d and copied mbr and partition table from b to d.
I removed a from raid in software. I added c and let it finish syncing. I added d. It appeared as spare. I grew the raid to 3 drives (all mirrored) and d synced ok. So I now have three identical drives (as in Raid 1).
I shut the machine down.
I removed a from case.
It rebooted ok. (all drives had changes letter reference but it all was ok)
I shut it down.
Then I tried removing b as well (the old still working drive), hoping it would boot into degraded raid without b present i.e using only new drives c and d, after which I wanted to “grow” the raid back down to 2 drives. Thus ending up with two new drives in Raid 1.
However, wherever the new drives are in the machine it wouldn’t boot. Just hung with flashing cursor. I assume this means something is wrong with grub (i.e. it’s not even loading, no menu, nothing).
I thought copying the mbr from the original drive(s) and then having it sync as part of the adding-to-raid process would effectively install grub. But I think there must be something in grub which points to the UUID of the drive or something such that this isn’t sufficient?
I've found two Ubuntu guidance pages which give conflicting advice about installing grub in Raid arrays.
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html]("https://help.ubuntu.com/lts/serverguide/advanced-installation.html")
and 
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

One says you need to grub-install /dev/sdc and grub-install /dev/sdd such that grub gets installed on all devices. But I don't understand this because doesn't grub affect mbr and /boot...and /boot is on raid partition so will affect all physical drives etc.
The other says you need to grub-install /dev/md0 or other appropriate raid partition, but I thought grub was (generally) installed to a drive not a partition.

By putting back in the original and still working drive b, the system boots ok and reports 3 active and synced Raid 1 drives but I'm not sure how to get the system to boot from just the new drives.

Any help or advice would be appreciated. :)

thanks

---

### Post by oldfred on 2016-09-16
Moving to Server sub-forum, where those who know RAID may be able to help.

Do not know RAID, but familiar with grub. Different types of RAID work differently & I do not understand all the differences.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by darkod on 2016-09-16
Yes, grub (as most bootloaders) is installed on the MBR of the disks. DO NOT install it on the SW arrays.

I am not sure it can work by copying the MBRs. You should have simply installed it with sudo grub-install /dev/sdc and sudo grub-install /dev/sdd. You have a working system with all 4 disks installed, all you needed to do is simply install grub on the MBR of all the disks where you want it to be... Try that.

---

### Post by Leechpool on 2016-09-16
Hi,
Thanks for the advice. So the statement in the advanced Ubuntu installation guide as follows is simply wrong? (I guess it wouldn't be the first time a guide contained errors but I'm weary of rendering my system un-bootable and trying to untangle that mess. You may have gathered I'm not very good with GRUB. On most installations it just happened, and this is my first RAID array).

[I] If you do need to replace a faulty drive, after the drive has been replaced and synced, grub will need to be installed. To install grub on the new drive, enter the following:

sudo grub-install /dev/md0

Replace /dev/md0 with the appropriate array device name.
[/I]

Thanks again
:)

---

### Post by darkod on 2016-09-16
Yes, I think they have made a mistake with the grub-install /dev/md0. In case you have done a server install with SW raid, and watching carefully the final steps after it asks you if you want to install grub on the MBR, the command it actually performs is grub-install /dev/sda, never /dev/md0.

I have to admit I have never tried it with md0, maybe they somehow "linked" that to be identical to grub-install /dev/sda. But anyway, I consider it much cleaner to simply do the grub-install /dev/sda and then you don't need to be wondering if it was done right or not.

FYI, on my home server I have a 4-disk raid1 and I was installing grub with the grub-install /dev/sdX.

---

### Post by Vegan on 2016-09-16
best bet is to use a small SSD for the system and one or more hard disks for user files

raid is obsolete, all you need is to do is backup with a cron task and ignore the problem

---

### Post by Leechpool on 2016-09-17
Update:
I followed darkod's advice with sudo grub-install /dev/sdX and sudo grub-install /dev/sdY for the two new drives.
I then ran sudo update-grub, shutdown, removed the old still working drive, rebooted and every thing was fine with the degraded (2/3) array/system :) .
I then ran sudo mdadm /dev/md0 --grow --raid-devices=2 and same for md1 and md2 to reduce Raid 1 back to 2 drives.
Perfect.
thanks to everyone, especially darkrod!
:)

---

