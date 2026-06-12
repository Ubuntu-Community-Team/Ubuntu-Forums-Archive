---
title: "Increase Partition Size on Ubuntu Server 11.04"
date: 2011-08-25
forum: Server Platforms
---

### Post by leonardknight on 2011-08-25
I have a server setup running VirtualBox and several Windows guests.  I'm running the box headless and start the windows machines using 

```
sudo vboxheadless -s "WinXP Pro SP3"&
```

via SSH session from my MacBookPro in terminal.  I then connect to the Virtual Machines running MS Remote Desktop from the MacBookPro.  All of this works perfectly except that I've run out of space on my partition for Virtual Machines and need to create a few more.  I have plenty of room on the HDD but when first installing Ubuntu Server I only partitioned and formated about 1/4 of the drive.

Now for my question:

Is it possible to run a command in my SSH session at the command line to partition the unused portion of the HDD, format it, and expand my current partition into that space?  Or, do I have to use something like gpartedlive, boot from the CD and do the partitioning?

Any help is greatly appreciated!  I'll be posting other questions soon as I'm very new to setting up and running a server.

---

### Post by YesWeCan on 2011-08-25
Do you mean that you want to remotely resize a partition on your server's hard drive? So this isn't really a VirtualBox issue? Or are you wanting to resize an active partition (without shutting VB down)?
Is the partition you wish to resize separate from the OS root partition?

---

### Post by leonardknight on 2011-08-25
Sorry, for all the extra information.

This isn't related to VirtualBox at all...I just provided that information since creating a new Virtual Machine is the main goal...and running out of space is the real problem.

I can shutdown all the VM's, VirtualBox and the Server...non of them are critical to continue running.

Here are the results of "fdisk - l"

```
lrknight@vm-server:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000b360

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       91202   732322817    5  Extended
/dev/sda5              32       91202   732322816   8e  Linux LVM

Disk /dev/dm-0: 71.9 GB, 71886176256 bytes
255 heads, 63 sectors/track, 8739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 3099 MB, 3099590656 bytes
255 heads, 63 sectors/track, 376 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 3099 MB, 3099590656 bytes
255 heads, 63 sectors/track, 376 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8e8c7fd

Disk /dev/dm-2 doesn't contain a valid partition table

```

This is a 750 Gb disk and I want to use more for cloning virtual machines.

---

### Post by YesWeCan on 2011-08-26
It looks like your main linux partition uses LVM so that makes things easy. Have a look here: [http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

To get more detailed help you'll need to post the LVM volume groups and logical volumes from the output of
[COLOR=Navy]sudo lvs[/COLOR]

Basically, you may not be able to remotely resize the active physical partition sda5 because it is running the OS. But what you can do is create a new physical partition, sda6, and add it to your LVM volume group and then extend the logical volume that you use for VBox.

To create a new, extended partition using fdisk: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

To add it to your volume Group
[COLOR=Navy]sudo pvcreate /dev/sdax[/COLOR]   (x=number of the new partition)
[COLOR=Navy]sudo vgextend mv_volume_group /dev/sdax[/COLOR]

To expand a logical volume by 1GB
[COLOR=Navy][FONT=Arial][SIZE=2]lvextend -L+1G /dev/my_volume_group/my_logical_volume
resize2fs /dev/my_volume_group/my_logical_volume[/SIZE][/FONT][/COLOR]

---

### Post by leonardknight on 2011-09-01
I'm still having issues with resizing my partition.

Here are some screen shots while running from LIVE Ubuntu 11.04 CD.  Tried Disk Utility and Gparted but they don't seem to be able to resize a partition.

[https://picasaweb.google.com/leonardrknight/ScreenShots?authuser=0&feat=directlink](https://picasaweb.google.com/leonardrknight/ScreenShots?authuser=0&feat=directlink)

---

### Post by YesWeCan on 2011-09-01
GParted can't cope with LVM at all. Disk Utility can't resize partitions.

It looks like you have 675GB unallocated space in your "vm-server" VG which you can use to expand the "root" LV.

In a live CD console (having installed lvm2):
[COLOR="Navy"]sudo lvextend -L+675G /dev/vm-server/root
sudo e2fsck -f /dev/vm-server/root
sudo resize2fs /dev/vm-server/root[/COLOR]

---

### Post by leonardknight on 2011-09-01
Thank you!  That worked perfectly!

---

### Post by YesWeCan on 2011-09-02
You're welcome. Don't forget to mark this as solved in [COLOR="Red"]Thread Tools[/COLOR].

---

