---
title: "Worst nightmare. Lost all my files after upgrade"
date: 2020-05-04
forum: Server Platforms
---

### Post by kmneimneh on 2020-05-04
Pardon my first post.

So I have a Supermicro ubuntu server that was shipped with ubuntu 16.04 I upgraded a while to 18.04 without any issue. Last night I decided to upgrade to 20.04 ( silly me ) and after restarting, the system will not boot. Kernel panic. I tried to troubleshoot but it won't even go to recovery mode.

Fortunately I had the home partition backed up so I decided to reinstall everything from scratch using 20.04 LTS server live disk. Before I do that, I removed my 2x10TB Raid1 disk because I didn't have a backup for these and it had literally every I have in life.

Everything went straight forward. I booted up ubuntu then attached both disk after powering it off. Once it booted, it detected the Raid1 array as md127. I thought everything was OK but no, when I mount the array, the drives are empty. I only have lost+found folder. I'm literally up since 30 hours trying to find a solution.


```
cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md127 : active raid1 sdd1[1] sdc1[0]
      9766303744 blocks super 1.2 [2/2] [UU]
      bitmap: 0/73 pages [0KB], 65536KB chunk


unused devices: <none>
ubnt@ubnt:/mnt$ cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md127 : active raid1 sdd1[1] sdc1[0]
      9766303744 blocks super 1.2 [2/2] [UU]
      bitmap: 0/73 pages [0KB], 65536KB chunk

```


```
Model: ATA HGST HUH721010AL (scsi)
Disk /dev/sdc: 10.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  10.0TB  10.0TB               primary  raid




Model: ATA HGST HUH721010AL (scsi)
Disk /dev/sdd: 10.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  10.0TB  10.0TB               primary  raid




Model: Linux Software RAID Array (md)
Disk /dev/md127: 10.0TB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:


Number  Start  End     Size    File system  Flags
 1      0.00B  10.0TB  10.0TB  ext4

```





```
ubnt@ubnt:/mnt$ lsblk -f
NAME      FSTYPE            LABEL       UUID                                 FSAVAIL FSUSE% MOUNTPOINT
loop0     squashfs                                                                 0   100% /snap/core/9066
loop1     squashfs                                                                 0   100% /snap/snapd/7264
loop2     squashfs                                                                 0   100% /snap/docker/423
loop3     squashfs                                                                 0   100% /snap/core18/1705
loop4     squashfs                                                                 0   100% /snap/lxd/14804
sda
&#9492;&#9472;sda1    vfat              UBUNTU-SERV 866B-7F5F
sdb
&#9500;&#9472;sdb1
&#9492;&#9472;sdb2    ext4                          65eaefff-7753-4477-9ac3-0ad6c8b86c67   93.6G     9% /
sdc
&#9492;&#9472;sdc1    linux_raid_member ubnt:0      3cebc7c1-c766-7152-9424-f217e9209273
  &#9492;&#9472;md127 ext4                          36c839d5-f205-4ae0-919c-c1582ce73e23
sdd
&#9492;&#9472;sdd1    linux_raid_member ubnt:0      3cebc7c1-c766-7152-9424-f217e9209273
  &#9492;&#9472;md127 ext4                          36c839d5-f205-4ae0-919c-c1582ce73e23


```


```
 sudo mdadm -D /dev/md127
/dev/md127:
           Version : 1.2
     Creation Time : Tue Jan 29 14:00:54 2019
        Raid Level : raid1
        Array Size : 9766303744 (9313.87 GiB 10000.70 GB)
     Used Dev Size : 9766303744 (9313.87 GiB 10000.70 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Mon May  4 08:38:07 2020
             State : clean
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0


Consistency Policy : bitmap


              Name : ubnt:0  (local to host ubnt)
              UUID : 3cebc7c1:c7667152:9424f217:e9209273
            Events : 37610


    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1


```

```
ubnt@ubnt:~$ sudo  mount /dev/md127 /mnt
ubnt@ubnt:~$ cd /mnt/
ubnt@ubnt:/mnt$ ls
lost+found

```




```
ubnt@ubnt:/mnt$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# !NB! Run update-initramfs -u after updating this file.
# !NB! This will ensure that initramfs has an uptodate copy.
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays


# This configuration was auto-generated on Thu, 23 Apr 2020 07:34:28 +0000 by mkconf
ARRAY /dev/md/ubnt:0 level=raid1 num-devices=2 metadata=1.2 name=ubnt:0 UUID=3cebc7c1:c7667152:9424f217:e9209273
   devices=/dev/sdc1,/dev/sdd1

```



Can you please help me? I'm totally clueless from there and this is torture at its best.

---

### Post by slickymaster on 2020-05-04
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2020-05-04
The LTS to LTS upgrade message does not show up until 20.04.1 is out. I don't know how you started the upgrade, but usually it's best to wait until the first point .1 release is out.

The mdadm -D looks correct.

Can you please post the output of the following in CODE tags:
```
sudo mdadm -E /dev/sd[cd]1
sudo blkid
```

---

### Post by kmneimneh on 2020-05-04
> **darkod said:**
> The LTS to LTS upgrade message does not show up until 20.04.1 is out. I don't know how you started the upgrade, but usually it's best to wait until the first point .1 release is out.

The mdadm -D looks correct.

Can you please post the output of the following in CODE tags:
```
sudo mdadm -E /dev/sd[cd]1
sudo blkid
```


Hello darkod, I installed it using -d ( developer mode ) I know I know.... 

Please find below the output


```
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 3cebc7c1:c7667152:9424f217:e9209273
           Name : ubnt:0  (local to host ubnt)
  Creation Time : Tue Jan 29 14:00:54 2019
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 19532607488 (9313.87 GiB 10000.70 GB)
     Array Size : 9766303744 (9313.87 GiB 10000.70 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : d4844739:387ead4e:55f840f6:31ce9b4c


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon May  4 09:39:41 2020
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 5baef607 - correct
         Events : 37612




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 3cebc7c1:c7667152:9424f217:e9209273
           Name : ubnt:0  (local to host ubnt)
  Creation Time : Tue Jan 29 14:00:54 2019
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 19532607488 (9313.87 GiB 10000.70 GB)
     Array Size : 9766303744 (9313.87 GiB 10000.70 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 2e24aded:08b61d92:80970c4b:429ab0ea


Internal Bitmap : 8 sectors from superblock
    Update Time : Mon May  4 09:39:41 2020
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 4665386f - correct
         Events : 37612




   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)



```


```
ubnt@ubnt:~$ sudo blkid
/dev/sda1: LABEL="UBIQUITI AP" UUID="4063-0D7D" TYPE="vfat" PARTUUID="1b669f87-01"
/dev/sdb2: UUID="65eaefff-7753-4477-9ac3-0ad6c8b86c67" TYPE="ext4" PARTUUID="3e8047e3-f7a1-40ee-b163-e905593b3927"
/dev/sdd1: UUID="3cebc7c1-c766-7152-9424-f217e9209273" UUID_SUB="2e24aded-08b6-1d92-8097-0c4b429ab0ea" LABEL="ubnt:0" TYPE="linux_raid_member" PARTLABEL="primary" PARTUUID="42c00189-f997-41c7-a586-8f7fb1f04f4b"
/dev/sdc1: UUID="3cebc7c1-c766-7152-9424-f217e9209273" UUID_SUB="d4844739-387e-ad4e-55f8-40f631ce9b4c" LABEL="ubnt:0" TYPE="linux_raid_member" PARTLABEL="primary" PARTUUID="023ae8f7-feb4-4ae6-8de9-6aedf7d13573"
/dev/md127: UUID="ab2eb17e-d462-4ef8-aeac-61399f713162" TYPE="ext4"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sdb1: PARTUUID="9e6a05d5-84f0-4809-9eee-cbf243b9cfeb"

```

---

### Post by darkod on 2020-05-04
Developer mode upgrade for a production server with important data??? No comment...

Well, in theory it looks good.

What I would do:
1. Unmount md127, it is mounted RW. Best to try to mount it RO only.
2. Try to stop the array and reassemble it.

```
sudo umount /mnt
sudo mdadm --stop /dev/md127
sudo mdadm --assemble --verbose /dev/md0 /dev/sdc1 /dev/sdd1
```

Lets see what output that gives you. After it is assembled try to mount RO and check again for files.
```
sudo mount -o ro /dev/md0 /mnt
ls /mnt/
```

---

### Post by kmneimneh on 2020-05-04
> **darkod said:**
> Developer mode upgrade for a production server with important data??? No comment...

Well, in theory it looks good.

What I would do:
1. Unmount md127, it is mounted RW. Best to try to mount it RO only.
2. Try to stop the array and reassemble it.

```
sudo umount /mnt
sudo mdadm --stop /dev/md127
sudo mdadm --assemble --verbose /dev/md0 /dev/sdc1 /dev/sdd1
```

Lets see what output that gives you. After it is assembled try to mount RO and check again for files.
```
sudo mount -o ro /dev/md0 /mnt
ls /mnt/
```


Thanks for the follow up. Exactly what I feared, no files are showing.

```
umount: /mnt: not mounted.ubnt@ubnt:~$ sudo mdadm --stop /dev/md127
mdadm: stopped /dev/md127
ubnt@ubnt:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sdc1 /dev/sdd1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sdd1 to /dev/md0 as 1
mdadm: added /dev/sdc1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 2 drives.
ubnt@ubnt:~$ sudo mount -o ro /dev/md0 /mnt
ubnt@ubnt:~$ ls /mnt/
lost+found
ubnt@ubnt:~$



```

---

### Post by darkod on 2020-05-04
Well, it looks like maybe md0 got formatted. But the disks were disconnected during the OS install so we can't even say it was formatted then by error. I also don't see it logical the array to get formatted after you connected the disks.

You didn't need to create the array again, right? It got assembled automatically after connecting the disks and powering on? But now thinking about it, a newly installed OS would not know to assemble the array on boot, its mdadm.conf would be empty unless you manually modified it.

I don't have much experience searching the age of a filesystem. Maybe google around how to check how old is the ext4 on md0. If you manage to get a date it could confirm if it's few days old or few years.

And always mount md0 as RO only. Better to prevent writing to it while you are troubleshooting.

---

### Post by kmneimneh on 2020-05-04
> **darkod said:**
> Well, it looks like maybe md0 got formatted. But the disks were disconnected during the OS install so we can't even say it was formatted then by error. I also don't see it logical the array to get formatted after you connected the disks.

You didn't need to create the array again, right? It got assembled automatically after connecting the disks and powering on? But now thinking about it, a newly installed OS would not know to assemble the array on boot, its mdadm.conf would be empty unless you manually modified it.

I don't have much experience searching the age of a filesystem. Maybe google around how to check how old is the ext4 on md0. If you manage to get a date it could confirm if it's few days old or few years.

And always mount md0 as RO only. Better to prevent writing to it while you are troubleshooting.


I guess I know what happened. Probably overexhausted and dumb but I was reviewing the putty logs and it looks like I accidentally copied this command by mistake before mounting :)  I strongly believe there's no way back.

[LIST]
[*]sudo mkfs.ext4 -F /dev/md127
[/LIST]

---

### Post by darkod on 2020-05-04
Well that explains a lot...

Try googling for "undo mfks.ext4" or something similar.

Here is one of the results, but I just glanced over it. You need to do much deeper investigation if you want to try saving the data.
[https://unix.stackexchange.com/questions/168704/data-recovery-from-an-accidental-format-on-ext4-partition](https://unix.stackexchange.com/questions/168704/data-recovery-from-an-accidental-format-on-ext4-partition)

---

### Post by dragonfly41 on 2020-05-04
This is a sad case. If you search "reverse mkfs.ext4" you see the difficulties ahead.
You might try posting question in testdisk forum in addition to advice from this forum.
All the advice is to try recovery on a cloned system but this requires having at least two additional 10Tb drives.
In any case if you try TestDisk/PhotoRec you will need extra space into which you recover any files (i.e. never into the same device you are recovering since this act overwrites your files) so I would start now by ordering at least two extra drives to match your existing drives in size.
Someone wrote that Gparted (running in LiveUSB) has an option Device > Attempt Data Rescue.
Another tool to try is R-Linux (from R-Studio) again in a LiveUSB.
On a general point if you can get out of this hole I would spread your drives over a set of smaller drives on the principle of redundancy.
10TB recovery using PhotoRec will be a nightmare. The names of the files will not be recovered. TestDisk might recover filenames.

I can add no further suggestions other than possibly researching expert forensic recovery services which will be expensive.

---

