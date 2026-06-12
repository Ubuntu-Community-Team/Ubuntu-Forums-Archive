---
title: "RAID-6 cannot start degraded array"
date: 2011-06-26
forum: Server Platforms
---

### Post by nev_au on 2011-06-26
Hello All,

Ubuntu Server 11.04 i386.

I've used linux on and off for years but only in small doses, so I'm really just at newbie level.

I was running an Openfiler NAS, but decided to give Ubuntu+Webmin a try. And up 'til now I've been happy with progress.

I have set up a RAID-6 array using 5 x 1TB SATA drives. 
I've ensured that the array is in a "clean" state, and now I want to do some failure testing.
The problem occurs when I remove one of the drives in the array. I shutdown, remove a drive, then boot up. The array wont start at all, and comes up with this error during boot:

> the disk drive for /mnt/raidvol1 is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recoveryIf I wait, nothing happens.
Obviously the RAID array should start in degraded mode, but it fails to mount at all.
When I press "M" to go into manual recovery and type "mount -a" I get the response: 

> mount: special device /dev/RAIDVG1/RAIDLV1 does not existI have set BOOT_DEGRADED=true in /etc/initramfs-tools/conf.d/mdadm  without success.

If I reconnect the disconnected drive, the array works fine, and is in a clean state.

Any help much appreciated!

Nev

---

### Post by rubylaser on 2011-06-26
What do you have in your /etc/mdadm/mdadm.conf file?
```
cat /etc/mdadm/mdadm.conf
```

and what does your fstab look like?
```
cat /etc/fstab
```

---

### Post by ian dobson on 2011-06-26
Hi,

Maybe add bootdegraded=1 to your kernel command line. Also did you run update-initramfs after changing  /etc/initramfs-tools/conf.d/mdadm?

Regards
Ian Dobson

---

### Post by nev_au on 2011-06-26
Thanks for your prompt response rubylaser. File contents shown below..

> **rubylaser said:**
> What do you have in your /etc/mdadm/mdadm.conf file?
and what does your fstab look like?


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

# This file was auto-generated on Sun, 05 Jun 2011 09:11:28 +0930
# by mkconf $Id$
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
ARRAY /dev/md0 level=raid6 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1,/dev/sdf1


``````

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sunny-root /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
/dev/mapper/sunny-swap_1 none            swap    sw              0       0
/dev/RAIDVG1/RAIDLV1  /mnt/raidvol1  ext3  defaults  0  0

```

---

### Post by nev_au on 2011-06-26
hi Ian, thanks for your suggestions..

> **ian dobson said:**
> Hi,
Maybe add bootdegraded=1 to your kernel command line.


Unfortunately that made no difference.

> 
Also did you run update-initramfs after changing  /etc/initramfs-tools/conf.d/mdadm?
I get this error when running this..

```

nev@sunny:~$ sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic-pae
mdadm: md device /dev/md0 does not appear to be active.

```

---

### Post by ian dobson on 2011-06-26
Hi,

So whats your raid device called, you have /mnt/raidvol1 in fstab and /dev/md0 in mdadm.conf.

Get your array up and running first, run then run update-initramfs, then start playing with removing drives.

Regards
Ian Dobson

---

### Post by rubylaser on 2011-06-26
It looks like your mdadm.conf file and fstab aren't using the same array.  I'd suggest, you remake your mdadm.conf file like this...

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

It will give you something that looks like this...
```
root@fileserver:~# cat /etc/mdadm/mdadm.conf 
DEVICE partitions
HOMEHOST fileserver
MAILADDR root@localhost
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41

```

You don't need to list out your disks, by sd[abcd]1 etc, just use partitions with the UUID's and it will assemble it perfectly, and be available at /dev/md0 for you.

Then, in your /etc/fstab file, change your array line to look like this...
```
/dev/md0  /mnt/raidvol1  ext3  defaults  0  0
```

Finally, you can run update-initramfs.  This should get your working :)

***** Disregard what I said above, if you're using LVM, as the mount point will need to change in /etc/fstab. You'll need to post the output of lvdisplay to figure that out. If you are using LVM, I'm wondering what features you're using it for.  mdadm covers almost all of the features that normal people think they need LVM for, and it's less complex to just run mdadm instead of LVM on top of mdadm when it comes time to troubleshoot problems. *****

---

### Post by nev_au on 2011-06-26
> **ian dobson said:**
> Hi,
Get your array up and running first, run then run update-initramfs, then start playing with removing drives.


I reconnected the drive to bring the array back online, and ran update-initramsfs ...

```
nev@sunny:~$ sudo update-initramfs -u -k all
[sudo] password for nev:
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic-pae
W: mdadm: the array /dev/md0 with UUID 3014aa73:85f03c13:55f7f1de:8667688e
W: mdadm: is currently active, but it is not listed in mdadm.conf. if
W: mdadm: it is needed for boot, then YOUR SYSTEM IS NOW UNBOOTABLE!
W: mdadm: please inspect the output of /usr/share/mdadm/mkconf, compare
W: mdadm: it to /etc/mdadm/mdadm.conf, and make the necessary changes.

```mkconf brings this up...
```

nev@sunny:~$ /usr/share/mdadm/mkconf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
/dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

```

---

### Post by rubylaser on 2011-06-26
mkconf is not generating an mdadm.conf file with the UUID for your array.  If you follow the directions I gave you, you will end up with a valid mdadm.conf file.

---

### Post by nev_au on 2011-06-26
> **rubylaser said:**
> 
I'm wondering what features you're using it for. mdadm covers almost all of the features that normal people think they need LVM for, and it's less complex to just run mdadm instead of LVM on top of mdadm when it comes time to troubleshoot problems.


I did it this way because this was the way it was done with Openfiler .. it worked fine, so I duplicated the method. All I really want is to have part of the array as an ext3 partition, and the rest as iSCSI (at the moment, for testing, am just making it all one ext3 partition).

Here is the output of lvdisplay..

```

  --- Logical volume ---
  LV Name                /dev/sunny/root
  VG Name                sunny
  LV UUID                YDA1wF-FdyP-VAHm-DOPR-PZdt-PD5F-A8PjNB
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                25.79 GiB
  Current LE             6601
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
  --- Logical volume ---
  LV Name                /dev/sunny/swap_1
  VG Name                sunny
  LV UUID                Qp2dl2-9lOo-VAhG-3qWJ-hqUN-Jvoi-XHm507
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                1.87 GiB
  Current LE             479
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1
   
  --- Logical volume ---
  LV Name                /dev/RAIDVG1/RAIDLV1
  VG Name                RAIDVG1
  LV UUID                byiTZG-ryrm-it00-swJB-Uq8B-Ciyv-PXFdQ1
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                2.73 TiB
  Current LE             715264
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:2

```

---

### Post by nev_au on 2011-06-26
> **rubylaser said:**
> mkconf is not generating an mdadm.conf file with the UUID for your array.  If you follow the directions I gave you, you will end up with a valid mdadm.conf file.

Apologies. When you had said "Disregard what I said above", I thought you meant everything above. I now realise you meant just the fstab part.

Will do the mdadm part now..

---

### Post by nev_au on 2011-06-26
> **rubylaser said:**
> mkconf is not generating an mdadm.conf file with the UUID for your array.  If you follow the directions I gave you, you will end up with a valid mdadm.conf file.

I have now done this, this is what mdadm.conf now looks like..

```
root@sunny:/etc/mdadm# cat /etc/mdadm/mdadm.conf
DEVICE partitions
HOMEHOST fileserver
MAILADDR root@localhost
ARRAY /dev/md0 metadata=1.2 name=sunny:0 UUID=3014aa73:85f03c13:55f7f1de:8667688e

```I have just ran update-initramfs and this time it seemed to go through fine, as you said it would!

Now just need your fstab assistance :)

Thanks.

---

### Post by rubylaser on 2011-06-26
Glad to hear you got that working :) You're going in the right direction now. Depending on the output og vgdisplay, you're previous fstab could be correct now.  Can you post that output?

---

### Post by nev_au on 2011-06-26
> **rubylaser said:**
> Glad to hear you got that working :) You're going in the right direction now. Depending on the output og vgdisplay, you're previous fstab could be correct now.  Can you post that output?

Here it is ruby .. so I keep fstab how it originally was?


```
  --- Volume group ---
  VG Name               sunny
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               27.70 GiB
  PE Size               4.00 MiB
  Total PE              7092
  Alloc PE / Size       7080 / 27.66 GiB
  Free  PE / Size       12 / 48.00 MiB
  VG UUID               TtcCSy-Szsh-MAn0-JWKN-8NMm-PhTK-RPib73
   
  --- Volume group ---
  VG Name               RAIDVG1
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               2.73 TiB
  PE Size               4.00 MiB
  Total PE              715399
  Alloc PE / Size       715264 / 2.73 TiB
  Free  PE / Size       135 / 540.00 MiB
  VG UUID               2WMSgB-IVja-2tYu-Tdzv-0gAb-YA5I-pRAqvZ
   

```

---

### Post by rubylaser on 2011-06-26
Yup, based on your vg/lvdisplay output, leaving as it was should do it for you.

---

### Post by nev_au on 2011-06-26
Thanks Ruby,

Unfortunately, I am still getting the same error though, as in my original post, (when I disconnect a drive) ..

```
the disk drive for /mnt/raidvol1 is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery 			 		
```

---

### Post by rubylaser on 2011-06-26
When you did your vgcreate, did you create the array on /dev/md0 or somewhere else? What's this show?
```
pvdisplay
```

It appears that you did because RAIDVG1 is showing the correct volume group size (2.73 TiB). If you comment out that line from your fstab, can you mount it manually after the machine is booted?

```
mount /dev/RAIDVG1/RAIDLV1 /mnt/raidvol1
```
Also, just from copy and pasting your mount path from fstab, it appears that you have an extra space before /mnt/raidvol1, you should remove that.

Finally, what is the output of the following commands once it's booted?
```
cat /proc/mdstat
```
```
mdadm --detail /dev/md0
```

---

### Post by nev_au on 2011-06-26
Thanks for your continued help...

> **rubylaser said:**
> When you did your vgcreate, did you create the array on /dev/md0 or somewhere else? What's this show? 

I did this using webmin. 
1. I went into Hardware -> Logical Volume Management, and "Add New volume Group". and called it RAIDVG1.
2. Then I created a logical volume within RAIDVG1 called RAIDLV1. 
3. Went back into RAIDLV1's config page and formatted it as ext3
4. Created a folder called /mnt/raidvol1 (using SSH)
5. Went back into RAIDLV1's config page and mounted it to /mnt/raidvol1

```

nev@sunny:~$ sudo pvdisplay
[sudo] password for nev:
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               sunny
  PV Size               27.71 GiB / not usable 2.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              7092
  Free PE               12
  Allocated PE          7080
  PV UUID               mpo6JC-avYc-XMmj-ABiu-gUS3-H8E1-rCuv0U

  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               RAIDVG1
  PV Size               2.73 TiB / not usable 2.16 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              715399
  Free PE               135
  Allocated PE          715264
  PV UUID               lOsMhr-g9wh-FF60-gpnD-YsfZ-psje-ql4BPt

```>  If you comment out that line from your fstab, can you mount it manually after the machine is booted?Yes, manually mounting it as per your command does work.

> Also, just from copy and pasting your mount path from fstab, it appears that you have an extra space before /mnt/raidvol1, you should remove that.
Thanks, extra space removed..

```

nev@sunny:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdc1[1] sdb1[0] sdd1[2] sdf1[4] sde1[3]
      2930276520 blocks super 1.2 level 6, 4k chunk, algorithm 2 [5/5] [UUUUU]

unused devices: <none>

``````

nev@sunny:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Jun  5 10:34:45 2011
     Raid Level : raid6
     Array Size : 2930276520 (2794.53 GiB 3000.60 GB)
  Used Dev Size : 976758840 (931.51 GiB 1000.20 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Mon Jun 27 11:25:49 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 4K

           Name : sunny:0
           UUID : 3014aa73:85f03c13:55f7f1de:8667688e
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1

```

---

### Post by rubylaser on 2011-06-27
Since, you can mount it manually, the array is auto starting, it's just not auto mounting at this point.  Have you ran
```
update-initramfs -u -k all
```

Since you've made these changes?  If so, now that you have a valid mdadm.conf file, you should try to run
```
dpkg-reconfigure mdadm
```

This won't uninstall anything, and it shouldn't overwrite your now valid mdadm.conf file.  If this doesn't get it auto starting and assembling, I'll give you directions to create an init script, but that would be a hack and not as good as getting this working correctly.

---

### Post by nev_au on 2011-06-27
> **rubylaser said:**
> Since, you can mount it manually, the array is auto starting, it's just not auto mounting at this point.

hi rubylaser,

There could be some confusion between us here ... those steps that you mentioned I tried when I had all drives connected and the array was operating fine. The problem occurs when I disconnect any array member.

When I tested manual mount I didnt test it with an array member disconnected. I will try that now..

---

### Post by nev_au on 2011-06-27
Ok, I have disconnected one of the array members and ran some commands..

```

nev@sunny:~$ sudo mdadm --detail /dev/md0
[sudo] password for nev:
mdadm: md device /dev/md0 does not appear to be active.
``````

nev@sunny:~$ sudo mount /dev/RAIDVG1/RAIDLV1 /mnt/raidvol1
mount: special device /dev/RAIDVG1/RAIDLV1 does not exist

``````

nev@sunny:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[4](S) sdc1[2](S) sdd1[3](S) sdb1[0](S)
      3907035908 blocks super 1.2

unused devices: <none>

```

---

### Post by rubylaser on 2011-06-27
Oh, okay.  Thanks for the explanation.  I thought mdadm was still misbehaving.  Yes, please let me know what happens when you remove a disk.  Everything should still work fine, and the array show a degraded status when you look at:
```
mdadm --detail /dev/md0
```

---

### Post by nev_au on 2011-06-27
> **rubylaser said:**
>   Everything should still work fine, and the array show a degraded status 

See my post just previous to yours ... as you can see /dev/md0 isnt showing..

---

### Post by rubylaser on 2011-06-27
> **nev_au said:**
> Ok, I have disconnected one of the array members and ran some commands..

```

nev@sunny:~$ sudo mdadm --detail /dev/md0
[sudo] password for nev:
mdadm: md device /dev/md0 does not appear to be active.
``````

nev@sunny:~$ sudo mount /dev/RAIDVG1/RAIDLV1 /mnt/raidvol1
mount: special device /dev/RAIDVG1/RAIDLV1 does not exist

``````

nev@sunny:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[4](S) sdc1[2](S) sdd1[3](S) sdb1[0](S)
      3907035908 blocks super 1.2

unused devices: <none>

```

That is weird. Your mdadm.conf file is correct now, but it's showing all the disks as spares, and not auto-assembling when degraded.  The boot degraded option shouldn't matter in this context, because the array isn't where your root filesystem is. What does this show?
```
mdadm -E /dev/sd[bcde]1
```

You could assemble the array by hand and have it work, but this should work even on a degraded array.

---

### Post by nev_au on 2011-06-27
Output from mdadm -E /dev/sd[bcde]1  :

```

/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3014aa73:85f03c13:55f7f1de:8667688e
           Name : sunny:0
  Creation Time : Sun Jun  5 10:34:45 2011
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 1953517954 (931.51 GiB 1000.20 GB)
     Array Size : 5860553040 (2794.53 GiB 3000.60 GB)
  Used Dev Size : 1953517680 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 292eb1ea:64726a79:64ce2b18:7d374788

    Update Time : Mon Jun 27 20:54:19 2011
       Checksum : 94b2f269 - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 4K

   Device Role : Active device 0
   Array State : AAAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3014aa73:85f03c13:55f7f1de:8667688e
           Name : sunny:0
  Creation Time : Sun Jun  5 10:34:45 2011
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 1953517954 (931.51 GiB 1000.20 GB)
     Array Size : 5860553040 (2794.53 GiB 3000.60 GB)
  Used Dev Size : 1953517680 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 9a535708:94d327f6:5acbd4ef:d1913d52

    Update Time : Mon Jun 27 20:54:19 2011
       Checksum : d0b5d056 - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 4K

   Device Role : Active device 2
   Array State : AAAAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3014aa73:85f03c13:55f7f1de:8667688e
           Name : sunny:0
  Creation Time : Sun Jun  5 10:34:45 2011
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 1953517954 (931.51 GiB 1000.20 GB)
     Array Size : 5860553040 (2794.53 GiB 3000.60 GB)
  Used Dev Size : 1953517680 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fb5da350:1f535a86:0e039d01:848f6b2b

    Update Time : Mon Jun 27 20:54:19 2011
       Checksum : 942a8fa9 - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 4K

   Device Role : Active device 3
   Array State : AAAAA ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 3014aa73:85f03c13:55f7f1de:8667688e
           Name : sunny:0
  Creation Time : Sun Jun  5 10:34:45 2011
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 1953517954 (931.51 GiB 1000.20 GB)
     Array Size : 5860553040 (2794.53 GiB 3000.60 GB)
  Used Dev Size : 1953517680 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 094bc001:652f4e1f:f493b849:781fe13b

    Update Time : Mon Jun 27 20:54:19 2011
       Checksum : 36cc79d8 - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 4K

   Device Role : Active device 4
   Array State : AAAAA ('A' == active, '.' == missing)

```

---

### Post by rubylaser on 2011-06-27
All of that info looks good, so it's not a disk out of sync.  Have you tried to stop /dev/md0, and assemble it by hand with the missing disk to see if that will work (it should)?

```
mdadm --stop /dev/md0
```
```
mdadm -A /dev/md0 /dev/sd[bcde]1
```

---

### Post by nev_au on 2011-06-27
Thanks ruby ... that has done the trick! It has placed the array into degraded mode, as it should be.

I had to also use the "--run" option on the mdadm command line.

I guess the question is then, why did I have to re-assemble the drives to get it to work? For some reason removing an array member causes the array to break.

---

### Post by rubylaser on 2011-06-27
mdadm won't boot from a degraded array without changing the file that you already modified to prevent potential data loss.  But, it shouldn't have a problem assembling a degraded non-root array (your scenario).  Have you checked the log files to see if there is anything of interest?

---

