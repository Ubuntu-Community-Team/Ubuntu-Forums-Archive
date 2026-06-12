---
title: "HW RAID disk shows up in fstab but not in /dev/disk/by-uuid?"
date: 2010-06-28
forum: Server Platforms
---

### Post by fowie on 2010-06-28
I have an SiI hardware SATA RAID card, with two 500GB disks in mirrored RAID configuration.  When I first plugged them in and set it up, things seemed to work ok, but on boot the raid controller told me that the RAID needed rebuilding, and it would happen automatically after POST.  So I didn't worry about it, and the drive mounted fine, and it's been that way for years.  I just went in and manually on-line rebuilt the RAID in the controller's BIOS, and now when I boot into Ubuntu, both disks show up in fdisk, but neither show up in /dev/disk/by-uuid.  Am I missing something?

---

### Post by jbrown96 on 2010-06-28
Unless you are dual-booting with Windows on that RAID array, then you are far, far better off using Linux software RAID. It's faster, more reliable, and easier to configure. However, you may need to install from the alternate cd.

posting the output of ```
sudo fdisk -l
``` would help.

---

### Post by fowie on 2010-06-29
Well, you asked for it,
```

Disk /dev/sda: 9100 MB, 9100044288 bytes
64 heads, 32 sectors/track, 8678 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8678     8886256   83  Linux

Disk /dev/sdb: 9100 MB, 9100044288 bytes
64 heads, 32 sectors/track, 8678 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8678     8886256   83  Linux

Disk /dev/sdc: 18.2 GB, 18209792000 bytes
255 heads, 63 sectors/track, 2213 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4af884f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2116    16996738+  83  Linux

Disk /dev/sdd: 13.0 GB, 13022324736 bytes
255 heads, 63 sectors/track, 1583 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8a3d8a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1510    12129043+  83  Linux
/dev/sdd2            1511        1583      586372+   5  Extended
/dev/sdd5            1511        1583      586341   82  Linux swap / Solaris

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   83  Linux

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   83  Linux

Disk /dev/sdg: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       24319   195342336   83  Linux

```
dev sdd is my os disk.  Dev's sda/b/and c are all LVM'ed into my /var/www area (and subversion).  sdg is an IDE drive for backups, leaving sde and sdf, which are the two 500GB that are mirrored.

Thanks for the plug, yes, I've weighed the consequences, but as you can see, it's a little late to start everything over so I can deal with linux's wonderful software raid.  I'll stick with my hardware.  And yes, I've read the FAQ's and HOWTOs about the differences.

---

### Post by fowie on 2010-06-29
Oh yeah, and I guess if you wanted to explain how I could keep all of the data on the 500GB drives WHILE switching to software, THEN maybe I'd be open to that idea...

---

### Post by Vegan on 2010-06-29
Do not use software RAID is no good, stick with the controller.

The sda shows the pair of 500GB disks so do not worry about it.

---

### Post by fowie on 2010-06-29
Wow, I really love this completely off-topic discussion, but could someone maybe reply with an answer to my actual question?  Why don't the drives show up in /dev/disk/by-uuid?

ls -lah /dev/disk/by-uuid shows:
```

lrwxrwxrwx 1 root root  10 2010-06-28 20:00 36016408-d426-4284-83d7-695828a9b146 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2010-06-28 20:00 40bb79a6-87db-45e8-a8a5-e5f3854e46a1 -> ../../sdd5
lrwxrwxrwx 1 root root  28 2010-06-28 20:00 5c6fc833-559b-4156-8da1-765b6edeacab -> ../../mapper/scsiLVM-scsiLVM
lrwxrwxrwx 1 root root  10 2010-06-28 20:00 a3c7ba39-57e4-4357-9f71-103cf1d17ac9 -> ../../sdg1

```
The scsiLVM is /dev/sda,b,and c, and sdg1 is the 200GB IDE backup, but not entry for /dev/sde or /dev/sdf?

---

### Post by fowie on 2010-06-29
some more info, if I try
```

sudo mount /dev/sdf1 /sataraid/

```
I get:
```

mount: unknown filesystem type 'LVM2_member'

```
but sorry, these aren't LVM2, they're standard EXT3 in a RAID1 configuration

---

### Post by jbrown96 on 2010-06-30
when you use the fake mobo raid, then the OS can't see the individual disks. It will show up as one disk to the OS. It's /dev/sde.

There's your answer.

---

### Post by fowie on 2010-06-30
Thanks, but why can't I access it?  Before, I could just mount /dev/sde1 and it worked fine, now I get this LVM2 error.  Not to mention that neither /dev/sde1 NOR /dev/sdf1 are listed in /dev/disks/by-uuid, so my question remains unanswered...

---

### Post by fowie on 2010-06-30
I agree with you, and theoretically, that's how it should work, but if you look at my fdisk output, you'll see that's not the case.  The two 500GB drives are in hardware RAID1 configuration, yet they BOTH appear in Linux's fdisk as /dev/sde1 and /dev/sdf1.  Even if you're correct and it should be accessible as /dev/sde1, why can't I access it?  Before, I could just mount /dev/sde1 and it worked fine, now I get this LVM2 error.  Not to mention that neither /dev/sde1 NOR /dev/sdf1 are listed in /dev/disks/by-uuid, so my question remains unanswered, why are they not there, and why can't I mount them?

---

### Post by jbrown96 on 2010-06-30
Could you post what's in /dev/disks/by-uuid ```
sudo ls /dev/disks/by-uuid
``` and then ```
sudo blkid
``` I imagine they will be the same but worth checking. You could also try running ```
sudo partprobe
``` and then see if you get different results from blkid.

---

### Post by fowie on 2010-07-01
see post #6 for /dev/disk/by-uuid, but here it is again:
```



fowie@FowieWeb:~$ sudo partprobe
fowie@FowieWeb:~$ sudo blkid
/dev/sda1: UUID="JmrYSl-lPhx-9RK1-c3A8-3Umm-kgVs-gC611o" TYPE="LVM2_member" 
/dev/sdb1: UUID="2vpUQ5-WVYB-3u7x-epjA-eIhU-GnTX-DlSfgL" TYPE="LVM2_member" 
/dev/sdc1: UUID="X73RbP-aWSW-ZqP1-U2oL-enQH-HIqk-s2sB02" TYPE="LVM2_member" 
/dev/sdd1: UUID="36016408-d426-4284-83d7-695828a9b146" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd5: UUID="40bb79a6-87db-45e8-a8a5-e5f3854e46a1" TYPE="swap" 
/dev/sde1: UUID="Tfgow0-KNGT-4t3n-ciHn-1ScJ-r63r-tPaBdm" TYPE="LVM2_member" 
/dev/sdf1: UUID="Tfgow0-KNGT-4t3n-ciHn-1ScJ-r63r-tPaBdm" TYPE="LVM2_member" 
/dev/mapper/scsiLVM-scsiLVM: UUID="5c6fc833-559b-4156-8da1-765b6edeacab" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdg1: LABEL="BACKUP_HD" UUID="a3c7ba39-57e4-4357-9f71-103cf1d17ac9" TYPE="reiserfs" 
fowie@FowieWeb:~$ sudo ls -lah /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 120 2010-06-28 20:00 .
drwxr-xr-x 6 root root 120 2010-06-28 20:00 ..
lrwxrwxrwx 1 root root  10 2010-06-28 20:00 36016408-d426-4284-83d7-695828a9b146 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2010-06-28 20:00 40bb79a6-87db-45e8-a8a5-e5f3854e46a1 -> ../../sdd5
lrwxrwxrwx 1 root root  28 2010-06-30 21:59 5c6fc833-559b-4156-8da1-765b6edeacab -> ../../mapper/scsiLVM-scsiLVM
lrwxrwxrwx 1 root root  10 2010-06-28 20:00 a3c7ba39-57e4-4357-9f71-103cf1d17ac9 -> ../../sdg1

```

The other concerning thing is that /dev/sde1 and /dev/sdf1 (the RAID disks in question) are NOT LVM2.  They're RAID1 XFS.

---

### Post by fowie on 2010-07-10
ok, looks like when I re-mirrored the drives it mirrored something old, when I was using LVM.  I've grabbed the LVM info off the old drive, and gotten a file I can use for vgcfgrestore.  However, one of the pv's in the vg has a UID (of course), and it doesn't match my 500GB drive because, well, as we've read earlier in this thread, I _don't_ have a UID for this drive.  Can anyone tell me why these two drives do not have UID's in /dev/disk/by-uuid or blkid???

---

