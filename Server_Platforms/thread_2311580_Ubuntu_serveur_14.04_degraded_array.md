---
title: "Ubuntu serveur 14.04 degraded array"
date: 2016-01-28
forum: Server Platforms
---

### Post by brother-bernard on 2016-01-28
Hello,

I am running Ubuntu server 14.04 on a server named dev, which sends me every day, since 1rst of November 2015, a nice message :
```
This is an automatically generated mail message from mdadm running on dev
A DegradedArray event had been detected on md device /dev/md/2.
Faithfully yours, etc.
P.S. The /proc/mdstat file currently contains the following:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda3[3] sdb3[2](F)
     484152128 blocks super 1.2 [2/1] [_U]
md1 : active raid1 sda2[3] sdb2[2]
     195392 blocks super 1.2 [2/2] [UU]
md0 : active raid1 sda1[3] sdb1[2]
     3903424 blocks super 1.2 [2/2] [UU]
md3 : active raid1 sdd1[1] sdc1[0]
     976630336 blocks super 1.2 [2/2] [UU]
unused devices: <none>
```
From 6th of November, the message was a bit modified on the line md2 (may be after a hardware reboot ?) :
```
md2 : active raid1 sda3[3]
     484152128 blocks super 1.2 [2/1] [_U]

```
Le sdb3 partition seems lost ! It does not matter since there was nothing important on the RAID partition md2 whose content has been moved elsewhere.
The lsblk command gives :
```
root@dev:~# lsblk
NAME                     MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                        8:0    0 465,8G  0 disk  
&#9500;&#9472;sda1                     8:1    0   3,7G  0 part  
&#9474; &#9492;&#9472;md0                    9:0    0   3,7G  0 raid1 [SWAP]
&#9500;&#9472;sda2                     8:2    0   191M  0 part  
&#9474; &#9492;&#9472;md1                    9:1    0 190,8M  0 raid1 
&#9492;&#9472;sda3                     8:3    0 461,9G  0 part  
  &#9492;&#9472;md2                    9:2    0 461,7G  0 raid1 
sdb                        8:16   0 465,8G  0 disk  
&#9500;&#9472;sdb1                     8:17   0   3,7G  0 part  
&#9474; &#9492;&#9472;md0                    9:0    0   3,7G  0 raid1 [SWAP]
&#9500;&#9472;sdb2                     8:18   0   191M  0 part  
&#9474; &#9492;&#9472;md1                    9:1    0 190,8M  0 raid1 
&#9492;&#9472;sdb3                     8:19   0 461,9G  0 part  
sdc                        8:32   0 931,5G  0 disk  
&#9492;&#9472;sdc1                     8:33   0 931,5G  0 part  
  &#9492;&#9472;md3                    9:3    0 931,4G  0 raid1 
    &#9500;&#9472;vg-root (dm-0)     252:0    0     5G  0 lvm   /
    &#9500;&#9472;vg-home (dm-1)     252:1    0     5G  0 lvm   /home
    &#9500;&#9472;vg-var (dm-2)      252:2    0 746,9G  0 lvm   /var
    &#9500;&#9472;vg-log (dm-3)      252:3    0     5G  0 lvm   /var/log
    &#9492;&#9472;vg-archives (dm-4) 252:4    0  23,9G  0 lvm   /var/archives
sdd                        8:48   0 931,5G  0 disk  
&#9492;&#9472;sdd1                     8:49   0 931,5G  0 part  
  &#9492;&#9472;md3                    9:3    0 931,4G  0 raid1 
    &#9500;&#9472;vg-root (dm-0)     252:0    0     5G  0 lvm   /
    &#9500;&#9472;vg-home (dm-1)     252:1    0     5G  0 lvm   /home
    &#9500;&#9472;vg-var (dm-2)      252:2    0 746,9G  0 lvm   /var
    &#9500;&#9472;vg-log (dm-3)      252:3    0     5G  0 lvm   /var/log
    &#9492;&#9472;vg-archives (dm-4) 252:4    0  23,9G  0 lvm   /var/archives
sr0                       11:0    1  1024M  0 rom   
sr1                       11:1    1  1024M  0 rom   

```

I would like to rebuild a clean array md2 and not have anymore the mdadm message every day !
My server dev is currently in production and I want to play it safe...
Thank you in advance for any help about this issue.

B. Bernard

---

### Post by TheFu on 2016-01-28
Replace the failed disk.
Check the cables.
Check the controller.
Check the power.

Waiting this long is highly concerning. Should have addressed this the first day that email arrived for a production system. Seriously.

BTW, I hope you have backups from before this issue started. All that data could be lost.

So - find the root cause of the issue from the list above. Fix it.  Create a backup (3rd or 4th copy) of the data, remove md2 and recreate it.  Restore the data from the backup. Done.  This method will almost certainly result in a faster restore to a protected RAID.

Or you can find the root cause of the issue from the list above. Fix it.  Create a backup (3rd or 4th copy) of the data, then run some mdadm commands to force the still working part of that array-set to re-sync with the new storage.  For large disks, there is a risk that the primary drive will fail during this operation. That is theory. I've never seen it. If the issue is the disk, replace it with an identical disk. Might be easier to replace both the pri/mirror disks. If they are over 4 yrs old, I would. This is a production box, right? Data is important - especially since it is RAID1.

RAID doesn't remove the need for backups. Never has. Never will.

Once this issue is fixed, the email messages will stop.


So - I used to have a disk that got disconnected from an array due to bad SATA cable connections. This happened about once a month due to vibrations.  The disk was fine, just the cable was an issue.  Eventually, I replaced all the cables with 90 deg plugs and never had another issue. The first time I happened, I freaked out (as anyone would).  Wrote some notes so I wouldn't have to do the research over and over every time.  Below are my notes, for my system. From them you can figure out what to do for yours:
```

#
# These are notes, NOT A SCRIPT. Do not run it.  Copy/paste and modify the commands for the specific system.
#

# Review the Array config - Missing/Failed
sudo mdadm --detail /dev/md0

# umount the filesystem
umount /raid5

# Verify that the failed drive is seen by the OS - look for the partitions
ls -l /dev/sd*1

# if there is missing - power down the array and check connections
#
# Usually, it is /dev/sdf1 that lost a connection. ADD it back
sudo mdadm /dev/md0 -a /dev/sdf1
# If none of those methods work, you may need to check the array devices
# in /etc/mdadm/mdadm.conf and force it to assemble.
sudo mdadm --assemble /dev/md0 -v --force

# mount the array
sudo mount -a

# ##############################################
# RAID Maintenance - weekly
echo check > /sys/block/mdX/md/sync_action
echo repair > /sys/block/mdX/md/sync_action
# After, look at the syslog for any errors.
egrep -i 'error|warn'  /var/log/syslog  | more
```

Hope that helps.

---

### Post by darkod on 2016-01-28
We don't know the disk has failed, and there is no important data to try to save from the array (if I understood it correctly). Other arrays use sdb1 and sdb2 from the same disk and show no failed members. It could be simply that sdb3 dropped from the md2 array at one point.

Since you said you do not even care to try assembling the array, I would do the following:
1. Unmount md2 (in case it's mounted).
2. Stop md2.
3. Zero the superblocks of sda3 and sdb3 (to remove superblock data of current array).
4. Create new md2 array.
5. Format md2.
6. Mount it and use it.

Watch out if messages of failed sdb3 start showing up again, the disk might be damaged only where that partition is located. In such case you would need to replace the whole disk.

---

### Post by brother-bernard on 2016-01-29
Thank you very much for your answers.

@TheFu : Yes, I have daily backups on a Synology NAS.

@darkod : Yes, the disk hasn't failed. What I have done : First, a clean install of Ubuntu server 14.04 with RAID1 on 2 disks (750 GB) with 3 partitions md0, md1 and md2. LVM on md2. Later 2 disks (1 TB) were added in RAID1, sdc and sdd assembled in md3. The all partition md2 was copied into md3. The md2 is now unused ! The issue has apparead after but I don't notice the exact time...

If I follow your advice, are these commands correct ?
1. umount md2
2. sudo mdadm --stop /dev/md2
3. sudo mdadm --zero-superblock /dev/sda3
sudo mdadm --zero-superblock /dev/sdb3
4. sudo mdadm --create /dev/md2 --level=1 --raid-devices=2 /dev/sda3 /dev/sdb3
sudo mdadm --assemble /dev/md2 /dev/sda3 /dev/sdb3 (is necessary ?)
5. sudo mkfs.ext4 /dev/md2
6. mount md2

What about mdadm.conf ? No change ?

Below, some results of commands :
```
root@dev:~# mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Sun Sep 14 15:09:40 2014
     Raid Level : raid1
     Array Size : 484152128 (461.72 GiB 495.77 GB)
  Used Dev Size : 484152128 (461.72 GiB 495.77 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jan  3 00:57:26 2016
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : dev:2  (local to host dev)
           UUID : 72ef70a3:cc3b099a:767360e8:76cd6228
         Events : 18208

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       3       8        3        1      active sync   /dev/sda3

root@dev:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sun Sep 14 15:09:31 2014
     Raid Level : raid1
     Array Size : 195392 (190.84 MiB 200.08 MB)
  Used Dev Size : 195392 (190.84 MiB 200.08 MB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sun Jan  3 00:57:26 2016
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : dev:1  (local to host dev)
           UUID : 28c8eb8d:470ca4e4:0eae6232:5e1c77d0
         Events : 129

    Number   Major   Minor   RaidDevice State
       2       8       18        0      active sync   /dev/sdb2
       3       8        2        1      active sync   /dev/sda2


root@dev:~# ls -l /dev/sdb3
brw-rw---- 1 root disk 8, 19 déc.  14 19:17 /dev/sdb3
root@dev:~# ls -l /dev/sda3
brw-rw---- 1 root disk 8, 3 déc.  14 19:17 /dev/sda3


```

Thank you again for your help !
B. Bernard

---

### Post by darkod on 2016-01-29
Hold on... You say you had/have LVM on md2. And then you added md3. Is md2 still part of the LVM? Are there different volume groups on md2 and md3 or the same group?

If it's part of LVM you can't simply get rid of it like that. In fact some data might still be on it.

If you have LVM please show:
```
sudo pvdisplay
sudo vgdisplay
df -h
```

---

### Post by brother-bernard on 2016-01-30
Thank you for your help.
As a matter of fact, I have not added the 1TB raid and the person who did it is not reachable now. I can't answer your question about the LVM on md2. Perhaps that is the question !
Below, the commands you requested me to play :

```
cell@dev:~$ sudo pvdisplay
[sudo] password for cell: 
  --- Physical volume ---
  PV Name               /dev/md2
  VG Name               vg
  PV Size               461,72 GiB / not usable 4,81 MiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              118200
  Free PE               118200
  Allocated PE          0
  PV UUID               RiBJX5-8c1b-tOcf-u25D-VI1P-BRlK-k14Cwc
   
  --- Physical volume ---
  PV Name               /dev/md3
  VG Name               vg
  PV Size               931,39 GiB / not usable 4,56 MiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              238434
  Free PE               37287
  Allocated PE          201147
  PV UUID               jzlGTw-RS6Z-kOrl-aB5O-MR0o-ahge-ykH2bn

cell@dev:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               vg
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  83
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                5
  Open LV               5
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1,36 TiB
  PE Size               4,00 MiB
  Total PE              356634
  Alloc PE / Size       201147 / 785,73 GiB
  Free  PE / Size       155487 / 607,37 GiB
  VG UUID               fRqq1H-IOWV-FBgM-UVGb-E1fw-g7xe-bdEj6V

cell@dev:~$ df -h
Sys. de fichiers        Taille Utilisé Dispo Uti% Monté sur
udev                      990M    8,0K  990M   1% /dev
tmpfs                     201M    716K  200M   1% /run
/dev/mapper/vg-root       4,8G    2,8G  1,8G  62% /
none                      4,0K       0  4,0K   0% /sys/fs/cgroup
none                      5,0M       0  5,0M   0% /run/lock
none                     1001M       0 1001M   0% /run/shm
none                      100M       0  100M   0% /run/user
/dev/mapper/vg-home       4,8G     43M  4,5G   1% /home
/dev/mapper/vg-var        735G    628G   76G  90% /var
/dev/mapper/vg-log        4,8G    174M  4,4G   4% /var/log
/dev/mapper/vg-archives    24G     19G  4,4G  81% /var/archives

```

It seems that it remains something about lvm on the md2 partition, isn't it ?
Thank you.

---

### Post by darkod on 2016-01-30
Yes, md2 is part of the LVM in the volume group vg. But right now it is not used, you can see all extents are free in the pvdisplay output for md2:
```
Total PE 118200
Free PE 118200
```

So, if you want to remove md2 from the LVM this is the perfect moment because you can't remove from LVM a physical volume that has used extents. However consider this: Right now you have 5 logical volumes in the vg group, including root, home, var, var log, etc. The total size of vg is 1.36TB which includes 461GB from md2 and 931GB from md3. Removing md2 from vg will leave you only a maximum size of 931GB that is on md3. If you need to extend any logical volume(s) in the future the total size of all LVs can't pass 931GB. That will be your maximum.

So if you need to keep vg at 1.36TB there is no point removing md2, redoing the array and putting it back into the LVM. Better to simply repair the current md2 array and leaving it part of vg.

That is the next question for you: Do you still want to remove md2 from the LVM knowing that it will limit the max size of your VG to 931GB? Is that enough for you?

Depending on the answer, we will consider future actions...

---

### Post by brother-bernard on 2016-01-30
Thank you for your fast answer ! I appreciate greatly !
Today, I don't need 1.36 TB, but tomorrow..., it would be better to have this space included inside LVM. No ? So, I think it is better to repair the md2 array than delete it.
AppleUpdates and Munki are installed on this server, among others apps. Their sizes in GB are important and constantly growing.
Thank you to hold my hand in this risky repair :)
Completely rebuilt this server would be a pain !

---

### Post by darkod on 2016-01-30
OK then... Repairing the array should be quite easy in this situation.

As you see in your first post, in the first emails it said sdb3 is with failed (F) status and then from 6th November it removed it from the array, only sda3 is showing in md2 now.

It should be easy to add sdb3 back but you have to zero the superblock first because it will get confused, it knows it was part of the array but is now out of sync. Try this:
```
sudo mdadm --zero-superblock /dev/sdb3
sudo mdadm /dev/md2 --verbose --add /dev/sdb3
cat /proc/mdstat
```

With the mdstat you can check if sdb3 was added and is it syncing. That should do it.

---

### Post by brother-bernard on 2016-01-30
I just play the commands mdadm and md2 is syncing correctly.

[code]cell@dev:~$ sudo mdadm --zero-superblock /dev/sdb3
[sudo] password for cell: 
cell@dev:~$ sudo mdadm /dev/md2 --verbose --add /dev/sdb3
mdadm: added /dev/sdb3
cell@dev:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb2[2] sda2[3]
      195392 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sdb3[2] sda3[3]
      484152128 blocks super 1.2 [2/1] [_U]
      [>....................]  recovery =  0.3% (1689024/484152128) finish=52.3min speed=153547K/sec
      
md0 : active raid1 sda1[3] sdb1[2]
      3903424 blocks super 1.2 [2/2] [UU]
      
md3 : active raid1 sdd1[1] sdc1[0]
      976630336 blocks super 1.2 [2/2] [UU]
[code]

I will put the mention **solved** when the syncing will be complete.
Thank you very much for your great help !
Have a good weekend !


cell@dev:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb2[2] sda2[3]
      195392 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sdb3[2] sda3[3]
      484152128 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sda1[3] sdb1[2]
      3903424 blocks super 1.2 [2/2] [UU]
      
md3 : active raid1 sdd1[1] sdc1[0]
      976630336 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

All is OK ! Thank you again.

---

### Post by darkod on 2016-01-30
No problem. Glad it worked out OK.

---

