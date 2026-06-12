---
title: "LVM w/RAID1 - RAID device not present on restart"
date: 2011-01-29
forum: Server Platforms
---

### Post by Rab22 on 2011-01-29
I've decided to toy around with LVM and mdadm this weekend. I can get everything working, and all is well, until I restart. After that, I no longer have any /dev/md0 device, which during the auto mount process, causes an error. 

I've looked through several HOWTOs, as well as the LVM/mdadm man pages, and I believe I've tracked it down to mdadm's "assemble" that is needed (so that LVM can see the md0 device). Not exactly sure how to go about having this occur during the boot process to ensure that the LVM mapped drive is available for when fstab is read. 

I'm sure it's something simple...and I'm overlooking it :(

In case it helps this is a base install of 10.10 server 64. I have four drives, the first is used for the OS and is not in the RAID array (nor LVM). The second and third are RAID1 (/dev/md0) and there is a volume group associated with /dev/md0. The last is a LVM, but not RAID, and it has its own volume group.

Thanks!

---

### Post by Rab22 on 2011-01-29
BTW, just realized I forgot to add that the /dev/sdd LVM displays just fine after reboot. 


But still cannot figure out how to get mdadm to assemble on boot. :(

---

### Post by YesWeCan on 2011-01-29
Are your HDs set to type "Linux raid auto detect"?
Check with 'sudo fdisk -l'

---

### Post by Rab22 on 2011-01-29
> **YesWeCan said:**
> Are your HDs set to type "Linux raid auto detect"?
Check with 'sudo fdisk -l'

Yup. /dev/sdb1 and /dev/sdc1 are set with FD - Linux raid autodetect.

(sorry, working on my laptop so I can't copy/paste the output)

Another strange thing is that after rebooting,```
sudo mdadm --assemble --scan 
``` only restarts the first drive (/dev/sdb1). When attempting to ```
 sudo mdadm --manage --add /dev/sdc1 
``` I receive a "a device or resource is busy" error. I tried ```
sudo fuser -m /dev/sdc1
``` to locate it, and nothing, I also tried ```
sudo lsof | grep sdc1 
``` as well, and nothing. 

Figured maybe I could stop the RAID and restart, tried ```
sudo mdadm --stop /dev/md0
``` and same device is busy error.

...this is getting way past my level of knowledge :(

---

### Post by YesWeCan on 2011-01-29
When you are able to post, we'd better take a look at
sudo fdisk -l
sudo blkid
/etc/fstab
/etc/mdadm/mdadm.conf

---

### Post by Rab22 on 2011-01-29
> **YesWeCan said:**
> When you are able to post, we'd better take a look at
sudo fdisk -l
sudo blkid
/etc/fstab
/etc/mdadm/mdadm.conf

Okay, I can get it on here...I just need to put the command output onto my usb stick. 

Give me a few minutes.

Thanks for your help!

---

### Post by Rab22 on 2011-01-29
**blkid output:**
```

/dev/sda1: UUID="1dad0cbe-85fd-4036-a887-813c057f1097" TYPE="ext2" 
/dev/sda2: LABEL="Recovery" UUID="2C88743C8874071C" TYPE="ntfs" 
/dev/sda5: UUID="69240c90-48c1-4113-81c6-4354ade0a098" TYPE="ext4" 
/dev/sda6: UUID="255d0ecb-ed81-4586-a224-469e92f8e97e" TYPE="swap" 
/dev/sdb1: UUID="fca621f8-e194-5614-92b4-038b23779ef6" TYPE="linux_raid_member" 
/dev/sdd1: UUID="Ia057v-PPBO-CZZz-TDE0-7xg6-Q40B-xnlYOY" TYPE="LVM2_member" 
/dev/mapper/vg_nonraid_data_01-lv_nonraid_data_01: UUID="9e6a1385-8037-42d7-9b0e-e41ac764459b" TYPE="ext4" 
/dev/sdi1: LABEL="PENDRIVE" UUID="1CB0-4FD1" TYPE="vfat" 
/dev/md0: UUID="Wdnw2F-1OtV-PA5P-nNz1-H4yS-YupM-CmMfMu" TYPE="LVM2_member" 
/dev/mapper/vg_raid_data_01-lv_raid_data_01: UUID="0f2b5fce-a2de-47fe-be63-565ec3560767" TYPE="ext4" 

```

**fdisk output:**
```



Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          63      498688   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2           37928       38913     7920045    7  HPFS/NTFS
/dev/sda3              63       37927   304147457    5  Extended
/dev/sda5              63       37178   298127360   83  Linux
/dev/sda6           37178       37927     6019072   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35101150

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7a467639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff84ac1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001   8e  Linux LVM

Disk /dev/dm-0: 250.0 GB, 250001489920 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdi: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders
Units = cylinders of 735 * 512 = 376320 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1       21270     7816688    b  W95 FAT32

Disk /dev/md0: 320.1 GB, 320070221824 bytes
2 heads, 4 sectors/track, 78142144 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/dm-1: 320.0 GB, 320000229376 bytes
255 heads, 63 sectors/track, 38904 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```

**fstab output:**
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=69240c90-48c1-4113-81c6-4354ade0a098 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=1dad0cbe-85fd-4036-a887-813c057f1097 /boot           ext2    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=255d0ecb-ed81-4586-a224-469e92f8e97e none            swap    sw              0       0

```

**mdadm.conf file**
```


# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sat, 29 Jan 2011 03:34:21 -0600
# by mkconf $Id$

```

---

### Post by Rab22 on 2011-01-29
Okay, I just noticed that /dev/sda1 is also giving me some errors related to the partition table -- partition 1 does not end on a cylinder boundary. 

I allowed the installer to set up my partitions on the first drive for me, so not sure why that occurred. I was hoping to keep my recovery partition, so that when I build my next server I could recover Windows and give this computer to my bro. Guess I'll just need to order the recovery CDs. 

I think at this point, I'm going to scrap this install and restart (as there are no files on it currently). Still not certain why the RAID1 would not work for me...hopefully reinstalling will help!

Thanks for the help!

---

### Post by YesWeCan on 2011-01-29
One obvious problem is that fstab does not have an entry for your RAID array. The array will not be mounted at boot unless it is listed here.

I'm not sure whether the sda cylinder thing is important or not. It certainly has nothing to do with the RAID issue.

---

### Post by Rab22 on 2011-01-29
> **YesWeCan said:**
> One obvious problem is that fstab does not have an entry for your RAID array. The array will not be mounted at boot unless it is listed here.

I'm not sure whether the sda cylinder thing is important or not. It certainly has nothing to do with the RAID issue.

I tried adding it to fstab earlier. I tried by both UUID and next by /dev/mapper/md0. For both I had to "skip" the fstab mounts during boot because the device /dev/md0 didn't yet exist. After skipping and returning into the system, I couldn't locate the /dev/md0 device until I did a mdadm --assemble --scan command.

My assumption was that fstab was read, attempted to mount the md0 device, but since no dameon for RAID1 had yet ran, no device was "configured" to mount. I looked around the scripts, but couldn't find anything to start RAID. 

LVM is so much easier to setup...I should stick with that...who needs reliability! :)

---

### Post by 1clue on 2011-01-29
It took me a few times to get it right.

Let me ask an explicit question that may seem obvious:

You have RAID on the disk, then LVM2 running on top of that, right?  That's the usual way, but not the only way.

Most RAID modes require that all partitions be essentially identical.  There are modes that don't but I think those are aimed at just stringing a bunch of old junk together.

First, you need to set your partition types to RAID autodetect.  It seems you've done that.

Second, you need to have the UUID set to the same value for all partitions on a single array.  That's how the kernel knows which partitions go with which.

I have everything on RAID but only some things on LVM.  /boot and / are raid1 right on the bare disk, and everything else is on LVM2.

---

### Post by Rab22 on 2011-01-29
Appears the partition 1 issue maybe with 10.10 server installer? I selected to use the entire disk and the same result occurred. I'm going to manually partition this time around...

---

### Post by Rab22 on 2011-01-29
> **1clue said:**
> It took me a few times to get it right.

Yeah, I figured it would take me a few tries. It is frustrating, but I'm doing it just because its something I haven't done yet. I've wanted to mess with it for years, but always just used LVM. 

> **1clue said:**
> 
Let me ask an explicit question that may seem obvious:

You have RAID on the disk, then LVM2 running on top of that, right?  That's the usual way, but not the only way.

Most RAID modes require that all partitions be essentially identical.  There are modes that don't but I think those are aimed at just stringing a bunch of old junk together.


Yes, I have RAID on the disk and then LVM2 running on top. Here was my command order... 

```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```
```
sudo pvcreate /dev/md0
```
```
sudo vgcreate vg_name /dev/md0 
```
```
lvcreate --name lv_name --size 298.02G vg_name
```

From there I built the ext4 filesystem on /dev/vg_name/lv_name

> **1clue said:**
> 
Second, you need to have the UUID set to the same value for all partitions on a single array.  That's how the kernel knows which partitions go with which.

I have everything on RAID but only some things on LVM.  /boot and / are raid1 right on the bare disk, and everything else is on LVM2.

Not sure how to set the UUID for the array...do I just use the UUID that is in /dev/disk/by-uuid for the /dev/md0?

Thanks!! :)

---

### Post by Rab22 on 2011-01-30
I think there are some bugs with the 10.10 server installer.

For one, the bootable flag does not get toggle to 'YES' when changed via the option even though fdisk reports the change. It will go from YES to NO but not back again. I opened up tty2 and fdisk showed it set properly. I had to 'Go back' a page and select the partition setup again to see it. I tried a few times to ensure it was in fact an issue.

Second, it appears that the automated partition has an issue with using the END cylinder of the boot partition as the start of the next logical partition being built. I'm not certain of the risks associated with this, but I fear that if that cylinder is written to, it would affect data in both the primary and the logical. Took me three installs (on the third I manually partitioned using fdisk on tty2). 

On a good note, somehow mdadm now is correctly registering md0 during the boot process and the LVM is available when mounting fstab. I do receive an initial error when booting about md0 not available, but I couldn't read the entire error in time and didn't find it (grep) in /var/log/dmesg. I'll further research that tomorrow.

So all in all, good day. :)

---

### Post by 1clue on 2011-01-30
> **Rab22 said:**
> Yeah, I figured it would take me a few tries. It is frustrating, but I'm doing it just because its something I haven't done yet. I've wanted to mess with it for years, but always just used LVM. 


Me too.  Just recently started messing with RAID.

> 
Not sure how to set the UUID for the array...do I just use the UUID that is in /dev/disk/by-uuid for the /dev/md0?

Thanks!! :)

I'm not sure.  :oops:

When you run mdcreate I think it should write the UUID for you.  There's an option in mdadm create to set the UUID, but I don't think that's what I used.

FWIW I did the disk admin stuff from the Gentoo disk.  That's where I tried RAID first and so I keep going back.

My starting point was here:
[http://www.gentoo.org/doc/en/gentoo-x86+raid+lvm2-quickinstall.xml](http://www.gentoo.org/doc/en/gentoo-x86+raid+lvm2-quickinstall.xml)

Start looking at code listing 2.10.

Here's a thread of mine when I tatered my boot, I got related help:
[http://forums.gentoo.org/viewtopic-t-825105-highlight-raid.html](http://forums.gentoo.org/viewtopic-t-825105-highlight-raid.html)

I can't seem to find the part I'm looking for though.

It's pretty late where I am right now, maybe I'll find something more relevant tomorrow.

---

### Post by YesWeCan on 2011-01-30
Referring to post #7, your fdisk report is inconsistent with your description of your system.

/dev/sda 320GB boot Ubuntu
/dev/sdb 250GB raid
/dev/sdc 250GB raid
/dev/sdd 250GB
/dev/sdi  8GB boot W95

which look ok

/dev/md0 320GB
/dev/dm-0 250GB
/dev/dm-1 320GB

Which do not look ok
What you should have is a single /dev/md0 250GB

So I suspect something has gone wrong in your RAID configuration. I am not sure where the dm prefixes came from...reminds me of dmraid which is definitely not something you should have installed. If you do, uninstall it and start again.

I know you have reinstalled the OS and the RAID now mounts but you are getting this fleeting error message on boot. Don't ignore this. Try booting from the recovery/safe OS option of the boot menu so that you can see all the spew.

Also, please post your latest fdisk -l. O:)

---

### Post by Rab22 on 2011-01-30
> **YesWeCan said:**
> Referring to post #7, your fdisk report is inconsistent with your description of your system.

/dev/sda 320GB boot Ubuntu
/dev/sdb 250GB raid
/dev/sdc 250GB raid
/dev/sdd 250GB
/dev/sdi  8GB boot W95

which look ok

/dev/md0 320GB
/dev/dm-0 250GB
/dev/dm-1 320GB

Which do not look ok
What you should have is a single /dev/md0 250GB

So I suspect something has gone wrong in your RAID configuration. I am not sure where the dm prefixes came from...reminds me of dmraid which is definitely not something you should have installed. If you do, uninstall it and start again.

I know you have reinstalled the OS and the RAID now mounts but you are getting this fleeting error message on boot. Don't ignore this. Try booting from the recovery/safe OS option of the boot menu so that you can see all the spew.

Also, please post your latest fdisk -l. O:)

There is actually 3 320, (two for RAID one for the OS) and one 250. But yes, I see what you are saying. Not exactly sure how that happened. The dm-# have always been created.

I can't post my current fdisk as I'm away from the computer currently. But when I get back to it, I'll take a look.

Yeah, I'm planning to review the error. I don't want it to work for 2-3 months just to lose everything. That would stink!

Thanks!

---

### Post by dtfinch on 2011-01-30
What does /proc/mdstat say when it fails to assembly md0?

There's a bug I've encountered a few times (in 10.04 at least) where mdadm's autoassembly sometimes steals a disk to create a new stopped raid under a different name (like md_d0 instead of md0), causing it to be unable to add the disk to md0, and causing the "device or resource is busy" when you try to add it manually. Listing the raid arrays in mdadm.conf seems to fix it.

If there is a rogue array:
mdadm --stop /dev/md_d0 (frees up the disk to be added to md0)
mdadm --assemble --scan (or add the disk manually)

Then add your array info your mdadm.conf:
mdadm -Es >> /etc/mdadm/mdadm.conf
update-initramfs -u

I also had problems getting LVM to see the raid on bootup. On 10.04 there's an issue with the udev rule (/lib/udev/rules.d/85-lvm2.rules) causing it to ignore md devices. Copying the file to /etc/udev/rules.d and removing the filter 'ENV{ID_FS_TYPE}=="lvm*|LVM*",' fixed it for me, in case the problem still exists.

---

### Post by YesWeCan on 2011-01-31
> **Rab22 said:**
> There is actually 3 320, (two for RAID one for the OS) and one 250. But yes, I see what you are saying. Not exactly sure how that happened. The dm-# have always been created.
Yes, my mistake.
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
Disk /dev/sdc: 320.1 GB, 320072933376 bytes
Disk /dev/sdd: 250.1 GB, 250059350016 bytes
Disk /dev/dm-0: 250.0 GB, 250001489920 bytes
Disk /dev/sdi: 8004 MB, 8004304896 bytes
Disk /dev/md0: 320.1 GB, 320070221824 bytes
Disk /dev/dm-1: 320.0 GB, 320000229376 bytes
```
The dm-0 and dm-1 also sound like names hardware RAID gives things. You might want to check that you have disabled RAID in your bios. Just a thought.

---

