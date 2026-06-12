---
title: "Can I controll the initrd module load order?"
date: 2006-07-20
forum: Server Platforms
---

### Post by ScatterBrain on 2006-07-20
I've got a Dell PowerEdge 850 that has a PERC4/SC attached to a Dell Powervault 220s for backup data storage.  The Powervault has two logical drives which were assigned as /dev/sdc and /dev/sdd.  The two internal 80GB SATA drives were assigned as /dev/sda and /dev/sdb and they contained the OS and the root directory tree.  The SATA drives each have 6 paritions on them all of which are tied together in software RAID1 arrays.

```
/dev/md0 = /dev/sda1+dev/sdb1 = /boot
/dev/md1 = /dev/sda2+/dev/sdb2 = /
/dev/md2 = /dev/sda3+/dev/sdb3 = /home
/dev/md3 = /dev/sda5+/dev/sdb5 = /var
/dev/sda4+/dev/sdb4 are extended partitions
/dev/sda6+/dev/sdb6 are used a swap space.
``` 

The two logical drives in the powervault I mounted under /daily and /monthly.

Two days ago, I needed to add an additional physical drive to one of the logical drives in the Powervault.  So I did, I used 'dellmgr' (a tool to manange the PERC RAID controller) to "reconstruct" Logical Drive 0 in the Powervault to increase its space.  This completed some time late on Tuesday night.

I came in yesterday morning to begin the expansion of the LVM and the XFS file system built on top of the Powervault logical drive.  I forced the machine to remove and then re-add the logical drive, which happened, but the drive got assigned to /dev/sde instead of /dev/sdc.  I figured no biggie, I've not really done anything except unmount the partition, so I rebooted the machine thinking that afterwards the proper drive assignment would return.

Well I was wrong.

For some reason (and I think it was because of kernel upgrade for security reasons I did just prior to this operation, but never booted on) when the machine came up, it failed saying that it couldn't find /dev/md1 - the root partition on the SATA software RAID array.  Throughout the day yesterday I've determined the reason for this is that the MegaRAID modules needed to access the drives in the Powervault are loading first and then SATA modules and the drive assignments have changed.

So, with the assistance of a guru friend of mine we "hacked" up a working initrd that makes the system boot like it should (very long story, one that I will probably blog about).  But my fear is that when I install my next kernel - that this same problem will return.

My question to the group is - **Is there a way that I can control which modules load and in which order in the initrd?**  From the looks of it, if I build a "stock" initrd, the MegaRAID modules will alwys load first and I'll have a borked box after the reboot.


HELP!

---

### Post by ScatterBrain on 2006-07-20
Well it looks like I can control this...

First, in **/etc/mkinitramfs/initramfs.conf**, make this change:

```
change this line:

[COLOR=Navy]MODULES=most[/COLOR]

to this line

[COLOR=Navy]MODULES=list[/COLOR]
``` 
Then you can edit the file /etc/mkinitramfs/modules and put in all the modules that your machine needs to boot.  In my case I had to use this list:

```
scsi_mod
sd_mod
libata
ata_piix
raid1
md
ext3

``` 
and then rebuild the initrd by either:

```
sudo dpkg-reconfigure linux-image[kernel version if needed]
``` 
or

```
sudo mkinitramfs -o /boot/initrd.img-[running kernel version here]
``` 
And then reboot.

BTW, a word of warning: Make sure that you load the filesystem modules for all the filesystems needed to boot the machine - in my case I only needed **ext3**, but some people may need others.

---

### Post by az on 2006-07-20
Would you please file a bug report about this?

Perhaps udev should be able to make this sort of thing not happen.

---

### Post by ScatterBrain on 2006-07-20
Done:

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/53546](https://launchpad.net/distros/ubuntu/+source/udev/+bug/53546)

---

