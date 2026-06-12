---
title: "External Drive Mounts Read-Only"
date: 2013-09-08
forum: Server Platforms
---

### Post by Josh_Sipahigil on 2013-09-08
I apologize if this has already been posted—if someone could direct me to the post I would greatly appreciate it. I've checked throughout the forum/Google under every query I can think of to find results related to my issue, but all of the results seem centered around mounting NTFS partitions and none of the resolutions have worked for me.

I have a 3TB external media storage drive connected to my Ubuntu Server 12.04.3 installation. The issue is that it always mounts with the incorrect permissions. I've followed the suggestions in this thread [http://ubuntuforums.org/showthread.php?t=2171268](http://ubuntuforums.org/showthread.php?t=2171268), however the fstab entry suggested there (below) causes an error (also below) when I try to mount my drive.

fstab entry mentioned above:
```
UUID=af257147-219f-4f55-a4c9-a7adcb7047bc    /media/BGDRV01/    ext4    errors=remount-ro,uid=1000,gid=50514,fmask=002,dmask=002           0      0
```

Error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Here are the details of my filesystem as it stands now (I commented out the fstab entry above in lieu of my original entry which at least mounted the drive). The drive will currently mount, but with the permissions below:

ls -l results of the mount point:
```
drwxrwx---+ 8 root root 4096 Sep  6 01:59 BGDRV01
```

fdisk -l
```
Disk /dev/sdb: 3000.6 GB, 3000558944256 bytes166 heads, 6 sectors/track, 735500 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x103420cf


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256   732558335  2930232320   83  Linux
```

blkid for the drive
```
/dev/sdb1: UUID="af257147-219f-4f55-a4c9-a7adcb7047bc" TYPE="ext4"
```

...and the original entry in my fstab
```
UUID=af257147-219f-4f55-a4c9-a7adcb7047bc    /media/BGDRV01/  ext4    relatime,noexec           0      0

```

Essentially, my question is: how can I get this drive to mount with 0755 permissions so my Plex installation can read my media on boot?
I considered an upstart cron job to chown/chmod/chgrp after the drive at boot, but there has to be a cleaner way of doing that. For now I've been changing the drive permissions after mount, but that obviously only sticks until a reboot and leaves my media inaccessible if I forget before leaving the house.

Let me know if I can provide more details—and thanks in advance.

---

### Post by zero2xiii on 2013-09-08
Hay,

I think you can try:
```
UUID=af257147-219f-4f55-a4c9-a7adcb7047bc    /media/BGDRV01/    ext4    errors=remount-ro,fmask=0755,dmask=0755           0      0
```
Or:
```
UUID=af257147-219f-4f55-a4c9-a7adcb7047bc    /media/BGDRV01/    ext4    errors=remount-ro,owner           0      0
```

If neither of them work I am at a loss.

Cheers

---

### Post by redmk2 on 2013-09-08
> **Josh_Sipahigil said:**
> I apologize if this has already been posted&#8212;if someone could direct me to the post I would greatly appreciate it. I've checked throughout the forum/Google under every query I can think of to find results related to my issue, but all of the results seem centered around mounting NTFS partitions and none of the resolutions have worked for me.

I have a 3TB external media storage drive connected to my Ubuntu Server 12.04.3 installation. The issue is that it always mounts with the incorrect permissions. I've followed the suggestions in this thread [http://ubuntuforums.org/showthread.php?t=2171268](http://ubuntuforums.org/showthread.php?t=2171268), however the fstab entry suggested there (below) causes an error (also below) when I try to mount my drive.

fstab entry mentioned above:
```
UUID=af257147-219f-4f55-a4c9-a7adcb7047bc    /media/BGDRV01/    ext4    errors=remount-ro,uid=1000,gid=50514,fmask=002,dmask=002           0      0
```

Error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Here are the details of my filesystem as it stands now (I commented out the fstab entry above in lieu of my original entry which at least mounted the drive). The drive will currently mount, but with the permissions below:

ls -l results of the mount point:
```
drwxrwx---+ 8 root root 4096 Sep  6 01:59 BGDRV01
```

fdisk -l
```
Disk /dev/sdb: 3000.6 GB, 3000558944256 bytes166 heads, 6 sectors/track, 735500 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x103420cf


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256   732558335  2930232320   83  Linux
```

blkid for the drive
```
/dev/sdb1: UUID="af257147-219f-4f55-a4c9-a7adcb7047bc" TYPE="ext4"
```

...and the original entry in my fstab
```
UUID=af257147-219f-4f55-a4c9-a7adcb7047bc    /media/BGDRV01/  ext4    relatime,noexec           0      0

```

Essentially, my question is: how can I get this drive to mount with 0755 permissions so my Plex installation can read my media on boot?
I considered an upstart cron job to chown/chmod/chgrp after the drive at boot, but there has to be a cleaner way of doing that. For now I've been changing the drive permissions after mount, but that obviously only sticks until a reboot and leaves my media inaccessible if I forget before leaving the house.

Let me know if I can provide more details&#8212;and thanks in advance.

Off the top of my head I would say the either the file system is damaged or the drive itself is damaged.  If a file system has errors the OS will mount it read only until you repair the errors or replace the disk.  I would try running *fsck* on that partition before mounting it. ```
sudo fsck /dev/sdb1
```

---

### Post by Josh_Sipahigil on 2013-09-08
Thank you both for the help&#8212;I was able to use the "owner" flag in the fstab listing to get the permissions correct, however it looks like the issue is actually the Zentyal Samba module changing the drive permissions when it loads the share point. Everything stays as it should after a restart with the Samba module disabled... guess I'll start digging into that. 

Thanks again.

---

