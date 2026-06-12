---
title: "new mounted hard disk  is size too small"
date: 2017-06-11
forum: Server Platforms
---

### Post by secoonder on 2017-06-11
Hello
i am using ubuntu 14.04 LTS. i used only one hard disk until yesterday.
Today, i am add a new hard disk (4 TB).i am mounted new hard disk.

My new hard disk partition is /dev/sdb
My fdisk -l output is:

> root@xxksrvv:~# fdisk -l | grep sdb

Disk /dev/sdb: **4000.8 GB**, 4000787030016 bytes
90 heads, 3 sectors/track, 28940878 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x67046a18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  4294967294  2147482623+  83  Linux


But my df -h output is
 > root@xxksrvv:~# df -h | grep /dev/sdb
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       **2.0T**  1.3T  606G  69% /_myfolder



My sdb disk size is 4 TB. it is true that fdisk -l output.
But df -h output is 2 TB.

what am i wrong ?

---

### Post by oldfred on 2017-06-11
You said you have 14.04.
The version of fdisk in 14.04 does not support gpt drives. Only16.04 or later has a newer fdisk.
You have to use gdisk or parted/gparted and set to gpt and then partition drive.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... (But that was with smaller drives).
I would expect it may default to gpt, but if drive is already MBR(msdos) then it may not.

Or with gdisk
      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) 
    
MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) 


Since very large drive, and gpt. I like to include both an ESP - efi system partition and the bios_grub partition as the first two partitions. If you ever want an install on that drive you need one or the other. Or if moved from an older BIOS system to newer UEFI, then you need the ESP. For about the last 4 years I have added both, originally only needing bios_grub, but now ESP. I even do that with larger flash drives.
And I suggest at least a smaller /(root) partition on drive even if primarily a drive drive. I like to have every drive bootable on its own even if just for emergency repair.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do

---

