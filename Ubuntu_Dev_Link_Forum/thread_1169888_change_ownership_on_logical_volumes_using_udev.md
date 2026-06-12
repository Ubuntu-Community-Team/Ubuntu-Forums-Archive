---
title: "change ownership on logical volumes using udev"
date: 2009-05-25
forum: Ubuntu Dev Link Forum
---

### Post by jp.hendrix on 2009-05-25
The short question is as follows:
I want to automatically set user:group permissions on a logical volume device node. By default udev assigns root:disk to all LV's.


The long story is as follows:
I have VirtualBox running and I want to use LV's instead of files for the disks. It is rather easy set up an LV for use with VirtualBox, using something like: 
```
vboxmanage internalcommands createrawvmdk -filename /home/user/.VirtualBox/HardDisks/w7rc.vmdk -rawdisk /dev/vg00/vm_Win7RC -register
```The problem is that during boot all LV's are assigned root:disk ownership, and I don't want a normal user added to the group "disk", because this is a gigantic security risk. So I am trying to figure out how I can configure udev to change some particular LV's to user:group.
So far, I've figured out that it is useless to use the FS_UUID for identifying LV's because not all Operating Systems support it (NTFS). A good option to identify my "target" LV is by LV-UUID or by name. Summarized: I want to be able to create a udev config file that tells the system to change ownership on "/dev/vg00/vm_W7RC" to user:group instead of the default root:disk.

My system: Linux diablo 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
udev version:141

Any help is welcome.

---

### Post by jp.hendrix on 2009-06-07
I created a file /etc/udev/rules.d/65-vmdmsetup.rules

with the following content:

```
SUBSYSTEM!="block",                             GOTO="vm_device_mapper_end"
KERNEL!="dm-*",                                 GOTO="vm_device_mapper_end"
ACTION!="add|change",                           GOTO="vm_device_mapper_end"

# Obtain device status
IMPORT{program}="/sbin/dmsetup export -j%M -m%m"
ENV{DM_NAME}!="?*",                             GOTO="vm_device_mapper_end"

ENV{DM_NAME}=="vg_usbraid-vm_laptop",           GROUP="jhendrix"
ENV{DM_NAME}=="vg_domU-domU_prime",             GROUP="jhendrix"

LABEL="vm_device_mapper_end"
```which sets the groupid on the LV to jhendrix at boot. Simply look with ls -l /dev/mapper which LV you want to configure. Somehow I need to change ownership by hand because of the ACTION line, but I'll figure that out next time ;)

---

### Post by russell-ault on 2009-07-30
So, as an addendum to this, I need to do exactly the same thing for exactly the same reasons (disk has way too much power to be user-level), but instead of using LVs I just need to alter the group-owner on a single partition (in this case /dev/sda2). I'm totally new to udev. Any thoughts?

---

### Post by jp.hendrix on 2010-03-11
> **russell-ault said:**
> So, as an addendum to this, I need to do exactly the same thing for exactly the same reasons (disk has way too much power to be user-level), but instead of using LVs I just need to alter the group-owner on a single partition (in this case /dev/sda2). I'm totally new to udev. Any thoughts?

Check my wikipage on udev. Not exactly your issue, but it may just help to get a little more understanding about udev. Notice that udev first has to find a disk, then run some tool to identify the partitions etc.

[http://wirespeed.xs4all.nl/mediawiki/index.php/Figuring_out_udev_rules](http://wirespeed.xs4all.nl/mediawiki/index.php/Figuring_out_udev_rules)

---

