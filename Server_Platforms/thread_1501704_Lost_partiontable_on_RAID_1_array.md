---
title: "Lost partiontable on RAID 1 array"
date: 2010-06-04
forum: Server Platforms
---

### Post by treinbert on 2010-06-04
I just restarted my server (Ubuntu 9.04 server, running on ESXi 4.0) and while copying files onto the server using samba I got strange problems and the connection was lost. When I rebooted the total system, so ESXi as well as Ubuntu Server I did find problems on my RAID disk.

The directory, where the new files were added I have a lot of files, but a lot of them do not have any info except their name:

1304 -rw-rw-rw-  1 spoorhobby spoorhobby 1327274 2010-05-15 22:10 DSCF1895.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1896.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1897.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1898.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1899.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1900.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1901.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1902.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1903.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1904.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1905.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1906.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1907.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1908.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1909.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1910.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1911.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1913.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1914.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1915.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1916.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1917.JPG
   ? -?????????  ? ?          ?                ?                ? DSCF1918.JPG
1504 -rw-rw-rw-  1 spoorhobby spoorhobby 1534274 2010-05-08 09:53 DSCN6024.JPG

When I want info from one of there files. I get a special mesage:

root@ubuntuserver:/home/m0/plaatjes/Vakantie2010# more DSCF1900.JPG
DSCF1900.JPG: Achterhaald NFS-bestandshandvat

This means that the NFS handle is wrong/old, but it is not an NFS-disk. It is a RAID-1 disk.
/dev/md0              252G  229G   11G  96% /home/m0
/dev/md1              252G  222G   18G  93% /home/m1

root@ubuntuserver:/home/m0/plaatjes/Vakantie2010# more /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdd1[1] sdc1[0]
      268429952 blocks [2/2] [UU]

md1 : active raid1 sdf1[1] sdb1[0]
      268429952 blocks [2/2] [UU]

If I try to run fdisk, it says there is no partition and that the number of cylinders is too high, 67107488.

Both mirror disks are still functioning and I can still add/delete files, from the server, from other LINUX systems and from other Windows systems via samba.

I did make a full backup on a different server.

What is the best cause of action?

Kind regards,
Bert Mengerink

---

### Post by uOpt on 2010-06-04
What filesystem?

Running the matching fsck for your filesystem is the next step. If fdisk is unhappy plese cut'n'paste the whole session of invoking it.

Please describe more clearly what kind of setup you have here. You say this is inside vmware. So are these virtual disks under the raid, or are they real disks assigned to the virtual machine?

---

### Post by Jeroensum on 2010-06-05
NFS is not a filesystem, it's a protocol to share files with. NFS provides the same as samba (a way to share files across the network) except it's been initially designed for *nix systems as SMB/cifs was for windows.

The error message of 'stale NFS handle' as it would translate (jaja, een mede nederlander hier ;) maar ik hou het ff engels zodat iedereen het kan volgen), is probably relating to you or your system having this directory shared trough NFS. It's got nothing to do with raid or partitioning. When you fix the filesystem, the NFS error will dissapear.

The partitiontable itself is not lost, it's just been corrupted and needs to be fixed, like uOpt allready stated, using fsck is a good start and will most probably fix your problem. What I would like to add is that in most cases your filesystem needs to be unmounted for it to work. (There are some filesystems that do not require this but it is good practise to unmount an FS before checking it).

Don't worry about fdisk, first, run *mount* and see what filesystem /dev/md0 has and then check it with the suitable fsck utillity. For ext2/3 this would be fsck.ext2 or fsck.ext3 for xfs this would be fsck.xfs  and so on. You can check/see for most of the fsck tools which are installed on the system by entering fsck in a terminal and then pressing TAB twice.

---

### Post by treinbert on 2010-06-06
Both Jeroen and uOpt thanks for the info.

The result of fdisk /dev/md0 is:

root@ubuntuserver:~# fdisk /dev/md0
Apparaat bevat geen geldig DOS-, Sun-, SGI- of OSF-schijflabel.
Er wordt een nieuwe DOS-partitietabel aangemaakt met schijf-ID 0xa4618701.
Wijzigingen vinden enkel en alleen in het geheugen plaats, totdat u besluit ze
weg te schrijven.  Daarna is de oude inhoud uiteraard niet meer herstelbaar.


Het aantal cilinders van deze schijf is ingesteld op 67107488.
Hier is niets mis mee, maar het is groter dan 1024 en kan
bij bepaalde instellingen problemen veroorzaken met:
1) opstartsoftware (bijvoorbeeld oude versies van LILO),
2) partitioneringssoftware van andere besturingssytemen
   (bijvoorbeeld DOS FDISK of OS/2 FDISK).
Waarschuwing: onjuiste optie 0x0000 van partitietabel 4 zal
worden gecorrigeerd bij het schrijven.

Opdracht (m voor hulp): p

Schijf /dev/md0: 274.8 GB, 274872270848 bytes
2 koppen, 4 sectoren/spoor, 67107488 cilinders
Eenheid = cilinders van 8 * 512 = 4096 bytes
Schijf-ID: 0xa4618701

  Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem

Opdracht (m voor hulp): q

The result is thus no partition table and a wrong type of disk. The only correct thing is the size. The heads should be 63, the number of sectors per track should be 63 with 33417 cylinders and 512 bytes per cylinder.

Currently there is only one disk per array active:

root@ubuntuserver:~# more /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [rai
d10]
md0 : active raid1 sdc1[0]
      268429952 blocks [2/1] [U_]

md1 : active raid1 sdb1[0]
      268429952 blocks [2/1] [U_]

unused devices: <none>

The disks are virtual disks within the ESXi 4.0 system sda, sdb and sdc on the first disk (750 Gb) and sdd, sde, sdf on the second disk (1 Tb) The disk sde is not part of any system at the moment.

root@ubuntuserver:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Jan  1 20:18:43 2010
     Raid Level : raid1
     Array Size : 268429952 (255.99 GiB 274.87 GB)
  Used Dev Size : 268429952 (255.99 GiB 274.87 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jun  6 07:56:53 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 4d982e45:d2c5a362:ba7489ed:df8edc67 (local to host ubuntuserver)
         Events : 0.968

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed

root@ubuntuserver:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Sat Jan  2 12:32:17 2010
     Raid Level : raid1
     Array Size : 268429952 (255.99 GiB 274.87 GB)
  Used Dev Size : 268429952 (255.99 GiB 274.87 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jun  6 07:55:28 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9ac07d37:2802cd78:ba7489ed:df8edc67 (local to host ubuntuserver)
         Events : 0.592

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed

I hope this is enough information to give me some help.

Kind regards,
Bert Mengerink

---

### Post by uOpt on 2010-06-07
Why do you think you want to have partitions inside the raid?

It's not impossible, just asking whether that is the intention.

---

### Post by Jeroensum on 2010-06-07
The information about the raid setup is kind of confusing since it's a bit onorthodox. Just using one disk per array is not really array and would not provide any raid-like solutions, in case of disk/partition failure everything would be lost regardless of the raidlevel...

Also I'm still curious about the result of the *mount* and fsck commands.

---

### Post by benderisgreat on 2010-06-07
to get the arrays back in sync again you need to add the relevant partitions back to the array:
```
# mdadm --add /dev/md0 /dev/sdd1
# mdadm --add /dev/md1 /dev/sdf1
```

> Why do you think you want to have partitions inside the raid?
Are you sure you have actually partitioned the raid?

> /dev/md0 252G 229G 11G 96% /home/m0
/dev/md1 252G 222G 18G 93% /home/m1
I'm not sure where this info came from (looks like df) but it looks like the device md0 is mounted as /home/m0 which would indicate you have a filesystem directly on the array, and not on a partition on the array.

---

### Post by treinbert on 2010-06-09
Sorry all for the confusion. I did not think clearly about the raid array.

There is no partition table on a raid as it mounts two identical partitions on two different disks in a mirror.

I managed to unmount the disk. I first did shutdown both the NFS and the SAMBA deamons. I did repair the filesystems.

Unfortunately I still have problems with the external disk connected to my ESXi 4.0 system. It looks like the disk is not spinning up, when powered on. I will try to reboot the complete virtual machine.

Regards,
Bert

---

### Post by uOpt on 2010-06-09
Since when are we talking about an external disk?

Are you using a USB disk through VMware?

Good luck with that. You'll have many scrambled filesystems like that.

---

### Post by treinbert on 2010-06-09
Thanks all,

Luckily I have found the problem. The external disk has a button, which needs to be pushed after a power failure. The disks are synchronising at the moment.

Kind regards,
Bert

---

