---
title: "WinXP RAID0 Partition Table Problem"
date: 2011-04-24
forum: Server Platforms
---

### Post by scritchmus on 2011-04-24
Okay. Here's the scoop!

Really hoping someone can help.

I downloaded Ubuntu 10.10 32-bit for Desktop.
Burned the .iso to CD and ran it from CD without installing.

It worked great as long as I checked the nomodeset option under F6. (I'm  assuming this has something to do with ATI Radeon video drivers?)

So it worked and I wanted to install onto a HDD for faster operations.

My system has 3 HDD's.

HDD 1 and 2 are 160GB Seagates set up as a RAID0 array - as stripe0 and stripe1. This is my WindowsXP bootable drive.

HDD3 is a 40GB Maxtor drive formatted NTFS but not bootable. Just an old extra drive I use for storage and backup.

So I installed Ubuntu using the "Alongside Windows" option and directed  the installer to create a partition on the 40GB Maxtor and install  itself there.

The installer then split the drive roughly in half, keeping my NTFS  stuff on one partition and making the other partition ext4 and  installing Ubuntu there.

So far so good.

Then I did a reboot and entered the 9th circle of hell.

Computer never booted into Ubuntu nor can it boot into XP anymore.

Here's what I attempted so far:

Went into Windows Recovery Console:
    FIXMBR
    FIXBOOT

Still nothing.

BOOTCFG /SCAN reveals that it can't find any Windows installations. Great!

Even tried:

   sudo apt-get install lilo
   sudo lilo -M /dev/sda mbr

from Ubuntu to see if that might work.
Nope.

From what I can gather so far, it looks like I lost the partition table on my RAID drive.

Windows cant find it anymore, but I can see the drive in Ubuntu, I can  open it, I can open Folders, I can open/copy/move files. (This is at  least a good thing since I can backup files if I need to rebuild the  RAID array.)

gparted see's my RAID array as sdb and sdc. On both it says "Partition unallocated"

sdb has a warning: "Can't have partition outside the disk"
sdc has a warning: "Unrecognized disk label"

So. Is there any way to repair my RAID partition table  (using Ubuntu) so that Windows can see it again and boot into XP?

Why did Ubuntu destroy my partition table on the RAID array drives when I  told it to install onto a partition on the other 40GB HDD?

Since I can access the RAID drive through Ubuntu and save my important  stuff, I can rebuild the RAID array if need be and start over. But I  would rather avoid that if I can.

Why is it that Windows cant see the RAID array anymore, yet Ubuntu can? I  take it this is due to Ubuntu's superiority as an OS! Even though the  partition tables are destroyed on the RAID array drives, Ubuntu is still  able to take the two striped drives and assemble the data such that I  can see all files and folders. Take that Microsoft!!

Please Help!!!!

Thank you!!

P.S.                                                     I have since  re-formatted the 40GB HDD that I installed Ubuntu to. Mainly to have  space to copy important files to, from the RAID array drives. 

Keep in mind that I'm not  concerned with the Ubuntu install for now.  It has been removed. I just want to get my RAID array back so that I can boot into XP. 

Here is the results of the boot info script:

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc
 => Lilo is installed in the MBR of /dev/mapper/via_ddbaabaefd

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

via_ddbaabaefd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    80,292,869    80,290,822   7 HPFS/NTFS


Drive: via_ddbaabaefd ___________________ _____________________________________________________

Disk /dev/mapper/via_ddbaabaefd: 320.1 GB, 320083722240 bytes
255 heads, 63 sectors/track, 38914 cylinders, total 625163520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/via_ddbaabaefd1   *             63   625,137,344   625,137,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/via_ddbaabaefd1 E66C36F36C36BE5D                       ntfs                                     
/dev/mapper/via_ddbaabaefd: PTTYPE="dos" 
/dev/sda                                                via_raid_member                               
/dev/sdb                                                via_raid_member                               
/dev/sdc1        1174F7BC1AECD0B0                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sda1: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
via_ddbaabaefd
via_ddbaabaefd1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/via_ddbaabaefd1 /media/E66C36F36C36BE5D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory  
```

---

### Post by dtfinch on 2011-04-25
XP lacks any built-in support for RAID, which might be why the recovery console wasn't useful. If the recovery console lets you provide a driver disk like the installer does (I can't remember), which would provide the raid driver, and you have it somewhere, you might be able to get it working that way.

I haven't been in a situation like this, but you could try reinstalling the Windows MBR from Ubuntu using by installing the ms-sys package and running "sudo ms-sys -m /dev/mapper/via_ddbaabaefd". Installing the MBR to /dev/sda might also work (unless ms-sys needs to examine the filesystem), but in most other cases it's unsafe to modify raid members directly.

Installing the ms-sys package may be a bit involved as it was removed long ago from the main repository over license uncertainty, but you can get it from this PPA:
[https://launchpad.net/~rzr/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~rzr/+archive/ppa?field.series_filter=maverick)

If you're booting the live CD, you can still install packages to work with, but they'll disappear on reboot.

---

### Post by scritchmus on 2011-04-25
I am a little confused.

Is the problem a result of a missing MBR or missing/corrupted partition tables?

Doesn't the gparted results indicate missing/damaged partition table?

My motherboard has built in RAID capability. I never had to use an external driver while setting it up.

Granted, I'm no RAID expert, but to my surprise it was quite easy. Plugged my two SATA drives in. Went to BIOS and enabled SATA RAID.  Went into the RAID controller utility and set up a RAID0 array. Then installed XP onto the RAID array. Worked ever since. Until this.

So is the problem as simple as Ubuntu just writing over the MBR? And console recovery couldn't recover it because it was on a RAID array? But XP knew how to write it there during the Windows install.

The big burning question I have is why did Ubuntu do this? Is the Ubuntu installer package faulty? Did it overstep its bounds by overwriting the MBR?

What would have been the correct way to set up a dual OS system with WinXP and Ubuntu?

---

### Post by dtfinch on 2011-04-26
I don't see anything wrong with the partitions.

I think with the gparted warnings, on that boot the drives were detected in a different order (so the raid members were sdb and sdc instead of sda and sdb), which happens sometimes. On the first raid disk, it sees the full raid's partition table, and getting confused because the raid is twice as big as a single disk, and on the second, there shouldn't be any partition table for it to see.

You're positive there was no driver disk? Most motherboard raids (all that I know of) are the "fakeraid" type, software raid with bios support to get it to boot far enough for a driver to take over. That's why Linux can still read the raw disks at sda/sdb, and why the raid has a dmraid (linux's fakeraid driver) style /dev/mapper/ path rather than appearing as another drive. The official XP install disk to my knowledge doesn't even support SATA, much less RAID, unless you have a custom disk with "slipstreamed" drivers, or maybe an OEM disk that came with the system.

I think the "SystemRescueCD" live cd has that ms-sys package preinstalled if you don't want to mess with setting up a ppa on the Ubuntu live cd, though I haven't used it much.

---

### Post by scritchmus on 2011-04-27
There was no driver disk.

The only thing I did was to take original WinXP Professional SP1 CD and create a slipstreamed CD with  SP2 & SP3 added to it.

Is it that important that the install disk support SATA/RAID when it is built-in to the BIOS?

I will try the ppa method that you mentioned. Thank you for your time and advice. I appreciate it. And I hope you stick with me to the end!

Will keep you posted.

P.S. I still want to know why Ubuntu screwed up my RAID array drives when I installed it on a different HDD?

---

### Post by scritchmus on 2011-04-27
To be honest, now that I think about it, there could have been more involved in installing WinXP on to the RAID array. It has been awhile and I really don't remember how I did it. I will go that route when all other avenues are exhausted.

---

### Post by dtfinch on 2011-04-27
One of these bug reports might be related:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/654820](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/654820) (grub installing to sda instead of the raid)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/732771](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/732771) (grub overwriting windows MBR on fakeraid when told to install just to partition, though in that case they were installing Ubuntu to the raid)
Neither has had any replies or "me too" upvotes though.

---

### Post by scritchmus on 2011-05-23
Well, nothing worked.

So I just re-installed Windows.

OK.

Now that I have my computer back, what is the correct procedure for installing Ubuntu to a
separate HDD, WITHOUT destroying WinXP's Boot Record, so that I can have a dual OS system???

---

