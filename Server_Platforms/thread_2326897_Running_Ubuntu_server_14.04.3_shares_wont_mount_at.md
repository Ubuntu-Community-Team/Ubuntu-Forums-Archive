---
title: "Running Ubuntu server 14.04.3 shares wont mount at boot ?"
date: 2016-06-05
forum: Server Platforms
---

### Post by johnmccormack on 2016-06-05
Hi hoping some server guru maybe able to point me in the right direction.

Once the server is booting i get this error " The drive for /media/VirtualBoxVms is not ready yet or not present. keys: Contuine to wait, or press s to skip mounting or M for manual recovery. 
 i alsoi get this for an other share /media/MediaShare

i have setup the server to boot from a high speed usb3 pen drive and have to internal hdd's which for the LVM for my shares. but if i log in remotely using webmin i can see the volume groups in logical Volume management but have just noticed that even though its reporting   [SIZE=+2][/SIZE]the full 700GB (one drive is 298 and the other is 495 roughly) but on trying to add the missing physical volume its now showing 1.2TB which is impossible, now i dont know whether to remove it again as its now saying its going to try and move the data from the disk to the rest of the volume

if its any help i think this problem was caused by me powering down the server and removing the usb drive with Ubuntu server on it. so i could use load Ubuntu 16 on to another pen drive using the dvd drive which i did making sure to have the pen drive boot info written to the pen drive and not the hdds. but on powering back up the server im left with this issue and help would be great 

not sure what logs would be helpfull had a look at some but nothing sticks out? i can post them just let me know which

---

### Post by einom on 2016-06-05
hello 

could you show the output of this commands?:

sudo fdisk -l
sudo cat /etc/fstab
sudo vgchange -ay 
sudo lvs

---

### Post by johnmccormack on 2016-06-06
Thanks for for the reply einom here you go ....

> **einom said:**
> hello 

could you show the output of this commands?:

sudo fdisk -l 
[HTML]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023098

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   976773164   488385558+  83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35b22083

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   625142447   312571223+  ee  GPT

Disk /dev/sdc: 32.0 GB, 32010928128 bytes
64 heads, 32 sectors/track, 30528 cylinders, total 62521344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef99f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   83  Linux
/dev/sdc2          501758    62519295    31008769    5  Extended
/dev/sdc5          501760    62519295    31008768   8e  Linux LVM

Disk /dev/mapper/ubuntuServer--vg-root: 27.5 GB, 27502051328 bytes
255 heads, 63 sectors/track, 3343 cylinders, total 53714944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntuServer--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntuServer--vg-swap_1: 4248 MB, 4248829952 bytes
255 heads, 63 sectors/track, 516 cylinders, total 8298496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntuServer--vg-swap_1 doesn't contain a valid partition table

[/HTML]

> 
sudo cat /etc/fstab

[HTML]# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntuServer--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=e66b786d-7865-4a2c-bdee-73ee1c1e5ade /boot           ext2    defaults        0       2
/dev/mapper/ubuntuServer--vg-swap_1 none            swap    sw              0       0
#VirtualBox VM Partition
/dev/mapper/SataDrives-VirtualBoxVMs   /media/VirtualBoxVMs   ext4   rw  0      0

#Media Partition
/dev/mapper/SataDrives-MediaShare  /media/MediaShare   ext4    rw   0       0

[/HTML]

> sudo vgchange -ay 
[HTML] 2 logical volume(s) in volume group "ubuntuServer-vg" now active
  Couldn't find device with uuid QXds3O-aDrp-Z2hC-uveY-k1Dx-zp2v-rI6Vak.
  Refusing activation of partial LV Data. Use --partial to override.
  Refusing activation of partial LV VirtualBoxVMs. Use --partial to override.
  Refusing activation of partial LV MediaShare. Use --partial to override.
  Refusing activation of partial LV VirtualBoxVMS. Use --partial to override.
  Refusing activation of partial LV VMS. Use --partial to override.
  0 logical volume(s) in volume group "storeage" now active
[/HTML]

> 
sudo lvs


[HTML]  Couldn't find device with uuid QXds3O-aDrp-Z2hC-uveY-k1Dx-zp2v-rI6Vak.
  LV            VG              Attr      LSize   Pool Origin Data%  Move Log Copy%  Convert
  Data          storeage        -wi-----p 233.00g                                           
  MediaShare    storeage        -wi-----p 300.00g                                           
  VMS           storeage        -wi-----p  50.00g                                           
  VirtualBoxVMS storeage        -wi-----p  50.00g                                           
  VirtualBoxVMs storeage        -wi-----p  80.00g                                           
  root          ubuntuServer-vg -wi-ao---  25.61g                                           
  swap_1        ubuntuServer-vg -wi-ao---   3.96g[/HTML]

---

### Post by einom on 2016-06-06
look like that the /dev/sdb disk don&#8217;t have a partition for LVM, and your volumes need more than 500G of space.

you could try to recovery the PV missing, take a look to:
[http://askubuntu.com/questions/219151/is-it-possible-to-recover-a-partial-lvm-logical-volume](http://askubuntu.com/questions/219151/is-it-possible-to-recover-a-partial-lvm-logical-volume)

---

### Post by darkod on 2016-06-06
Sorry to jump in, but there are few better commands to try...

fdisk does not work with GPT tables that many people use today, so a better command to see all partitions is:
```
sudo parted -l
```

Then, to check LVM physical volumes, don't try to activate them. Simply:
```
sudo pvdisplay
sudo vgdisplay
```

We can't know if sdb has partition for LVM or not because fdisk will not read gpt table...

But it does look like one of the physical volumes is missing from the LVM, hence it's not working good...

And for the end, DO NOT use webmin!!!! It is not supported and is not recommended. If you were managing your LVM through webmin I'm not surprised it failed. I didn't understand the part where you tried again to add the same partition to the LVM and it made it 1.2TB. Why would you try adding same partition twice? And webmin allowed you that?

---

### Post by johnmccormack on 2016-06-06
than einom will have a look

---

### Post by johnmccormack on 2016-06-06
> **darkod said:**
> Sorry to jump in, but there are few better commands to try...

fdisk does not work with GPT tables that many people use today, so a better command to see all partitions is:
```
sudo parted -l
```

```
Model: ATA ST3500630AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? cancel                                                         

Model: SanDisk Cruzer U (scsi)
Disk /dev/sdc: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   32.0GB  31.8GB  extended
 5      257MB   32.0GB  31.8GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntuServer--vg-root: 27.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  27.5GB  27.5GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntuServer--vg-swap_1: 4249MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4249MB  4249MB  linux-swap(v1)
``` 

The above is what i get if i type CANCEL to the "Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used." i hope i haven't messed things up cuz as i was typing out the initial post i noticed that the sda1=>465.76 GB drive was missing  in Webmin so try'd to added it but it put it in as a new volume instead of an existing one. Some thing to keep in mind as yeah read the output real appreciate the help as i moved all my files and music over on the to lvm sda1=>465.76 GB sdb1=>298.09 GB ( because it had been running fine for a couple of months and i sadly have no backup made #-o.

This is what i get if i answer OK to "Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used

```
Model: ATA ST3500630AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? ok                                                             
Warning: Not all of the space available to /dev/sdb appears to be used, you can fix the GPT to use all of the space (an extra 3 blocks) or continue with the current setting? 
Fix/Ignore?
```                                                              

And this is as far as i will go cuz i dont want to over write any info that may yet be recoverable 
> 
Then, to check LVM physical volumes, don't try to activate them. Simply:
```
sudo pvdisplay
sudo vgdisplay
```

```

  --- Volume group ---
  VG Name               ubuntuServer-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               29.57 GiB
  PE Size               4.00 MiB
  Total PE              7570
  Alloc PE / Size       7570 / 29.57 GiB
  Free  PE / Size       0 / 0   
  VG UUID               pQxBWB-HyX7-GsQe-V1gk-Olyu-zsIw-xE6SYH
   
  Couldn't find device with uuid QXds3O-aDrp-Z2hC-uveY-k1Dx-zp2v-rI6Vak.
  --- Volume group ---
  VG Name               storeage
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  10
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                5
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                2
  VG Size               1.20 TiB
  PE Size               4.00 MiB
  Total PE              314778
  Alloc PE / Size       182528 / 713.00 GiB
  Free  PE / Size       132250 / 516.60 GiB
  VG UUID               HEgeMv-Jjid-rwQY-vfnc-5eQ3-1Yjo-2FGjhd
```
> 
We can't know if sdb has partition for LVM or not because fdisk will not read gpt table...

But it does look like one of the physical volumes is missing from the LVM, hence it's not working good...

And for the end, DO NOT use webmin!!!! It is not supported and is not recommended. If you were managing your LVM through webmin I'm not surprised it failed. I didn't understand the part where you tried again to add the same partition to the LVM and it made it 1.2TB. Why would you try adding same partition twice?  well even though the size of the LVM was been reported correctly at the time it must not have been able to mount the physical drive so when i saw that in webmin i thought ah theres the problem....... > And webmin allowed you that?

Thanks for the advice about Webmin but i fear its to late as you can see from the output of "sudo vgdisplay" it is now looking for and LVM of 1.2TB damn it i should have left it alone aaaarrrggghhh!!
the physical volumes in the server are 
sda1=>465.76 GB ( isuspect this is the one that is/was missing )
 sdb1=>298.09 GB 
total =>763.85 (which is what the total should be not 1.2TB so to get this webmin/I has added the volume of sda1 to the lvm again im guess maybe because the original uuid for this volume was corrupted some how )
sdc5=>29.57 GB (This is the pen drive with Ubuntu on it )



is this Terminal ?:(

---

### Post by darkod on 2016-06-07
When posting output better to put it in CODE tags, not HTML CODE. Not sure if there is real difference, I usually use CODE.

I think you have two issues.

1. That somehow the sda1 500GB partition got added second time as physical volume for your LVM, so it incorrectly reports its size as 1.2TB now.

2. The bigger problem. Even parted does not see the /dev/sdb disk correctly (the 320GB disk). It might be a temporary smaller error, or the disk has failed in a bad way.

It seems that /dev/sdb failed first, and that provoked the LVM not to mount/work. After that you somehow managed to add sda1 again to the LVM.

I would try to sort out /dev/sdb first. If that works, that would be very good. You will tackle the LVM 1.2TB size later.

In the above warning that not all space is being used, if you do Ignore that should show sdb as it is, without trying to fix/modify anything. In theory that should not change anything on the disk.

Another way to try take a look at sdb partitions is using parted prompt. Try something like:
```
sudo parted /dev/sdb
unit MiB
print
```

The first command opens parted prompt for sdb, the second sets default unit to MiB (just for display, doesn't change anything on the disk), and the third prints out the current partition table. Try that to see what output it gives you...

To go out of the parted prompt you use 'quit'.

---

### Post by johnmccormack on 2016-06-07
Thanks for the info ill try and post the output.
and thanks for the info on the code tags wasn't sure which to use !

---

### Post by johnmccormack on 2016-06-08
> **darkod said:**
> When posting output better to put it in CODE tags, not HTML CODE. Not sure if there is real difference, I usually use CODE.

I think you have two issues.

1. That somehow the sda1 500GB partition got added second time as physical volume for your LVM, so it incorrectly reports its size as 1.2TB now.

2. The bigger problem. Even parted does not see the /dev/sdb disk correctly (the 320GB disk). It might be a temporary smaller error, or the disk has failed in a bad way.

It seems that /dev/sdb failed first, and that provoked the LVM not to mount/work. After that you somehow managed to add sda1 again to the LVM.

I would try to sort out /dev/sdb first. If that works, that would be very good. You will tackle the LVM 1.2TB size later.

In the above warning that not all space is being used, if you do Ignore that should show sdb as it is, without trying to fix/modify anything. In theory that should not change anything on the disk.


This is the output form ```
sudo parted -l

```
```
Model: ATA ST3500630AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary


Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? ok
Warning: Not all of the space available to /dev/sdb appears to be used, you can
fix the GPT to use all of the space (an extra 3 blocks) or continue with the
current setting?
Fix/Ignore? ignore
Model: ATA ST3320418AS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name           Flags
 1      1049kB  320GB  320GB               ServerStorage


Model: SanDisk Cruzer U (scsi)
Disk /dev/sdc: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   32.0GB  31.8GB  extended
 5      257MB   32.0GB  31.8GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntuServer--vg-root: 27.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  27.5GB  27.5GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntuServer--vg-swap_1: 4249MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4249MB  4249MB  linux-swap(v1)
```


> 
Another way to try take a look at sdb partitions is using parted prompt. Try something like:
```
sudo parted /dev/sdb
unit MiB
print
```

The first command opens parted prompt for sdb, the second sets default unit to MiB (just for display, doesn't change anything on the disk), and the third prints out the current partition table. Try that to see what output it gives you...

To go out of the parted prompt you use 'quit'.

```
GNU Parted 2.3
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit MiB
(parted) print
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? ok
Warning: Not all of the space available to /dev/sdb appears to be used, you can
fix the GPT to use all of the space (an extra 3 blocks) or continue with the
current setting?
Fix/Ignore? I
Model: ATA ST3320418AS (scsi)
Disk /dev/sdb: 305245MiB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start    End        Size       File system  Name           Flags
 1      1.00MiB  305245MiB  305244MiB               ServerStorage

(parted) 1
  align-check TYPE N                        check partition N for TYPE(min|opt)
        alignment
  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on
        COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition
        table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on
        partition NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  resizepart NUMBER END                    resize partition NUMBER
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table,
        available devices, free space, all found partitions, or a particular
        partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START
        and END
  resize NUMBER START END                  resize partition NUMBER and its file
        system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition
        NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and
        copyright information of GNU Parted
(parted)


```
I'm not familiar with these options so hopefully you could point out which if any of these i could use ?
The next ouput if it helps is CANCEL to the first Error ... well that just drops me back to the parted prompt. how can i see or compare to backup GPT table with the primary or would that be of any use ? still very much a Padawin learner when it comes to these kinds of errors :-)
Thanks for you input darkod!

---

### Post by johnmccormack on 2016-06-08
This is the output from sda.


```
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit MiB
(parted) print
Model: ATA ST3500630AS (scsi)
Disk /dev/sda: 476940MiB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End        Size       Type     File system  Flags
 1      1.00MiB  476940MiB  476939MiB  primary
```

And sdc 

```
GNU Parted 2.3
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit MiB
(parted) print
Model: SanDisk Cruzer U (scsi)
Disk /dev/sdc: 30528MiB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End       Size      Type      File system  Flags
 1      1.00MiB  244MiB    243MiB    primary   ext2         boot
 2      245MiB   30527MiB  30282MiB  extended
 5      245MiB   30527MiB  30282MiB  logical                lvm

(parted)
```

---

### Post by darkod on 2016-06-08
Do you have another spare disk so that you can clone that 320GB disk before attempting to repair it?

I think ubuntu can fix this very easily, but if you want to clone it for your piece of mind, that would be a smart thing to do. Sometimes things go wrong even with simple fixes...

I found one tutorial how to try to fix gpt disks with gdisk and it looks like it should work in your case. So the only thing now is if you want to clone it first or not???

---

### Post by johnmccormack on 2016-06-08
Hi darkod 
Yes I do have a spare disk 1TB in size so I can either clone the hole life to one drive (if possible) or just the one you mentioned. But am at work at the moment so will attempt it when I get home. Is there anything special about cloning a lot that I shoul know about before hand I'll do some research on it and let you know 
Thanks again for your patience!

---

### Post by darkod on 2016-06-08
You can read the section 'Using ddrescue' here: [https://wiki.archlinux.org/index.php/disk_cloning](https://wiki.archlinux.org/index.php/disk_cloning)

Basically you clone the whole disk as root, and in the ddrescue command the bad disk (/dev/sdb) is always first and the new disk (let's say it will be /dev/sdd) is second.

So according to that article the commands would be like:
```
sudo -i
ddrescue -f -n /dev/sdb /dev/sdd /root/rescue.log
```

After that review the rescue.log and see what it says. In the article there is a second command to try copying possible sectors with errors, but if the log says there are no errors you can save yourself time and not run that.

See how that goes... I have no idea how long it would take, probably a number of hours.

You can also search other articles for disk cloning, there are plenty. Most of them use ddrescue or dd commands.

PS. To save time clone only /dev/sdb because that is the partition table you need to fix. Don't clone the whole LVM... Besides if the LVM considers it has 1.2TB size right now, trying to clone it to 1TB disk might present problems.

Of course, it goes without saying that you will lose the data on the 1TB disk, so first move any data that you might have on it right now!!!

---

### Post by johnmccormack on 2016-06-10
> **darkod said:**
> You can read the section 'Using ddrescue' here: [https://wiki.archlinux.org/index.php/disk_cloning](https://wiki.archlinux.org/index.php/disk_cloning)

Basically you clone the whole disk as root, and in the ddrescue command the bad disk (/dev/sdb) is always first and the new disk (let's say it will be /dev/sdd) is second.

So according to that article the commands would be like:
```
sudo -i
ddrescue -f -n /dev/sdb /dev/sdd /root/rescue.log
```

After that review the rescue.log and see what it says. In the article there is a second command to try copying possible sectors with errors, but if the log says there are no errors you can save yourself time and not run that.

See how that goes... I have no idea how long it would take, probably a number of hours.

You can also search other articles for disk cloning, there are plenty. Most of them use ddrescue or dd commands.

PS. To save time clone only /dev/sdb because that is the partition table you need to fix. Don't clone the whole LVM... Besides if the LVM considers it has 1.2TB size right now, trying to clone it to 1TB disk might present problems.

Of course, it goes without saying that you will lose the data on the 1TB disk, so first move any data that you might have on it right now!!!

Thanks for that i'll do that tonight, i was going to create a snap shot but have only been able to find instructions about doing a snapshot for the hole LV, dont know if you cant take a snap shot of the individual drives. But ill use the DD command you suggested.

Would like to run something by you though and see wht you think.. initally when i first discovered this problem this is what ```
sudo pvs
``` looked like 
```
sudo pvs
  Couldn't find device with uuid QXds3O-aDrp-Z2hC-uveY-k1Dx-zp2v-rI6Vak.
  PV             VG              Fmt  Attr PSize   PFree
  /dev/sdb1      storeage        lvm2 a--  298.09g      0
  /dev/sdc5      ubuntuServer-vg lvm2 a--   29.57g      0
  unknown device storeage        lvm2 a-m  465.76g  50.84g



``` i may be wrong but my original though ws that the UUID for the now unknown device 456.76G  which only has 50G free space some how got corrupted and that is the UUID that LVM 2 cant find? 
and now because but just before i sent the very first post here, i was looking at Webmin ( by the way any suggestions for a better GUI) and saw that the the sda1 465.76G physical drive was missing and added it back in thinking that would sorted it, is that  also why Webmin allowed me to added it a second time as it wasn't being identified as part of the volume as the UUID for it had been corrupted 

This is what it looks like now, i added the spare 1TB drive to it here as well 
sudo pvs
 ```
 sudo pvs
  Couldn't find device with uuid QXds3O-aDrp-Z2hC-uveY-k1Dx-zp2v-rI6Vak.
  PV             VG              Fmt  Attr PSize   PFree
  /dev/sda1      storeage        lvm2 a--  465.76g 465.76g
  /dev/sdb1      storeage        lvm2 a--  298.09g      0
  /dev/sdc5      ubuntuServer-vg lvm2 a--   29.57g      0
  /dev/sdd1      rescue          lvm2 a--  931.51g 431.51g
  unknown device storeage        lvm2 a-m  465.76g  50.84g

```

---

### Post by johnmccormack on 2016-06-10
No matter what i try i seem to hit yet another brick wall or maybe the Ubuntu knights are testing me lol can you have a look over this and see if ive dont something to cause this i think its a bit strange to be asking me to sudo apt-get install LVM2 seeing as the partions are in LVM2 ??
```
root@ubuntuServer:~# ddrescue -f -n /dev/sdb /dev/sdd /root/rescue.log


GNU ddrescue 1.17
Press Ctrl-C to interrupt
rescued:   781189 kB,  errsize:       0 B,  current rate:     131 kB/s
   ipos:   781189 kB,   errors:       0,    average rate:   26937 kB/s
   opos:   781189 kB,    time since last successful read:       0 s
Copying non-tried blocks...
rescued:   781451 kB,  errsize:       0 B,  current rate:     262 kB/sonly file    ipos:   781385 kB,   errors:       0,    average rate:   26048 kB/s
   opos:   781385 kB,    time since last successful read:       0 s

Logfile error
root@ubuntuServer:~# ddrescue -f -n /dev/sdb /dev/sdd1 /root/rescue.log

ddrescue: Error opening logfile '/root/rescue.log' for writing.: Read-only file system
Fix the problem and press ENTER to retry, or Q+ENTER to abort. q
root@ubuntuServer:~# sudo lvcreate -n rescuevl -L 400g /dev/sdd
sudo: lvcreate: command not found
root@ubuntuServer:~# lvcreate -n rescuevl -L 400g /dev/sdd
The program 'lvcreate' is currently not installed. You can install it by typing:
apt-get install lvm2
root@ubuntuServer:~# sudo apt-get install lvm2
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@ubuntuServer:~# ddrescue -f -n /dev/sdb /dev/sdd1 /root/rescue.log

ddrescue: Error opening logfile '/root/rescue.log' for writing.: Read-only file system
Fix the problem and press ENTER to retry, or Q+ENTER to abort.





ddrescue: Error opening logfile '/root/rescue.log' for writing.: Read-only file system
Fix the problem and press ENTER to retry, or Q+ENTER to abort. qq
root@ubuntuServer:~# sudo apt-get install lvm2
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
```

i have to give it a rest just finished an evening shift and its 03:00am #-o:cry:[-o

---

### Post by johnmccormack on 2016-06-10
Oh nearly forgot this is output from glances around the tim i preformed the dd command 
```
Warning or critical alerts (last 5 entries)
                          2016-06-11 01:59:36 (0:00:09) - WARNING on CPU_IOWAIT (73.5)
                          2016-06-11 01:59:14 (0:00:19) - WARNING on CPU_IOWAIT (86.2)
                          2016-06-11 01:58:59 (0:00:12) - WARNING on CPU_IOWAIT (73.4)
                          2016-06-11 01:58:37 (0:00:12) - WARNING on CPU_IOWAIT (74.3)
            3:14:33       2016-06-11 01:56:32 (0:00:12) - WARNING on CPU_IOWAIT (74.1)
```

---

### Post by darkod on 2016-06-11
Man, you are asking for trouble... :)

Why did you add the 1TB disk to the lvm too? When cloning disks both the source and destination disk need to be not mounted and not in use, for best results. We never discussed to add the 1TB disk to the lvm or mount it otherwise.

And the ddrescue is giving you error because you are not using sudo in front of it. If you check my commands again, I used 'sudo -i' before using ddrescue which would make you root. You either do that or use sudo in front of ddrescue.

But now first remove sdd1 from the lvm, you want it to clone to it, not to be part of the lvm.

And we also said to try and fix the partition table issue on sdb first, don't go into why sda1 is or is not recognized by the lvm. That comes later...

---

### Post by johnmccormack on 2016-06-11
> **darkod said:**
> Man, you are asking for trouble... :)

Why did you add the 1TB disk to the lvm too? When cloning disks both the source and destination disk need to be not mounted and not in use, for best results. We never discussed to add the 1TB disk to the lvm or mount it otherwise.

I didnt i added it as a seperate LG called "rescue" to copy/ backup the 320GB drive 
```

/dev/sda1      [COLOR=#ff0000]**storeage**[/COLOR]        lvm2 a--  465.76g 465.76g
  /dev/sdb1     **[COLOR=#ff0000] storeage[/COLOR]**        lvm2 a--  298.09g      0

  /dev/sdd1      **[COLOR=#00ff00]rescue[/COLOR]**          lvm2 a--  931.51g 431.51g
```


> And the ddrescue is giving you error because you are not using sudo in front of it. If you check my commands again, I used 'sudo -i' before using ddrescue which would make you root. You either do that or use sudo in front of ddrescue.

i have but didnt copy and paste that part in ```
 
[COLOR=#ff0000]**_root@ubuntuServe_**[/COLOR]r:~# ddrescue -f -n /dev/sdb /dev/sdd /root/rescue.log
```


but it some how looks like i managed to wipe the grub config files on the server thumb drive ! as i cant boot the server up just get drop to grub rescue 
so i would imagine that the chances of recovering the original LVM has just got harder / impossible 
note to self dont try to fix anything in the early hours of the morning !!!! :confused:



 > But now first remove sdd1 from the lvm, you want it to clone to it, not to be part of the lvm.

And we also said to try and fix the partition table issue on sdb first, don't go into why sda1 is or is not recognized by the lvm. That comes later...

---

### Post by darkod on 2016-06-11
I see that you added sdd1 to new separate VG but still... As I said, cloning of disks should be done while the disks are not mounted or used in any way. So it was best not to add it to the LVM, there was no reason to do it.

With ddrescue you will clone sdb to sdd sector by sector, you are not mounting it and copying it. It's not the same.

Even if you can't boot the server from the usb stcik, you can still use ubuntu desktop live cd and boot it like that, and work from live mode in the terminal. That way you also make sure that any of the disks are not mounted because you are working from live mode.

One more reason not to add sdd1 to the LVM is that you want to clone sdb which partitions are part of the LVM. Cloning will clone the UUIDs and everything. So later LVM can get confused what is what seeing that it has more members but identical UUIDs etc...

So, if you still want to try fix this, get into live mode with the live cd, remove sdd1 from the LVM (there are plenty tutorials online how to remove partition from LVM), and clone sdb to sdd. You don't need to use log file if that is giving you an error. Just run both ddrescue commands, one to clone all good sectors, and one to clone sectors with errors (if there are any).

---

### Post by johnmccormack on 2016-06-13
i will try again :sad:.
one question i read the there is backups of the lvm's in var/logs i think it was would they be of any use ??

---

### Post by johnmccormack on 2016-06-14
hi darkod
back for another round lol.
this is the fdisk -l output of the rescue os (ubuntu 16.04) that i hope to preform the dd command on. A question about the log file will that also be saved to the output drive or will it be saved somewhere else ?
  insteadof a live cd i have installed ubuntu 16.04 os on a other 64gb thumb drive and am leaving all other drives unmounted, that set shouldn't pose any problems should it ? again thanks for your help so far!   

```
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00023098

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1        2048 976773164 976771117 465.8G 83 Linux


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0006740f

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953525167 1953523120 931.5G 83 Linux


The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sdc: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2D7411B0-E408-4C6F-973C-DD828665CDFE

Device     Start       End   Sectors   Size Type
/dev/sdc1   2048 625141759 625139712 298.1G Linux filesystem


Disk /dev/sdd: 58.2 GiB, 62518853632 bytes, 122107136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x68a3c484

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sdd1  *         2048 113944575 113942528 54.3G 83 Linux
/dev/sdd2       113946622 122105855   8159234  3.9G  5 Extended
/dev/sdd5       113946624 122105855   8159232  3.9G 82 Linux swap / Solaris
```

---

### Post by johnmccormack on 2016-06-14
well this is the out put from DDrescue so far 
```
GNU ddrescue 1.19
About to copy 320071 MBytes from /dev/sdc1 to /dev/sdb1.
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 sectors       Initial skip size: 128 sectors
Sector size: 512 Bytes

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0

Current status
rescued:     2968 MB,  errsize:       0 B,  current rate:     110 MB/s
   ipos:     2968 MB,   errors:       0,    average rate:     102 MB/s
   opos:     2968 MB, run time:      29 s,  successful read:       0 s ago
Copying non-tried blocks... Pass 1 (forwards)Killed
```

---

### Post by darkod on 2016-06-14
OK, so you cloned the partition. I would have done it with the disk, not the partition, but you don't seem to be paying much attention. Don't forget, every letter counts...

Now you can try opening /dev/sdc with parted and when it asks you to fix it, select Fix. Note that the 320GB disk changed identifier from sdb to sdc after you added the 1TB disk (which is now sdb).

---

### Post by johnmccormack on 2016-06-15
no scratch that last. i have since made an image couldnt get dd to work sdc => sdb could would not work i also try as you mentioned sdc1 => sdb1 and you saw the results but i have since got a image of sdc on to sdb1 and now realised that i was using the wrong path to store the file, (according to some of the tutorials i read)  in my original DD command but if you think a clone would be better ill do that? i havent tested the .img file yet. but i also had a look at the drives with gparted (didnt try anything just install and had a look, and guess what sdc 320GB drive is showing up with 320GB of free space !

---

### Post by darkod on 2016-06-17
I can't see the image very well, if you have two screen somehow crop only the relevant part, and keep it high res, don't lower the res too much. Otherwise the small stuff is not readable.

Anyway... The idea of cloning disk to disk (like sdc => sdb) is that it clones the full disk, including the partition table (which is contained in the first 512B of the disk). Cloning partition to partition (like sdc1 => sdb1) or disk to image file makes clone of only that partition but without the partition table info. It's up to you how you want to do it...

As for the disk showing 320GB free space in gparted, I'm not too surprised. Programs show the free space and the partition sizes based on the partition table (they do not scan the full disk). If there is an error in the partition table, and you already know there is, getting strange results is not a surprise. :)

So do the clone if you want to, and try to fix this. You've already waited long enough... :)

One question, which is not very relevant now: Why did you choose to have gpt table on the 320GB disk? GPT tables are usually needed only on very large disks, where you might have partitions larger than 2TB. Which means the disk itself has to be over 2TB. On smaller disks you might as well keep things simple and use the standard dos table. One exception from this is using the disk as windows OS disk and with UEFI boot, because windows can work only on gpt disks with UEFI boot. But for linux it doesn't really make a difference. Not unless you need to create 20 partitions on the disk which is also very unlikely for a disk of 320GB size.

---

### Post by MAFoElffen on 2016-06-18
I agree with Darkod and trust him immensely. I've been following and seeing how this goes. I am surprized that a PE could be added twice. I didn't think that was even physically possible!!! That makes sense that it then got a error on size and filled a PE incorrectly because of that incorrect size calculations of the algorithms being off. It unexpectedly ran out of room without knowing it was running low on space (usually throws a warning prior to that...) So, I can see where in that instance, it still had a file open and was busily writing to disk when that happened...

I use LVM a lot (understatement) I do a few things.  Not allocate all my disk to extents, so I either have PE room in the PV to grow or disks laying around to add more PE's and to clone disks that go bad.

Just thinking out loud. Logically, cloning the bad disk is the first step. But where from there? Usually, if you had a warning from LVM on low space, you would then add PE's to the PV, then go through the steps to grow. If a bad disk that is starting to fail, then add a disk, move data off that disk to the other disk members of the PV.

Since LVM is spanned, I, personally do not see a safe way to do any of that without getting clones of all the disks, to fall back to. Migrating data and/or when you add a repaired PE, after the first write, you will likely change metadata on one of the other (spanned) PE's. That is the risk. 

Another thing I though I would mention, has to do with technique. I do LVM rescues booted from a Live Image. That way you can either work with the disks mounted or offline. Offline, you can clone one disk to another as a disk image, immaterial of LVM and the suspected, corrupted system. LVM on your system is already in a world of hurt and you don't want to further corrupt the metadata before getting a disk image, or disk images, to fall back to.  That way you are somewhat isolated and one a good system. Also from that, you can mount into the rescued system with some isolation (through chroot) to be able to do other repairs.

The reason for not creating aan image on and from within that running filssytem has to do with file locks... tryting to take a picure of a moving, changing target

I haven't heard mention of these points and think you might want to think about them. Not mentioned is something everyone takes for granted: If there was a recent backup...  but then it would not be an issue right? No judgements (LOL) I've been guilty of that in the past. I've had my hands burned a few times.

But yes, the next step is-- once there is a copy, then that disk can be worked on.

---

### Post by johnmccormack on 2016-06-20
> **darkod said:**
> I can't see the image very well, if you have two screen somehow crop only the relevant part, and keep it high res, don't lower the res too much. Otherwise the small stuff is not readable.
Yaeh sorry about that i was rushed heading out to work ! i have edited it and attach it again.

> Anyway... The idea of cloning disk to disk (like sdc => sdb) is that it clones the full disk, including the partition table (which is contained in the first 512B of the disk). Cloning partition to partition (like sdc1 => sdb1) or disk to image file makes clone of only that partition but without the partition table info. It's up to you how you want to do it...
 

As for the disk showing 320GB free space in gparted, I'm not too surprised. Programs show the free space and the partition sizes based on the partition table (they do not scan the full disk). If there is an error in the partition table, and you already know there is, getting strange results is not a surprise. :)
 Thanks for explaining that, that's what i wasn't sure about.  This is  the first time i'v found myself in this situation never had a dive(s)  fail on me before but have had 2 fail on to different systems laptop and  the server funnily enough only the Linux partitions failed on the  laptop and the windows recovery partition is fine ? even the bios is  reporting it as 9gb instead of 160gb any way that's a different issue,  if you feel up to it after this one :wink::wink:

> So do the clone if you want to, and try to fix this. You've already waited long enough... :)
Will do but unfortunately im not going to be in a position to get a spare drive till the end of the week. id prefer to keep the backup images that i have on the 1TB drive just in-case. LOL i have backups of the backups now if only i did that in the first place i wouldn't be in this situation! lesson learn t. 

One question, which is not very relevant now: Why did you choose to have gpt table on the 320GB disk? GPT tables are usually needed only on very large disks, where you might have partitions larger than 2TB. Which means the disk itself has to be over 2TB. On smaller disks you might as well keep things simple and use the standard dos table. One exception from this is using the disk as windows OS disk and with UEFI boot, because windows can work only on gpt disks with UEFI boot. But for linux it doesn't really make a difference. Not unless you need to create 20 partitions on the disk which is also very unlikely for a disk of 320GB size.[/QUOTE]
funny you should ask actually i didn't is the short answer that has me stumped as well lol these are spare drives i had lying around which is another good reason not to store stuff on them. the only system i have/had that has a UEFI boot system is the server that I'm having/had the drive/partition failure on ?? but i have scanned the drive with a file recovery program to see if the files and information was sill the and it is, so that would leave to to believe that this partition isn't a recent development.

if you can bare with me a little longer i will do the dd clone command as soon as i have my hands on a brand spanking new drive ! at this point now i just want to know if it can be recovered and get a positive out come for all the effort and help that has been given

[ATTACH=CONFIG]269684[/ATTACH]

---

### Post by johnmccormack on 2016-06-20
> **MAFoElffen said:**
> I agree with Darkod and trust him immensely. I've been following and seeing how this goes. I am surprized that a PE could be added twice. I didn't think that was even physically possible!!! That makes sense that it then got a error on size and filled a PE incorrectly because of that incorrect size calculations of the algorithms being off. It unexpectedly ran out of room without knowing it was running low on space (usually throws a warning prior to that...) So, I can see where in that instance, it still had a file open and was busily writing to disk when that happened...
Hi MAFoElffen, he has the patient of a saint as well lol, i have been reading some of his other post aswell along the way that have come up in search's so i would agree with you agreeing with him lol. i gets bloody frustrating at times trying for hours to sort something out and to keep hitting a/the same brick wall lol. with regards to the physical volume being added twice well from what Darkod has said and what i have been reading about Webmin its not the most reliable, the drive that was added twice wasnt showing up in webmin but the 320GB one was for some reason. i suppose (and this is me taking a guess) is all the volume information for the 2 disk stored on one drive and if that drive was to be damaged would the other drive in the volume disappear (uneducated guess) ?? 

> I use LVM a lot (understatement) I do a few things.  Not allocate all my disk to extents, so I either have PE room in the PV to grow or disks laying around to add more PE's and to clone disks that go bad.

Just thinking out loud. Logically, cloning the bad disk is the first step. But where from there? Usually, if you had a warning from LVM on low space, you would then add PE's to the PV, then go through the steps to grow. If a bad disk that is starting to fail, then add a disk, move data off that disk to the other disk members of the PV.

Since LVM is spanned, I, personally do not see a safe way to do any of that without getting clones of all the disks, to fall back to. Migrating data and/or when you add a repaired PE, after the first write, you will likely change metadata on one of the other (spanned) PE's. That is the risk. 
so would you say that LVM's are a safe bet and not likely to give trouble over the long run, i ask because once i get the information back off these disks i will be going about setting up the sever again but this time i will but the backup fetcher in first and then the disk/data. or would you recommend and other file system ?

> Another thing I though I would mention, has to do with technique. I do LVM rescues booted from a Live Image. That way you can either work with the disks mounted or offline. Offline, you can clone one disk to another as a disk image, immaterial of LVM and the suspected, corrupted system. LVM on your system is already in a world of hurt and you don't want to further corrupt the metadata before getting a disk image, or disk images, to fall back to.  That way you are somewhat isolated and one a good system. Also from that, you can mount into the rescued system with some isolation (through chroot) to be able to do other repairs.

The reason for not creating aan image on and from within that running filssytem has to do with file locks... tryting to take a picure of a moving, changing target

I haven't heard mention of these points and think you might want to think about them. Not mentioned is something everyone takes for granted: If there was a recent backup...  but then it would not be an issue right? No judgements (LOL) I've been guilty of that in the past. I've had my hands burned a few times.

But yes, the next step is-- once there is a copy, then that disk can be worked on.

thanks for the info! about the backups i hear you ;-). my brilliant plan was to get the server up and running and THEN setup the backup system but over time "ah ill get to it later" and later becomes to late lol.
with regards to the live image i will go that root from a cd/dvd i have had live images mounted from a pen drive in the past and they just seem to grind to a halt over time to the point where i have had to to a hard reset, so hence my reluctance of using them for a process that could span hours. ah something i meant to ask Darkod can you recommend the best live rescue image to use ?

---

### Post by MAFoElffen on 2016-06-22
Safe? LOL! Matter of perspective. For personal use, with an active recovery plan where you actually do backups <---> Then yes. It you setup your backups in cron (scheduled), then that takes the "I'll get to that" factor out and it gets done.

On other production machines that are not my own, I still do LVM on top of RAID, with an active Recovery plan. I got those most customer when they lost what they had... (Various disasters.) ... and needed something safer.

On my own servers (14 servers)... Most are as above, 4 of them are LVM on RAID 6. But I my servers are linked to my storage server via fiber, on it's own net. Scripts do snapshots of data, then my backup server backs those up onto 200 GB tapes. Occasionally I do system images. (I want to save for a 3TB SAS tape drive.)

---

