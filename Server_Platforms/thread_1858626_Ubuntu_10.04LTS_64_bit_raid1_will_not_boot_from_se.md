---
title: "Ubuntu 10.04LTS 64 bit raid1 will not boot from second drive"
date: 2011-10-12
forum: Server Platforms
---

### Post by mucho_maze on 2011-10-12
I've installed Ubuntu 10.04LTS 64 bit in raid1 successfully using this guide: [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

Hd configuration (with SATA disks):
md0: / sda1 and sdb1
md2: swap sda5 and sdb5
md3: /home sda6 and sdb6
md4: /backup sda7 and sdb7
sda8 /media/no_raid (only on sda, this drive is larger than sdb)

In order to test booting in a degraded state, I tried to disconnect the secondary drive. Booting worked perfectly.

Then I disconnected the primary drive: SYSTEM WONT BOOT! I can hold down shift upon booting, and "GRUB" will appear on the screen, but nothing more when booting with the secondary drive alone. When both drives are connected, I can hold down shift, then e and I get the GRUB menu.

What am I doing wrong? I've configure mdadm to boot on degraded arrays.

---

### Post by vasile002 on 2011-10-12
do you get any errors? can you make a screen capture and show what exactly happens after the GRUB screen without the first HDD?

---

### Post by mucho_maze on 2011-10-13
> **vasile002 said:**
> do you get any errors? can you make a screen capture and show what exactly happens after the GRUB screen without the first HDD?

Hi vasile002,

Thanks for your reply.

There are no error messages (at least I cannot find any). The system is powered on, the HD-led flashes a few times, then the cd flashes and then the computer reboots: for me it seems that the pc cannot find anything to boot on.

However, having second drive connected only and holding down the shift-key, the text 'GRUB loading.' appears for a short time, and then the system reboots. As far as I can tell, this implies that GRUB is indeed installed on the second drive, but it cannot boot.

When I hold down shift + e having BOTH drives connect, I can successfully enter the GRUB menu, which contains this:

recordfail
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 698f0096-b284-45ca-bd0d-b5a16d3f0977
linux /boot/vmlinuz-2.6.32-34-server root=UUID=698f0096-b284-45ca-bd0d-b5a16d3f0977 ro quite
initrd /boot/initrd.img-2.6.32-34-server


The 'md0' seems to be correct, right?

There are no errors in the log and when a I reconnect the first drive, there is no syncronization (the drives are in sync =  indicates that ubuntu has not recognized that the first drive was ever off).

---

### Post by karlson on 2011-10-13
> **mucho_maze said:**
> Hi vasile002,

Thanks for your reply.

There are no error messages (at least I cannot find any). The system is powered on, the HD-led flashes a few times, then the cd flashes and then the computer reboots: for me it seems that the pc cannot find anything to boot on.

However, having second drive connected only and holding down the shift-key, the text 'GRUB loading.' appears for a short time, and then the system reboots. As far as I can tell, this implies that GRUB is indeed installed on the second drive, but it cannot boot.

When I hold down shift + e having BOTH drives connect, I can successfully enter the GRUB menu, which contains this:

recordfail
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set 698f0096-b284-45ca-bd0d-b5a16d3f0977
linux /boot/vmlinuz-2.6.32-34-server root=UUID=698f0096-b284-45ca-bd0d-b5a16d3f0977 ro quite
initrd /boot/initrd.img-2.6.32-34-server


The 'md0' seems to be correct, right?

Can you post /etc/fstab while you're at it?  The issue may be that if the UUID that GRUB points to is the one of the primary drive may be the reason why it's not booting from the secondary.

> 
There are no errors in the log and when a I reconnect the first drive, there is no syncronization (the drives are in sync =  indicates that ubuntu has not recognized that the first drive was ever off).

Because there were no updates to the secondary drive while the primary was disconnected.

---

### Post by mucho_maze on 2011-10-13
Thanks for replying karlson!

> **karlson said:**
> Can you post /etc/fstab while you're at it?  The issue may be that if the UUID that GRUB points to is the one of the primary drive may be the reason why it's not booting from the secondary.


Good idea, /etc/fstab/:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=698f0096-b284-45ca-bd0d-b5a16d3f0977 /               ext4    errors=remount-ro 0       1
# /backup was on /dev/md3 during installation
UUID=f362c244-84ca-4f4e-ab07-d04b80ea502a /backup         ext4    defaults        0       2
# /home was on /dev/md2 during installation
UUID=37243fc9-24e1-4483-8523-1e864f0dbaa7 /home           ext4    defaults        0       2
# /media/non_raid was on /dev/sda8 during installation
UUID=cd885a17-e5ea-4fcf-9a0e-03f0d7515f64 /media/non_raid ext4    defaults        0       2
# swap was on /dev/md1 during installation
UUID=42ae4acd-c87b-44f8-85b8-febe27877977 none            swap    sw              0       0

```

It seems that the UUID's are the same:

FSTAB: 698f0096-b284-45ca-bd0d-b5a16d3f0977 
GRUB:  698f0096-b284-45ca-bd0d-b5a16d3f0977

Right?

> **karlson said:**
> 
Because there were no updates to the secondary drive while the primary was disconnected.

Exactly!

---

### Post by vasile002 on 2011-10-13
while booted from both drives in RAID can you change any instance of UUID with the actual RAID device(/dev/md?)? Try to replace the UUIDs in both /etc/fstab and in the grub config files/mbr

Please let us know the results

---

### Post by karlson on 2011-10-13
> **mucho_maze said:**
> Thanks for replying karlson!



Good idea, /etc/fstab/:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=698f0096-b284-45ca-bd0d-b5a16d3f0977 /               ext4    errors=remount-ro 0       1
# /backup was on /dev/md3 during installation
UUID=f362c244-84ca-4f4e-ab07-d04b80ea502a /backup         ext4    defaults        0       2
# /home was on /dev/md2 during installation
UUID=37243fc9-24e1-4483-8523-1e864f0dbaa7 /home           ext4    defaults        0       2
# /media/non_raid was on /dev/sda8 during installation
UUID=cd885a17-e5ea-4fcf-9a0e-03f0d7515f64 /media/non_raid ext4    defaults        0       2
# swap was on /dev/md1 during installation
UUID=42ae4acd-c87b-44f8-85b8-febe27877977 none            swap    sw              0       0

```

It seems that the UUID's are the same:

FSTAB: 698f0096-b284-45ca-bd0d-b5a16d3f0977 
GRUB:  698f0096-b284-45ca-bd0d-b5a16d3f0977

Right?

Appears so.

> 
Exactly!

Just as a sanity check is GRUB installed on every disk?  and are there any issues with booting from a secondary disk from BIOS?

---

### Post by mucho_maze on 2011-10-13
Thanks for the suggestions.

> **karlson said:**
> Appears so.

Just as a sanity check is GRUB installed on every disk?  and are there any issues with booting from a secondary disk from BIOS?

I ran the commands

```

sudo grub-install /dev/sda
sudo grub-install /dev/sdb

```

in order to ensure that GRUB is on both drives MBR. That didn't make any difference.

I also ran

```

sudo grub-install /dev/md0

```

but it gave errors saying that it not recommended to install GRUB any other places that the MBR. Then I reinstall GRUB on /dev/sda and /dev/sdb.

To verify that the BIOS was able to boot from secondary drive, I switched the primary hdd to the secondary SATA cable (with this drive only). It booted up just fine.

---

### Post by mucho_maze on 2011-10-13
Thanks for your answer.

> **vasile002 said:**
> while booted from both drives in RAID can you change any instance of UUID with the actual RAID device(/dev/md?)? Try to replace the UUIDs in both /etc/fstab and in the grub config files/mbr

Please let us know the results

I'll try this tomorrow.

And I'll let you know the solution as soon as I get the server to boot..

---

### Post by mucho_maze on 2011-10-13
> **karlson said:**
> Appears so.

Just as a sanity check is GRUB installed on every disk?  and are there any issues with booting from a secondary disk from BIOS?

BTW, I tried to switch the secondary hdd to the primary SATA (without using the other hdd) and from here it couldn't boot either... hmm. Exactly the same behaviour as when connected to the secondary SATA.

It seems something is missing on this drive... but what could it be?

---

### Post by karlson on 2011-10-13
> **mucho_maze said:**
> btw, i tried to switch the secondary hdd to the primary sata (without using the other hdd) and from here it couldn't boot either... Hmm. Exactly the same behaviour as when connected to the secondary sata.

It seems something is missing on this drive... But what could it be?


grub...

---

### Post by mucho_maze on 2011-10-16
> **karlson said:**
> grub...

Yes exactly. GRUB was not install on /dev/sdb, even though I've run

```

sudo grub-install /dev/sda
sudo grub-install /dev/sdb

```

When trying to install on md0 I got the following
```

sudo grub-install /dev/md0

usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required when the root device is on a RAID array or LVM volume.

```

So the question was how to install GRUB. It turned out that I needed to run these commands

```

grub-setup -r  &#8221;(hd1)&#8221; /dev/sdb
grub-install --modules=raid /dev/sdb (thanks to HanB: http://ubuntuforums.org/showthread.php?t=1539205)

```

in order to install GRUB properly. After these commands have been run, I can take out either of the two drives, sda and sdb, and have a functioning system.

Thanks for all your help.

---

### Post by GabrielSyme on 2012-10-23
> **mucho_maze said:**
> Yes exactly. GRUB was not install on /dev/sdb, even though I've run

```

sudo grub-install /dev/sda
sudo grub-install /dev/sdb

```

When trying to install on md0 I got the following
```

sudo grub-install /dev/md0

usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required when the root device is on a RAID array or LVM volume.

```

So the question was how to install GRUB. It turned out that I needed to run these commands

```

grub-setup -r  ”(hd1)” /dev/sdb
grub-install --modules=raid /dev/sdb (thanks to HanB: http://ubuntuforums.org/showthread.php?t=1539205)

```

in order to install GRUB properly. After these commands have been run, I can take out either of the two drives, sda and sdb, and have a functioning system.

Thanks for all your help.

This post is a year old, but you just saved my bacon, sir! My hat is off to you. Thank you so much. This *really* should be documented somewhere.

---

