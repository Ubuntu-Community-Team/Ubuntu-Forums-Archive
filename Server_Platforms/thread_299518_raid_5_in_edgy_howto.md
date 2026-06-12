---
title: "raid 5 in edgy howto"
date: 2006-11-14
forum: Server Platforms
---

### Post by mariuz on 2006-11-14
this guide might be useful for other edgy raid problems 
see it how i solved (firs you need to read the original [raid howto]("http://tldp.org/HOWTO/Software-RAID-HOWTO.html") )

install 3 sata drives (3x500GB in my case) in a raid 5 array 

```
sudo apt-get install mdadm
```

```
sudo fdisk /dev/sda
n
p
1
t
fd
sudo fdisk /dev/sdb
n
p
1
t
fd
sudo fdisk /dev/sdc
n
p
1
t
fd
```

> sudo mdadm --create --verbose /dev/md1 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1

NO /dev/md1 in edgy!:-k 
seems that is somewhere in an new place /dev/.static/dev/md1

```
cd dev
sudo  MAKEDEV md
sudo modprobe md
sudo mdadm --create --verbose /dev/.static/dev/md1 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1

```

```
cat /proc/mdstat
```

---

### Post by gerscht on 2006-11-20
Thanks for that! 
worked great until I rebooted :-k 
I have the correct entry in the fstab 
```
/dev/md0 /media/supersave ext3 defaults 0 2
```
and before the reboot I was able to mount/unmount it, but now the raid isn't recognized anymore...
My syslog says
```
[XXX] EXT3-fs: unable to read superblock
```

Any Ideas?

Thanks!

---

### Post by aivegas on 2007-02-19
This worked great, but how do I get the system to mount the RAID5 array now that this is done?  I'm confused.

---

### Post by Xanthomryr on 2007-02-20
This is what i have in my fstab to mount my raid5 array (/dev/md0) in /raid.
```
/dev/md0      /raid       ext3   defaults     0    0

```

The server runs Ubuntu 6.06 TLS.

---

### Post by caffienda on 2007-02-21
> **gerscht said:**
> Thanks for that! 
worked great until I rebooted :-k 
I have the correct entry in the fstab 
```
/dev/md0 /media/supersave ext3 defaults 0 2
```
and before the reboot I was able to mount/unmount it, but now the raid isn't recognized anymore...
My syslog says
```
[XXX] EXT3-fs: unable to read superblock
```

Any Ideas?

Thanks!

Is this really supposed to be /dev/md0  or /dev/md1?  The OP uses md1 as his example, so if you are following that, it should be /dev/md1, correct?  
Also, How do I remove/delete the mdadm entry?  I want to start over and rebuild the array.  Thanks.

---

### Post by caffienda on 2007-02-25
Is there something missing from this "How To", like making the file system?  I have never configured a RAID array before, so I don't know if it was done already or not. 

When I created the partitions for each of the  HD's I used "83"  ext3.

This is what I did to create my array:
```
sudo apt-get install mdadm
sudo fdisk /dev/hda1 
                    /dev/hde1 
                    /dev/hdf1 
                    /dev/hdg1 
                    /dev/hdh1
```
(Created a primary partition with the full size of the HD, then used "t" and "83" for partition type)
```
cd /dev/
sudo  MAKEDEV md
sudo modprobe md
sudo mdadm --create --verbose [COLOR="Red"]/dev/.static/dev/md0[/COLOR] --level=0 --raid-devices=5 /dev/hda1 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1
***mdadm: layout defaults to left-symmetric
***mdadm: chunk size defaults to 64K
***mdadm: /dev/hde1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: /dev/hdf1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: /dev/hdg1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: /dev/hdh1 appears to be part of a raid array:
***    level=raid5 devices=5 ctime=Wed Feb 21 03:27:41 2007
***mdadm: size set to 156288256K
***Continue creating array? y
***mdadm: array /dev/.static/dev/md0 started.
``` ***denotes operation output
Also the [COLOR="Red"]/dev/.static/dev/md0[/COLOR] that was used by th OP is a little confusing.  Why add the /dev/.static part?  How does this affect the array down the road?  id the /dev/.static needed?
```
caffiendo@UbServ:/$ cat /proc/mdstat
***Personalities : [raid5] [raid4] [raid0] 
***md0 : active raid0 hda1[0] hdh1[4] hdg1[3] hdf1[2] hde1[1]
***      781443648 blocks 64k chunks
```
```
mdadm -S /dev/md0
``` Used to stop the array
```
sudo gedit /etc/mdadm.conf
```Add the following lines:
DEVICE  /dev/hda1 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1
ARRAY   /dev/md0 devices=/dev/hda1,/dev/hde1,/dev/hdf1,/dev/hdg1,/dev/hdh1
```
sudo mdadm --detail --scan
***ARRAY /dev/md0 level=raid0 num-devices=5 UID=54623f8a:a3b744af:45dca40a:d0833744

```
[COLOR="Red"]This is where it gets strange...
```
sudo mdadm -As /dev/md0
***mdadm: /dev/md0 not identified in config file.
```[/COLOR] WHY won't this start, considering that I made the /etc/mdadm.conf file?
```
 sudo mdadm -A /dev/md0 /dev/hda1 /dev/hde1 /dev/hdf1 /dev/hdg1 /dev/hdh1
***mdadm: /dev/md0 has been started with 5 drives.

``````
sudo mdadm -E /dev/hda1
/dev/hda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 54623f8b:b3b44af:45dca40a:d0833744
  Creation Time : Sun Feb 25 13:54:18 2007
     Raid Level : raid0
    Device Size : 0
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

    Update Time : Sun Feb 25 13:54:18 2007
          State : active
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 436417f3 - correct
         Events : 0.1

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       3        1        0      active sync   /dev/hda1

   0     0       3        1        0      active sync   /dev/hda1
   1     1      33        1        1      active sync   /dev/hde1
   2     2      33       65        2      active sync   /dev/hdf1
   3     3      34        1        3      active sync   /dev/hdg1
   4     4      34       65        4      active sync   /dev/hdh1

```This is the step by step procedure that  I used.  How do I configure this in the fstab?  Is it different for RAID arrays?  Do I need to include the  UUID : 54623f8b:b3b44af:45dca40a:d0833744 in the fstab?

Also, when i created the /etc/mdadm.conf , do I use /dev/.static/dev/md0 or /dev/md0?

Finally what do I use to create a file system?  
sudo mke2fs -j /dev/md0    or
sudo mke2fs -j /dev/.static/dev/md0   ?

Muchas Gracias!

---

### Post by caffienda on 2007-02-25
I created  /raid directory for my array mounting point,  then adding this to my fstab
```
# /dev/.static/dev/md0  UUID=54623f8b:b3b44af:45dca40a:d0833744    /raid               ext3    defaults  0    0
```
I then tried creating the FS with this:
```
[COLOR="Blue"] sudo mke2fs -j /dev/.static/dev/md0[/COLOR]
***mke2fs 1.39 (29-May-2006)
***Filesystem label=
***OS type: Linux
***Block size=4096 (log=2)
***Fragment size=4096 (log=2)
***97681408 inodes, 195360912 blocks
***9768045 blocks (5.00%) reserved for the super user
***First data block=0
***Maximum filesystem blocks=197132288
***5962 block groups
***32768 blocks per group, 32768 fragments per group
***16384 inodes per group
***Superblock backups stored on blocks: 
***        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
***       4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
***        102400000
***Writing inode tables: done                            
***Creating journal (32768 blocks): done
***Writing superblocks and filesystem accounting information: done
***This filesystem will be automatically checked every 24 mounts or
***180 days, whichever comes first.  Use tune2fs -c or -i to override.

[COLOR="Blue"] sudo fdisk -l[/COLOR]

***Disk /dev/hda: 160.0 GB, 160041885696 bytes
***137 heads, 8 sectors/track, 285202 cylinders
***Units = cylinders of 1096 * 512 = 561152 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hda1               1      285202   156290692   83  Linux

***Disk /dev/sda: 37.0 GB, 37019566080 bytes
***255 heads, 63 sectors/track, 4500 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/sda1   *           1        4314    34652173+  83  Linux
***/dev/sda2            4315        4500     1494045    5  Extended
***/dev/sda5            4315        4500     1494013+  82  Linux swap / Solaris

***Disk /dev/sdb: 74.3 GB, 74355769344 bytes
***255 heads, 63 sectors/track, 9039 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/sdb1               1        1200     9638968+  83  Linux
***/dev/sdb3            1201        3000    14458500   83  Linux
***/dev/sdb4            3001        9039    48508267+  83  Linux

***Disk /dev/hde: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hde1               1       19457   156288321   83  Linux

***Disk /dev/hdf: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hdf1               1       19457   156288321   83  Linux

***Disk /dev/hdg: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hdg1               1       19457   156288321   83  Linux

***Disk /dev/hdh: 160.0 GB, 160041885696 bytes
***255 heads, 63 sectors/track, 19457 cylinders
***Units = cylinders of 16065 * 512 = 8225280 bytes

***   Device Boot      Start         End      Blocks   Id  System
***/dev/hdh1               1       19457   156288321   83  Linux

[COLOR="Red"]***Disk /dev/md0: 800.1 GB, 800198295552 bytes
***2 heads, 4 sectors/track, 195360912 cylinders
***Units = cylinders of 8 * 512 = 4096 bytes

***Disk /dev/md0 doesn't contain a valid partition table[/COLOR]
[COLOR="Blue"] sudo mount /dev/md0[/COLOR]
***mount: can't find /dev/md0 in /etc/fstab or /etc/mtab
[COLOR="Blue"] sudo mount /dev/.static/dev/md0[/COLOR]
***mount: can't find /dev/.static/dev/md0 in /etc/fstab or /etc/mtab

[COLOR="Blue"]sudo gedit /etc/mtab[/COLOR]
***(((I added    /dev/md0  /raid  ext3  rw  0))))
[COLOR="Blue"]sudo mount /dev/md0[/COLOR]
***Cannot create link /etc/mtab~
***Perhaps there is a stale lock file?


```


What do I do to correct the /dev/md0 not having a valid partition table?

---

### Post by FITorion on 2007-03-21
Yeah... I made a mistake in while following this stuff...

and I need to destroy the raid so I can start over

how do I do that?

I did this...

sudo mdadm --create --verbose /dev/.static/dev/md0 --level=5 --raid-devices=4 /dev/sda /dev/sdb /dev/sdb /dev/sdd 

as you can see I put sdb twice...

this stoped the raid creation half way... so now I have half of what I want... or nothing at all...

HA HA figured out how to do that...

 sudo mdadm --manage --stop /dev/.static/dev/md0


but now I did this

sudo mdadm --create --verbose /dev/.static/dev/md0 --level=5 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc /dev/sdd
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sda appears to be part of a raid array:
    level=raid5 devices=4 ctime=Wed Mar 21 17:04:01 2007
mdadm: /dev/sdb appears to be part of a raid array:
    level=raid5 devices=4 ctime=Wed Mar 21 17:04:01 2007
mdadm: size set to 488386496K
Continue creating array? y
mdadm: array /dev/.static/dev/md0 started.


It looks to me like only sda and sdb were added... am I wrong?

---

