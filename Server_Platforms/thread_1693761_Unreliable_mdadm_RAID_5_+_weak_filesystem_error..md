---
title: "Unreliable mdadm RAID 5 + weak filesystem error."
date: 2011-02-23
forum: Server Platforms
---

### Post by Coder68 on 2011-02-23
I have built and rebuild my RAID 5 several times and each time it only last for a few reboots before I have to reboot many times to get it to come up. This all started after I did an update and started to get a weak filesystem error. Not sure exactly when it bit me as I do am still learning this stuff and I do not have it in "production" and do not work on it everyday due to work, school and a life. :)

The error I get when it starts to not come up is about md1 (raid 5) not being ready I can wait, skip or manually recover. (Oddly this does not show up in the boot log.)

Here are my relevant logs. (I waited for a decent amount of time and then skipped the auto mount.) If you need more or different logs, just let me know which ones.


fstab:
[PHP]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0p1 during installation
UUID=c796c793-585d-485c-94b7-28dfeee88cc8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md0p5 during installation
UUID=621d6209-9b9e-443e-ba30-99933de47aef none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.2.101/public  /mnt/nas1  cifs  password=password,username=us104  0  0
/dev/md1  /mnt/r5  ext3  defaults  0  0

# I commented out line 12 and 15 to try and fix raid5 and the one below 
# I uncommented all  to auto mount raid again and the swap file.
 /mnt/r5/Movies  /srv/nfs4/Movies  bind  bind  0  
[/PHP] cold boot log:
[PHP]fsck from util-linux-ng 2.17.2
/dev/md0p1: clean, 130131/8986624 files, 1014526/35943680 blocks (check after next mount)
init: ureadahead-other main process (945) terminated with status 4
init: ureadahead-other main process (946) terminated with status 4
Skipping /mnt/r5 at user request
 * Starting AppArmor profiles                                            [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/srv/nfs4/Movies".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x
[/PHP]mdstat log cold boot:
[PHP]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d1 : inactive sdc[3](S)
      1953514496 blocks
       
md0 : active raid1 sdd1[0] sdf1[1]
      149903296 blocks [2/2] [UU]
      
md1 : inactive sdb[2](S) sdg[1](S) sde[0](S)
      5860543488 blocks
       
unused devices: <none>
[/PHP]mdstat log 1st reboot:
[PHP]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d1 : inactive sda[4](S)
      1953514496 blocks
       
md0 : active raid1 sdf1[1] sdd1[0]
      149903296 blocks [2/2] [UU]
      
md1 : inactive sde[0](S) sdb[2](S) sdg[1](S)
      5860543488 blocks
       
unused devices: <none>
[/PHP]Notice how the inactive md_d1 device keeps changing?

My RAID 5 should have these drives in it:
sdb
sdd
sde
sdf
sdg

I am also getting an "unmounting week filesystems" when I reboot.  I was not having issues with my RAID 5 until I started to get this. I deleted the array and completely rebuilt it, but after just a few reboots I am back to it not mounting and drives not being active unless I reboot a bunch of times.

mdstat 4th reboot:
[PHP]cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc1[1] sda1[0]
      149903296 blocks [2/2] [UU]
      
md1 : active raid5 sdg[3] sdf[2] sde[4] sdd[1] sdb[0]
      7814057984 blocks level 5, 4k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>
[/PHP]4th boot boot log:
[PHP]fsck from util-linux-ng 2.17.2
/dev/md0p1: clean, 130136/8986624 files, 1014711/35943680 blocks
init: ureadahead-other main process (942) terminated with status 4
init: ureadahead-other main process (944) terminated with status 4
 * Starting AppArmor profiles                                            [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/srv/nfs4/Movies".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x
[/PHP]Questions:
1. Why does it take so many reboots for my RAID to be seen? (All drive show activity at boot.)
2. What is this, and how do I fix it? > /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/srv/nfs4/Movies".3. Why am I getting a unmounting sweek filesystems at reboot/shutdown (I have seen that many are bit by this bug) and is there anything I can do about it? (When my issues with my RAID started!!!) I started to get this error right after an update. Not sure which update though.
4. What is this and how do I fix it?>  init: ureadahead-other main process (942) terminated with status 4Thanks for the help,

C68

---

### Post by rubylaser on 2011-02-23
1. It looks like your RAID setup is wrong.  A few of your disks are in /dev/md0 and the other discs are in /dev/md1.  I'd probably stop both arrays, zero the superblocks on all of those drives, clear out your /etc/mdadm/mdadm.conf file, Reboot, and then setup the md array again.

2. The no_subtree_check is just an NFS export option that you need to add to your /etc/exports like this...
```
/var/marketing  10.1.1.0/24(rw,async,insecure,[COLOR="Red"]no_subtree_check[/COLOR])
```

3. This can happen because you need to run a fsck on the partition.
[http://ubuntuforums.org/showthread.php?t=1578000]("http://ubuntuforums.org/showthread.php?t=1578000")

4. This looks like a bug that Upstart is displaying these error messages.
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677")

---

### Post by rubylaser on 2011-02-23
Can you paste in the info from each of your disks from this command...
```
mdadm -E /dev/sdb1
```

And, also what do you have in your /etc/mdadm/mdadm.conf file?

---

### Post by dtfinch on 2011-02-23
I'd add the array lines outputted by mdadm -Es to the end of your mdadm.conf if they're not added already, or I think you can run "/usr/share/mdadm/mkconf > /etc/mdadm/mdadm.conf" to recreate it from scratch. If you don't list your arrays, it relies on autoassembly, which lately (in 10.04 at least) has had a bug where it'd randomly steal a drive to construct an inactive rogue array (like md_d0 or md_d1).

After updating mdadm.conf, you might need to run "update-initramfs -u -k `uname -r`" to update it to the early boot ramdisk.

---

### Post by Coder68 on 2011-02-23
Rubylaser:

I used webmin to create the RAID 5. I installed Ubuntu and created the RAID 1 at the same time. 

sda1 1st part of my RAID 1:

[PHP]sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c9396871:55e63817:84b59cf9:6247ed1d
  Creation Time : Wed Nov 24 10:34:03 2010
     Raid Level : raid1
  Used Dev Size : 149903296 (142.96 GiB 153.50 GB)
     Array Size : 149903296 (142.96 GiB 153.50 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Feb 23 19:58:53 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 528cb2d0 - correct
         Events : 65924


      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       33        1      active sync   /dev/sdc1
[/PHP]sdac: 2nd part of my RAID 1:

[PHP]/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c9396871:55e63817:84b59cf9:6247ed1d
  Creation Time : Wed Nov 24 10:34:03 2010
     Raid Level : raid1
  Used Dev Size : 149903296 (142.96 GiB 153.50 GB)
     Array Size : 149903296 (142.96 GiB 153.50 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Feb 23 20:00:26 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 528cb34f - correct
         Events : 65924


      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       33        1      active sync   /dev/sdc1
[/PHP]1st part of RAID 5:

[PHP]/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e509485d:97ef7ead:d14ee5ec:eb91e22c (local to host us104)
  Creation Time : Sat Feb 19 22:07:42 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1

    Update Time : Wed Feb 23 09:16:38 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f23b4af9 - correct
         Events : 15674

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       48        1      active sync   /dev/sdd
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8       96        3      active sync   /dev/sdg
   4     4       8       64        4      active sync   /dev/sde
[/PHP]sdd 2nd part of RAID 5:

[PHP]/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e509485d:97ef7ead:d14ee5ec:eb91e22c (local to host us104)
  Creation Time : Sat Feb 19 22:07:42 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1

    Update Time : Wed Feb 23 09:16:38 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f23b4b1b - correct
         Events : 15674

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     1       8       48        1      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       48        1      active sync   /dev/sdd
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8       96        3      active sync   /dev/sdg
   4     4       8       64        4      active sync   /dev/sde
[/PHP]sde 3rd part of RAID 5:

[PHP]/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e509485d:97ef7ead:d14ee5ec:eb91e22c (local to host us104)
  Creation Time : Sat Feb 19 22:07:42 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1

    Update Time : Wed Feb 23 09:16:38 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f23b4b31 - correct
         Events : 15674

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     4       8       64        4      active sync   /dev/sde

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       48        1      active sync   /dev/sdd
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8       96        3      active sync   /dev/sdg
   4     4       8       64        4      active sync   /dev/sde
[/PHP]sdf 4th part of RAID 5:

[PHP]/dev/sdf:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e509485d:97ef7ead:d14ee5ec:eb91e22c (local to host us104)
  Creation Time : Sat Feb 19 22:07:42 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1

    Update Time : Wed Feb 23 09:16:38 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f23b4b3d - correct
         Events : 15674

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     2       8       80        2      active sync   /dev/sdf

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       48        1      active sync   /dev/sdd
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8       96        3      active sync   /dev/sdg
   4     4       8       64        4      active sync   /dev/sde
[/PHP]sdg 5th part of RAID 5:

[PHP]/dev/sdg:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e509485d:97ef7ead:d14ee5ec:eb91e22c (local to host us104)
  Creation Time : Sat Feb 19 22:07:42 2011
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 7814057984 (7452.07 GiB 8001.60 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 1

    Update Time : Wed Feb 23 09:16:38 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f23b4b4f - correct
         Events : 15674

         Layout : left-symmetric
     Chunk Size : 4K

      Number   Major   Minor   RaidDevice State
this     3       8       96        3      active sync   /dev/sdg

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       48        1      active sync   /dev/sdd
   2     2       8       80        2      active sync   /dev/sdf
   3     3       8       96        3      active sync   /dev/sdg
   4     4       8       64        4      active sync   /dev/sde
[/PHP]I did not notice that the drive letters are wrong, ie sda vs sdb.  The size seems correct though.  My two drives for / are 160 gig's. Why would it rearange the drive "letters"?

here is my mdadm/.conf:

[PHP]cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions /dev/sdg /dev/sde

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c9396871:55e63817:84b59cf9:6247ed1d

# This file was auto-generated on Wed, 24 Nov 2010 11:01:16 -0500
# by mkconf $Id$
DEVICE /dev/sda /dev/sdc
DEVICE /dev/sdg
DEVICE /dev/sdb /dev/sdd /dev/sdf /dev/sdg
ARRAY /dev/md1 level=raid5 devices=/dev/sdb,/dev/sdd,/dev/sdf,/dev/sdg,/dev/sde
[/PHP]So if I add this array /dev/md1 to the fstab it will always use these devices in the RAID 5?  What exactly should my fstab then look like?

I have tried the forced check of the filesystem but no go.  I did add the cifs line manually, but it does not have spaces in it as some suggest is the issue.

I made the change to my /etc/exports file.

> /srv/nfs4/Movies    *(sync,rw,no_subtree_check)
# added ,no_subtree_check to line 11 based on post in ubuntu forum How does this look? I will be rebooting tomorrow.

Thank you for the help.

C68

---

### Post by YesWeCan on 2011-02-23
Your mdadm.conf looks pretty messed up to me.
I think it should look more like this:
[COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][/COLOR]```
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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c9396871:55e63817:84b59cf9:6247ed1d

ARRAY /dev/md1 level=raid5 num-devices=5 UUID=e509485d:97ef7ead:d14ee5ec:eb91e22c

# This file was auto-generated on Wed, 24 Nov 2010 11:01:16 -0500
# by mkconf $Id$
```

At the moment it is trying to assemble your RAID 5 based on dev names. These can get changed by the bios on reboots. So UUIDs are much more reliable.

---

### Post by Vegan on 2011-02-23
Read my paper on RAID

[http://www.windows-it.tk/papers/raid.php](http://www.windows-it.tk/papers/raid.php)

---

### Post by Coder68 on 2011-02-23
I wondered about that. > These can get changed by the bios on reboots. That would explain why the drives device names kept changing!  I take it that the UUID is tied to the drive so it knows which drives are associated with this UUID?

> [COLOR=#000000][COLOR=#007700]/[/COLOR][COLOR=#0000bb]dev[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]sdb[/COLOR][COLOR=#007700]:
          [/COLOR][COLOR=#0000bb]Magic [/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]a92b4efc
        Version [/COLOR][COLOR=#007700]: [/COLOR][COLOR=#0000bb]00.90.00
          [COLOR=Red] UUID [/COLOR][/COLOR][COLOR=Red][COLOR=#007700]: [/COLOR][COLOR=#0000bb]e509485d[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000bb]97ef7ead[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000bb]d14ee5ec[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#0000bb]eb91e22c [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]local to host us104[/COLOR][COLOR=#007700])[/COLOR][/COLOR][/COLOR]I have made a backup of my fstab and will make this change tonight and shutdown at bed time.  I will then test in the morning.

Thanks!

---

### Post by YesWeCan on 2011-02-23
> **Coder68 said:**
> I wondered about that.  That would explain why the drives device names kept changing!  I take it that the UUID is tied to the drive so it knows which drives are associated with this UUID?
Yes, that's right. The 'DEVICE partitions' tells mdadm to look up all the devices listed in /proc/partitions and then it assembles the arrays using those devices and partitions that have the correct UUID as defined in the ARRAY directives.

---

### Post by Coder68 on 2011-02-24
OK, now that I am awake...

This is what I have come up with for my new fstab:

[PHP]# mdadm.conf
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
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c9396871:55e63817:84b59cf9:6247ed1d

ARRAY /dev/md1 level=raid5 num-devices=5 UUID=e509485d:97ef7ead:d14ee5ec:eb91e22c

# Auto mount points:
# RAID 5
/dev/md1  /mnt/r5  ext3  defaults  0  0
# NFS exports:
/mnt/r5/Movies  /srv/nfs4/Movies  bind  bind  0 
# NAS1:
//192.168.2.101/public  /mnt/nas1  cifs  password=password,username=us104  0  0


# This file was auto-generated on Wed, 24 Nov 2010 11:01:16 -0500
# by mkconf $Id$[/PHP]But what about the swap file?

[PHP]# swap was on /dev/md0p5 during installation
UUID=621d6209-9b9e-443e-ba30-99933de47aef none            swap    sw              0       0
[/PHP]And where did it get that UUID? I do not see it on any of the drives. It is partition related? If so, how do I view it?

How does my new fstab look?

Thank you,

C68

---

### Post by YesWeCan on 2011-02-24
No, no, no. :)

You have put your mdadm.conf into fstab.

The mdadm.conf should be in its own file: /etc/mdadm/mdadm.conf

---

### Post by YesWeCan on 2011-02-24
Your /etc/fstab wants to look like this:
```
# <file system>                                <mount point>        <type>      <options>                             <dump>  <pass>
proc                                             /proc               proc    nodev,noexec,nosuid                         0       0

# root and swap on md0 RAID 1
UUID=c796c793-585d-485c-94b7-28dfeee88cc8        /                   ext4    errors=remount-ro                           0       1

UUID=621d6209-9b9e-443e-ba30-99933de47aef        none                swap           sw                                   0       0



/dev/md1                                         /mnt/r5             ext3         defaults                               0       2

/dev/fd0                                         /media/floppy0      auto    rw,user,noauto,exec,utf8                    0       0

//192.168.2.101/public                           /mnt/nas1           cifs    password=password,username=us104            0       0
```


You can start to understand what is going on by running 'sudo blkid'
This lists your partitions by label and UUID and type
The idea of fstab is to decide where in the filesystem to mount some of them at boot up.

fstab is very hard to read. The idiot who wrote the software that generates it didn't think to format it legibly! So I go in and tediously add spaces to it so I can read it.

---

### Post by Coder68 on 2011-02-24
Oops! I had not actually done it, but I was in a hurry when I posted that. I see where I went wrong.

I now understand it much better and it makes sense to me! I have rebooted several times with these changes and have not had any issues with the RAID 5!! 

Thank you soooooooooooo much!

I also fixed the no_subtree_check error. 

OK. Now I just have my dismounting weak filesystem error.  (**RUNNING NOW**) I am going to try the forced fschk again. Once fixed, I will be down to just one random error that makes no sense to me.  I will start a new thread for that one. But just to give you a taste:

Randomly on reboot: mountall: Disconnected from Plymouth.

I have no GUI and the forum seems to point that direction.  Oh well, off to a new thread.

Thanks again so much!

C68

---

### Post by YesWeCan on 2011-02-24
Glad the raid is working. :D
BTW do you back it up regularly?

This might be relevant: [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287)

---

### Post by Coder68 on 2011-02-25
Yes, that looks relevent alright. 

I started getting that after an update...

I do not backup my RAID as of yet.  There is almost nothing on it. I am still in the learning and testing phase, so it only has some test movies on it.  Once I do have all my stuff on it, I will only back up the "It can't be lost no matter what" stuff.  My movies and music can just be re-ripped since I own them. (It would still suck though!)  I do not have the space to back all of that stuff up!  But my "can't be lost no matter what" stuff will fit on a DAT 72 tape. :)

This issue has been reported since August of last year and is marked as high, but is unassigned.  I wonder if they will ever fix this issue.

Thanks again,

C68

edit:
The forced check of the filesystem took a while, but again, it did not fix the issue.  I get the exact same thing that post #8 describes at [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287)

---

