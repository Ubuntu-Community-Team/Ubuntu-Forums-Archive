---
title: "Ubuntu Server 10.04 - Odd mount mystery"
date: 2010-05-14
forum: Server Platforms
---

### Post by rjb-356 on 2010-05-14
Ubuntu Server 10.04 - If I attempt to auto mount NTFS drives via /etc/fstab (as follows)

*** Start fstab file ***
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=bc9cd652-30b8-470e-9366-13b9fa703206 /               ext3    errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0	0       1
# swap was on /dev/sda11 during installation
UUID=a9e2d141-c69c-4241-a195-86730bab86cc none            swap    sw              0       0

/dev/sdb7	/media/dat2-bmc-svr-2	ntfs	defaults	0	0
/dev/sdb11	/media/data-bmc-svr-2	ntfs	defaults	0	0
/dev/sda5	/media/osbu-bmc-svr-2	ntfs	defaults	0	0
/dev/sdb8	/media/pdat-bmc-svr-2	ntfs	defaults	0	0
/dev/sda1	/media/swbu-bmc-svr-2	ntfs	defaults	0	0
*** End fstab file ***

The boot will fail with the error:

*** Start Error message ***
NTFS signature is missing.
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
mountall: mount /media/osbu-bmc-svr-2 [755] terminated with status 12
mountall: Filesystem could not be mounted: /media/osbu-bmc-svr-2
init: ureadable-other main process (839) terminated with status 4
*** End Error message ***

If I comment out the /dev/sda5 line in /etc/fstab, the Server boots, requests username and password, accepts and ends with an appropriate prompt.

Then I can type:

sudo mount -t ntfs /dev/sda5 /media/osbu-bmc-svr-2

the osbu-bmc-svr-2 ntfs drive is mounted without problems.

I can't figure out what I'm doing wrong?

Additional information - here is the response to "sudo fdisk -l"

*** Start "sudo fdisk -l" response ***
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1a48a5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        9514    76413172+   7  HPFS/NTFS
/dev/sda2            9515       30401   167774827+   f  W95 Ext'd (LBA)
/dev/sda5            9515       30401   167774796    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091f9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdb2            2612       60801   467411144+   f  W95 Ext'd (LBA)
/dev/sdb5            2612        3394     6289416   83  Linux
/dev/sdb6            4048        5614    12586896   83  Linux
/dev/sdb7            5615       44777   314576766    7  HPFS/NTFS
/dev/sdb8           46965       60018   104856223+   7  HPFS/NTFS
/dev/sdb9           60019       60801     6289416    7  HPFS/NTFS
/dev/sdb10           3395        4047     5245191   82  Linux swap / Solaris
/dev/sdb11          44778       46964    17567046    7  HPFS/NTFS

Partition table entries are not in disk order
*** End "sudo fdisk -l" response ***

Any help would be appreciated.  I obviously have a simple work-around, but it would be nice to solve this and auto-mount all drives.

TIA,

RJB

---

### Post by rjb-356 on 2010-05-14
I should add that I'm using the 64 bit version of Ubuntu Server 10.04.

---

### Post by tgalati4 on 2010-05-14
Replace all of your /dev/sdXX entries with UUID entries.  To get the UUID for a device:

blkid /dev/sda1
blkid /dev/sda2 
.
.

---

### Post by rjb-356 on 2010-05-14
tgalati4,  

Thanks for the reply.  I will make the changes and report the results.

RJB

---

### Post by rjb-356 on 2010-05-14
tgalati4, 

Well, it sounded so right I couldn't help myself and just made the recommended changes and auto mount through the /etc/fstab file works when the description is changed from /dev/sdxx with UUID=xxxxxxxxxxxxx.  Wow!

Thanks.

I do have to ask if there is a "simple" explanation why one form of description (/dev/sdxx) works sometimes in the /etc/fstab file and when it didn't using a "mount -t" command with the same description (/dev/sdxx) at the command-line works.  Or why the "UUID=" always works in the /etc/fstab file?  Just curious at this point, but more importantly happy to have resolved the "problem" for me, on my server.

Thanks again,

RJB

---

