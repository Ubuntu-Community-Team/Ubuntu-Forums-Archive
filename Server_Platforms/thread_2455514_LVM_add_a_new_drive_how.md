---
title: "LVM add a new drive how?"
date: 2020-12-21
forum: Server Platforms
---

### Post by Raymond Day on 2020-12-21
Got Ubuntu Linux 18.04.4 server installed on a sg30 toshiba magnia neat little box but a i386 so 32 bit and it will not let me upgrade any more.

To get this to install seems like the only was was start with a old Ubuntu 15 and then upgrade to to 18. Had to pick LVM to install it else it just would not make it so it would boot.

Put a 500GB SSD in it and it worked like that for months. But ran out of room on it. I got a 1TB SSD and DD copied it. It has a main big partition and in that is a LVM partition. When I sent to make it the full size of the 1TB with gparted on another system. It would do it fast but then can't read the LVM partition gave some error.

So now just put the 1TB as a 2nd drive in it and trying to **vgextend** to it but having nothing but problems. Here is some commands that my help.

```
root@sg30:~# lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/sda5        [     465.52 GiB] LVM physical volume
  /dev/sdb1        [     931.51 GiB] LVM physical volume
  0 LVM physical volume whole disks
  2 LVM physical volumes
root@sg30:~# lvs
  WARNING: Device for PV pgxzPS-Wguk-sc1Q-GZE1-UafM-IpIY-33KSri not found or rejected by a filter.
  WARNING: Device for PV 6tpHZT-fCAs-GUOv-E6AU-B42o-O5X1-xJGQZt not found or rejected by a filter.
  LV     VG   Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   sg30 -wi-ao---- <462.61g                                               
  swap_1 sg30 -wi-ao----    2.86g                                               
root@sg30:~#
```

Guess it sees ones I was trying to make and not it has more then 1. Maybe have to start over. But I don't want to mess up the 500GB boot drive. Took a long time to get it working.

Hope someone can help. Seems like there should be a easter way to do LVM to just say add this drive to it.

-Raymond Day

---

### Post by darkod on 2020-12-21
Did you do 'sudo pvcreate' for the new partition to mark it as LVM available?

Please post the output of the following commands:
```
sudo pvdisplay
sudo vgdisplay
```

---

### Post by Dennis N on 2020-12-21
It's not a good idea to have a single volume group span two physical disks, because failure of either can result in loss of access to the entire vg. So we transfer all the data to sdb1 and remove sda5 from sg30 vg.

There is a way to move the root and swap_1 lvs to sdb1. I have it in my notes, with a link to the source information (you should read):

[https://www.thegeekdiary.com/centos-rhel-how-to-remove-used-physical-volumepv-from-volume-group-vg-in-lvm/](https://www.thegeekdiary.com/centos-rhel-how-to-remove-used-physical-volumepv-from-volume-group-vg-in-lvm/)
 
_Outline_:
Use vgextend to add physical volume sdb1 to the sg30 vg. 
Use pvmove operating on sda5
Use vgreduce to remove sda5 as a pv in sg30.

I suggest you backup your data first before starting this procedure.

If you want to still use physical volume sda5, create a new VG on it, or you can format it to be a regular partition.

---

### Post by TheFu on 2020-12-21
I've used pvmove between disks.

IMHO, really this is the time to fix some not-so-great LVM setup above.

The "root" LV should be 25-50G, no larger.  It holds the OS, nothing else.
Create other LVs for "home" and other data as needed. Keep the OS, home, data separate to make life easier next time any storage changes are needed.
Definitely keep media files outside the "home" LV. Media files that don't change really should be stored separately to make selective backups easier.  Storage design is mostly about backups AND restore processes.

And please don't span an LV between multiple disks. I've lost lots of data long, long, ago due to poor decisions like spanning an LV across multiple physical devices. Nothing teaches a lesson faster than data loss.

Feel free to ignore our hard-learned suggestions.

---

### Post by Raymond Day on 2020-12-22
> **darkod said:**
> Did you do 'sudo pvcreate' for the new partition to mark it as LVM available?

Please post the output of the following commands:
```
sudo pvdisplay
sudo vgdisplay
```

```
root@sg30:/usr/src/lcd-2.2# sudo pvdisplay
  WARNING: Device for PV pgxzPS-Wguk-sc1Q-GZE1-UafM-IpIY-33KSri not found or rejected by a filter.
  WARNING: Device for PV 6tpHZT-fCAs-GUOv-E6AU-B42o-O5X1-xJGQZt not found or rejected by a filter.
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               sg30
  PV Size               465.52 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               13
  Allocated PE          119160
  PV UUID               ODLjqT-W8dR-mxfF-qTz5-LkBk-HWAW-a0tSbo

  --- Physical volume ---
  PV Name               [unknown]
  VG Name               sg30
  PV Size               931.51 GiB / not usable <30.29 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              238459
  Free PE               238459
  Allocated PE          0
  PV UUID               pgxzPS-Wguk-sc1Q-GZE1-UafM-IpIY-33KSri

  --- Physical volume ---
  PV Name               [unknown]
  VG Name               sg30
  PV Size               931.51 GiB / not usable 33.71 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              238459
  Free PE               238459
  Allocated PE          0
  PV UUID               6tpHZT-fCAs-GUOv-E6AU-B42o-O5X1-xJGQZt

  "/dev/sdb1" is a new physical volume of "931.51 GiB"
  --- NEW Physical volume ---
  PV Name               /dev/sdb1
  VG Name
  PV Size               931.51 GiB
  Allocatable           NO
  PE Size               0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               PvAzgu-50oX-a26G-A26N-TDuN-Y06E-Vq0EV1

root@sg30:/usr/src/lcd-2.2# sudo vgdisplay
  WARNING: Device for PV pgxzPS-Wguk-sc1Q-GZE1-UafM-IpIY-33KSri not found or rejected by a filter.
  WARNING: Device for PV 6tpHZT-fCAs-GUOv-E6AU-B42o-O5X1-xJGQZt not found or rejected by a filter.
  --- Volume group ---
  VG Name               sg30
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  8
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                3
  Act PV                1
  VG Size               2.27 TiB
  PE Size               4.00 MiB
  Total PE              596091
  Alloc PE / Size       119160 / <465.47 GiB
  Free  PE / Size       476931 / <1.82 TiB
  VG UUID               0scfsB-UcgD-8KVW-Jk0q-2w4b-VT9I-801mMu

root@sg30:/usr/src/lcd-2.2#
```

-Raymond Day

---

### Post by Raymond Day on 2020-12-22
This my halp I did some other commands and it shows this:

```
root@sg30:/usr/src/lcd-2.2# dmesg|grep sdb
[    4.778213] sd 0:0:1:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/93               2 GiB)
[    4.778248] sd 0:0:1:0: [sdb] Write Protect is off
[    4.778254] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.778526] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, does               n't support DPO or FUA
[    4.780583]  sdb: sdb1
[    4.784206] sd 0:0:1:0: [sdb] Attached SCSI disk
[  619.039027]  sdb: sdb1
[  856.312702]  sdb: sdb1
[  856.334687]  sdb: sdb1
[ 1050.228084]  sdb: sdb1
root@sg30:/usr/src/lcd-2.2# fdisk -l /dev/sdb
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00040670

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1           1 1953525167 1953525167 931.5G 8e Linux LVM
root@sg30:/usr/src/lcd-2.2# blkid
/dev/sdb1: UUID="PvAzgu-50oX-a26G-A26N-TDuN-Y06E-Vq0EV1" TYPE="LVM2_member" PARTUUID="00040670-01"
/dev/sda1: UUID="e345a64a-69d6-4723-a469-2a9cd5dbb126" TYPE="ext2" PARTUUID="00040670-01"
/dev/sda5: UUID="ODLjqT-W8dR-mxfF-qTz5-LkBk-HWAW-a0tSbo" TYPE="LVM2_member" PARTUUID="00040670-05"
/dev/mapper/sg30-root: UUID="71bc748b-9faa-425d-a3f6-69f619b8aa81" TYPE="ext4"
/dev/mapper/sg30-swap_1: UUID="8897e94a-f70c-4e6a-85de-02f366fa3f62" TYPE="swap"
root@sg30:/usr/src/lcd-2.2# lsblk -f
NAME            FSTYPE      LABEL UUID                                   MOUNTPOINT
sda
&#9500;&#9472;sda1          ext2              e345a64a-69d6-4723-a469-2a9cd5dbb126   /boot
&#9500;&#9472;sda2
&#9492;&#9472;sda5          LVM2_member       ODLjqT-W8dR-mxfF-qTz5-LkBk-HWAW-a0tSbo
  &#9500;&#9472;sg30-root   ext4              71bc748b-9faa-425d-a3f6-69f619b8aa81   /
  &#9492;&#9472;sg30-swap_1 swap              8897e94a-f70c-4e6a-85de-02f366fa3f62   [SWAP]
sdb
&#9492;&#9472;sdb1          LVM2_member       PvAzgu-50oX-a26G-A26N-TDuN-Y06E-Vq0EV1
root@sg30:/usr/src/lcd-2.2#
```

-Raymond Day

---

### Post by Dennis N on 2020-12-22
Two defined PVs of sd30 have no named block device. They are in the warning message of post 5. Try using the -a option with vgreduce to see if they go away.  Then proceed with the outlined steps (post 2).

Also, Your command prompt in display of post 5 shows you are root user (#) so you needn't use sudo. That said, operating as root can lead to some messed up ownership if you forget you are root and continue working, so you should operate as a regular user and use sudo.

---

### Post by TheFu on 2020-12-22
This is a terrible idea, but  ...
[LIST]
[*]use **vgextend** to add the other PV into the existing VG.
[*]use **lvextend -r **to increase the size of any LV.  Don't forget the **-r** option, this resizes the file system at the same time. If you do forget that option, you'll need to extend the file system too, manually.
[/LIST]

This can all be done while online. Those commands are 5 seconds each. You'll spend more time reading the manpages or searching for examples than the run-time of both commands.

**Spanning VGs across multiple storage devices is a terrible idea**. Eventually, there will be data loss and crying.

---

### Post by darkod on 2020-12-22
I think your problem was not using pvcreate before the vgextend. Don't forget, with LVM you first need to use pvcreate on the new partition you want to use with LVM. Only after that you add that new partition to a VG using vgextend.

Like Dennis says, the non-identified devices seem to not be used (0 used extents) so try removing them from the VG. Once you do that continue with pvcreate and vgextend.

And like few people have mentioned here, don't forget that spanning VGs/LVs across multiple disks adds risk in case a disk fails. You should have good regular backups of your important data.

If you believe you need some redundancy, you can consider getting another 1TB disk, and then first create a mdadm raid1 array and then use that array as PV for LVM. But that is something you should do sooner rather than later if you wanna go that way.

In such case the raid would protect you against single disk failure, and the LVM on top of it gives you flexibility to work with LVs.

And backups you should always have, against accindental deletes, etc. None of the above is a replacement for backups.

---

### Post by TheFu on 2020-12-22
To add RAID1 to any existing LV, use **lvconvert** - lots of options around RAID inside LVM.  It is also a way to mirror an LV to another disk, then break that mirror once completed and remove the original.  No need for mdadm at all when LVM RAID is used.

About 5 yrs ago, I was at some storage training and they had decided that using RAID1 on enterprise SSDs really wasn't worth it. The failure rates were just so low for most uses. Only systems handling financial transactions would bother with RAID on enterprise SSDs.  Consumer SSDs failure rates still need RAID, if you don't want data loss, but usually when getting to more than 1TB, people switch to spinning disks for price reasons.

There is a really good reason to have large, RAID0 (striped), SSD storage and that is for temporary storage used in video processing.  In that situation, the rule has to never leave any files on that RAID0 storage overnight, but only while processing happens.  To get the stripe size optimized requires testing of multiple stripe sizes. The specific workload would would matter.  32M, 64M, 128M, 256M, 512M each would impact the overall performance. The kicker is that RAID0 has to be created with the multi-disk stripe, BEFORE any data gets placed onto the LV. It cannot be added later.

---

### Post by Raymond Day on 2020-12-22
Did the 1st command at the link gave in here but I get a error. Then I did the 2 other command said her but they are "No command with matching syntax recognised" Here is the code did.

```
root@sg30:/usr/src/lcd-2.2# cd /root
root@sg30:~# vgextend sg30 /dev/sdb
  WARNING: Device for PV pgxzPS-Wguk-sc1Q-GZE1-UafM-IpIY-33KSri not found or rejected by a filter.
  WARNING: Device for PV 6tpHZT-fCAs-GUOv-E6AU-B42o-O5X1-xJGQZt not found or rejected by a filter.
  Device /dev/sdb excluded by a filter.
root@sg30:~# vgextend
  No command with matching syntax recognised.  Run 'vgextend --help' for more information.
  Correct command syntax is:
  vgextend VG PV ...

root@sg30:~# lvextend -r
  No command with matching syntax recognised.  Run 'lvextend --help' for more information.
root@sg30:~#
```

What is the command to remove the [unknown] LVM?

Got Webmin on it and it says unknown on 2 of them and if I click on remove in Webmin it gives errors.

```
Failed to remove physical volume :
  Failed to find device for physical volume "[unknown]".
  WARNING: Device for PV pgxzPS-Wguk-sc1Q-GZE1-UafM-IpIY-33KSri not found or rejected by a filter.
  WARNING: Device for PV 6tpHZT-fCAs-GUOv-E6AU-B42o-O5X1-xJGQZt not found or rejected by a filter.
  Cannot change VG sg30 while PVs are missing.
  Consider vgreduce --removemissing.
  Cannot process volume group sg30
```

That my be what is wrong why can't get it to work.

-Raymond Day

---

### Post by Raymond Day on 2020-12-22
I think it worked don't get the unown now. Just did this command:

```
root@sg30:~# vgreduce sg30 --removemissing
  WARNING: Device for PV pgxzPS-Wguk-sc1Q-GZE1-UafM-IpIY-33KSri not found or rejected by a filter.
  WARNING: Device for PV 6tpHZT-fCAs-GUOv-E6AU-B42o-O5X1-xJGQZt not found or rejected by a filter.
  Wrote out consistent volume group sg30.
root@sg30:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               sg30
  PV Size               465.52 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               13
  Allocated PE          119160
  PV UUID               ODLjqT-W8dR-mxfF-qTz5-LkBk-HWAW-a0tSbo

  "/dev/sdb1" is a new physical volume of "931.51 GiB"
  --- NEW Physical volume ---
  PV Name               /dev/sdb1
  VG Name
  PV Size               931.51 GiB
  Allocatable           NO
  PE Size               0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               PvAzgu-50oX-a26G-A26N-TDuN-Y06E-Vq0EV1

root@sg30:~#
```

Now I can start over and hope do it right. [I will look at that link]("https://www.thegeekdiary.com/centos-rhel-how-to-remove-used-physical-volumepv-from-volume-group-vg-in-lvm/"). Maybe it will work.

-Raymond Day

---

### Post by Dennis N on 2020-12-22
**vgextend sg30 /dev/sdb** in post 11 should operate on the physical volume (pv) you are adding, not a disk  - should be:
```
sudo vgextend sg30 /dev/sdb1
```

Edit:
I would try to remove the spurious PVs in the warning before the above is done - if you don't, we'll see how it goes.

---

### Post by Raymond Day on 2020-12-22
It seems like it sees both now and are in the SG30 group but they do not look like one drive. Here one some commands I did.

```
root@sg30:~# lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/sda5        [     465.52 GiB] LVM physical volume
  /dev/sdb1        [     931.51 GiB] LVM physical volume
  0 LVM physical volume whole disks
  2 LVM physical volumes
root@sg30:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               sg30
  PV Size               465.52 GiB / not usable 2.81 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               13
  Allocated PE          119160
  PV UUID               ODLjqT-W8dR-mxfF-qTz5-LkBk-HWAW-a0tSbo

  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               sg30
  PV Size               931.51 GiB / not usable 296.50 KiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              238467
  Free PE               238467
  Allocated PE          0
  PV UUID               XWk9i7-JeIh-1C6g-xUtn-ifGv-eXk3-dO7og3

root@sg30:~# vgdisplay
  --- Volume group ---
  VG Name               sg30
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  12
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1.36 TiB
  PE Size               4.00 MiB
  Total PE              357640
  Alloc PE / Size       119160 / <465.47 GiB
  Free  PE / Size       238480 / 931.56 GiB
  VG UUID               0scfsB-UcgD-8KVW-Jk0q-2w4b-VT9I-801mMu

root@sg30:~# sudo vgextend sg30 /dev/sdb1
  Physical volume '/dev/sdb1' is already in volume group 'sg30'
  Unable to add physical volume '/dev/sdb1' to volume group 'sg30'
  /dev/sdb1: physical volume not initialized.
root@sg30:~#
```

It still shows 100 full.

```
root@sg30:~# df -h
Filesystem             Size  Used Avail Use% Mounted on
udev                   480M     0  480M   0% /dev
tmpfs                  100M  1.6M   99M   2% /run
/dev/mapper/sg30-root  456G  454G     0 100% /
tmpfs                  500M     0  500M   0% /dev/shm
tmpfs                  5.0M     0  5.0M   0% /run/lock
tmpfs                  500M     0  500M   0% /sys/fs/cgroup
/dev/sda1              228M  123M   94M  57% /boot
tmpfs                  100M     0  100M   0% /run/user/0
root@sg30:~#
```

I think all most got it fixed thanks for every ones help. Just need maybe one more right command.

-Raymond Day

---

### Post by TheFu on 2020-12-22
As other have said, which I missed, it appears a jump from partition --> VG, skipping the PV part happened.

LVM is just a partition type on the partition added by any partitioning tool. Nothing more. It shows up in output related to partition tools, and lsblk.

[LIST=1]
[*]File systems are placed onto an LV. The FS needs to be resized if the LV size changes.
[*]LVs are held within a VG. They can be RAID'ed or concatenated, thin provisioned or fully preallocated.
[*]A VG is held within one *or more* PVs.
[*]PVs are held by one of more partitions or "partition-like" objects (luks containers, for example).
[*]Partitions are held within a HDD/SSD.
[/LIST]

PV - Physical Volume (also called PEs or Physical Extents in other volume managers).
VG - Volume Group
LV - Logical Volume

These different objects have to be rolled and unrolled, **_in order_**, when doing things with LVM.

I like to see **pvs**, **vgs**, **lvs** output when working on LVM. These are much more compact versions of the 30 yr old pvdisplay, vgdisplay, lvdisplay commands.  Sometimes the full output is needed, like when doing RAID[0-10] within LVM or thin provisioning, but not really for other LVM information.

For example, I merged 2 disks on a 20.04 Mate desktop. Those disks are virtual and really on the same physical SSD:
```
$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/vda5  vgubuntu-mate lvm2 a--  <[COLOR="#008000"]29.50g[/COLOR]    0 
  /dev/vdb1  vgubuntu-mate lvm2 a--  <[COLOR="#008000"]10.00g[/COLOR] 6.39g
$ sudo vgs
  VG            #PV #LV #SN Attr   VSize  VFree
  vgubuntu-mate   2   3   0 wz--n- 39.49g 6.39g
$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  root   vgubuntu-mate -wi-ao---- 17.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g            
```

And just to show that fdisk has the LVM file system type:
```
Disk /dev/vda: [COLOR="#008000"]30 GiB[/COLOR], 32212254720 bytes, 62914560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa55500b1

Device     Boot   Start      End  Sectors  Size Id Type
/dev/vda1  *       2048  1050623  1048576  512M  b W95 FAT32
/dev/vda2       1052670 62912511 61859842 29.5G  5 Extended
/dev/vda5       1052672 62912511 61859840 29.5G 8e **Linux LVM**


Disk /dev/vdb: [COLOR="#008000"]10 GiB[/COLOR], 10737418240 bytes, 20971520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FADD8143-17B4-E446-B328-34BCE660B93C

Device     Start      End  Sectors Size Type
/dev/vdb1   2048 20971486 20969439  10G **Linux LVM**
```

And how lsblk shows this:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
vda                         [COLOR="#008000"]30G[/COLOR] disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;vgubuntu--mate-root     17G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         [COLOR="#008000"]10G[/COLOR] disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;vgubuntu--mate-root     17G lvm  ext4        /

```
vda and vdb are both on the same physical SSD, but presented to this virtual machine, regulus, as separate block storage devices. On the VM host, they are actually each LVs. Simplified lsblk output from the hypervisor host:
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                                SIZE TYPE FSTYPE      MOUNTPOINT
sdc                                 477G disk             
&#9500;&#9472;sdc2                                1K part             
&#9500;&#9472;sdc5                            476.2G part LVM2_member 
&#9474; &#9500;&#9472;hadar--vg-lv--regulus--2         [COLOR="#008000"]10G[/COLOR] lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--regulus            [COLOR="#008000"]30G[/COLOR] lvm         
```     

Sorry for the "Inception" stuff.  You can see why rolling and unrolling in the correct order is critical.

---

### Post by Raymond Day on 2020-12-22
Got to read the last post better yet just seen it. But I did some command [from this link]("https://www.thegeekdiary.com/centos-rhel-how-to-add-a-new-physical-volume-to-an-existing-volume-group/").

```
root@sg30:~# fdisk -l /dev/sdb
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00040670

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1           1 1953525167 1953525167 931.5G 8e Linux LVM
root@sg30:~# cat /proc/partitions | grep sdb
   8       16  976762584 sdb
   8       17  976762583 sdb1
root@sg30:~# pvs
  PV         VG   Fmt  Attr PSize    PFree
  /dev/sda5  sg30 lvm2 a--  <465.52g  52.00m
  /dev/sdb1  sg30 lvm2 a--   931.51g 931.51g
root@sg30:~# vgs
  VG   #PV #LV #SN Attr   VSize VFree
  sg30   2   2   0 wz--n- 1.36t 931.56g
root@sg30:~# lvs
  LV     VG   Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   sg30 -wi-ao---- <462.61g
  swap_1 sg30 -wi-ao----    2.86g
root@sg30:~# pvcreate /dev/sdb1
  Can't initialize physical volume "/dev/sdb1" of volume group "sg30" without -ff
  /dev/sdb1: physical volume not initialized.
root@sg30:~# vgextend sg30 /dev/sdb1
  Physical volume '/dev/sdb1' is already in volume group 'sg30'
  Unable to add physical volume '/dev/sdb1' to volume group 'sg30'
  /dev/sdb1: physical volume not initialized.
root@sg30:~#
```

-Raymond Day

---

### Post by Raymond Day on 2020-12-22
I did the command on the last link. It shows this:

root@sg30:~# lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME              SIZE TYPE FSTYPE      MOUNTPOINT
sda             465.8G disk
&#9500;&#9472;sda1            243M part ext2        /boot
&#9500;&#9472;sda2              1K part
&#9492;&#9472;sda5          465.5G part LVM2_member
  &#9500;&#9472;sg30-root   462.6G lvm  ext4        /
  &#9492;&#9472;sg30-swap_1   2.9G lvm  swap        [SWAP]
sdb             931.5G disk
&#9492;&#9472;sdb1          931.5G part LVM2_member
root@sg30:~#

Hope this helps.

I know when I had the drive on another computer I used gparted and it shows the LVM is in side a folder just about the same size as the LVM is. I don't know if this is the problems or not.

-Raymond Day

---

### Post by Dennis N on 2020-12-22
> It still shows 100 full.
You need to extend the root LV. Note you have 238480 free extents in the VG. (250 extents &#8773; 1 GB)
```
Free  PE / Size       238480 / 931.56 GiB
```

Also, you still are spanning 2 disks with the VG as indicated by post 17. That should be fixed by removing the sda5 PV from the VG with pvmove.

---

### Post by Raymond Day on 2020-12-22
I think I did it. Maybe have to reboot the command looked like this. But still says Used 100%. So that's why think got to reboot.

```
root@sg30:~# lvextend -l +100%free /dev/mapper/sg30-root
  Size of logical volume sg30/root changed from <462.61 GiB (118427 extents) to 1.36 TiB (356907 extents).
  Logical volume sg30/root successfully resized.
root@sg30:~# df -h
Filesystem             Size  Used Avail Use% Mounted on
udev                   480M     0  480M   0% /dev
tmpfs                  100M  1.6M   99M   2% /run
/dev/mapper/sg30-root  456G  454G     0 100% /
tmpfs                  500M     0  500M   0% /dev/shm
tmpfs                  5.0M     0  5.0M   0% /run/lock
tmpfs                  500M     0  500M   0% /sys/fs/cgroup
/dev/sda1              228M  123M   94M  57% /boot
tmpfs                  100M     0  100M   0% /run/user/0
root@sg30:~#
```

Maybe the sg30-root was wrong at the end of the command but it did say "root successfully resized." but I guess it should of said sg30 not root. But if I did just sg30 at the end of the command line it said Invalid path for Logical Volume.

Going to reboot it and see if it fixes it.

-Raymond Day

---

### Post by darkod on 2020-12-22
You extended the LV but you still need to resize the filesystem on it. Rebooting won't do that. You are missing one last command.
```
sudo resize2fs /dev/mapper/sg30-root
```

If you run it as root drop the sudo in front.

You added all the space to the LV at once, which is not usually how you use LVM and its point.

---

### Post by Raymond Day on 2020-12-22
I did reboot it but did not help.

But I did that command you said and it worked!

```
root@sg30:~# sudo resize2fs /dev/mapper/sg30-root
resize2fs 1.44.1 (24-Mar-2018)
Filesystem at /dev/mapper/sg30-root is mounted on /; on-line resizing required
old_desc_blocks = 29, new_desc_blocks = 88
The filesystem on /dev/mapper/sg30-root is now 365472768 (4k) blocks long.

root@sg30:~# df -h
Filesystem             Size  Used Avail Use% Mounted on
udev                   481M     0  481M   0% /dev
tmpfs                  100M  1.6M   99M   2% /run
/dev/mapper/sg30-root  1.4T  454G  859G  35% /
tmpfs                  500M     0  500M   0% /dev/shm
tmpfs                  5.0M     0  5.0M   0% /run/lock
tmpfs                  500M     0  500M   0% /sys/fs/cgroup
/dev/sda1              228M  123M   94M  57% /boot
tmpfs                  100M     0  100M   0% /run/user/0
root@sg30:~#

```

Now it says 35% used. Thank you it works now!

-Raymond Day

---

### Post by Raymond Day on 2020-12-22
Wow it's working good. I got 2 SSD's in it.

[URL="https://photos.app.goo.gl/XhhHiQQShmkFGtHB9"]Got this photo of it on my Google drive.
[/URL]

Started with ubuntu-16.04-server 32-bit and the only way it would boot was to pick LVM and good I did because I did not know would run out of room on the 500GB SSD have in it.

Updated it to Ubuntu Linux 18.04.4 now and logging in will say this.

```
login as: root
root@sg30's password:
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 4.15.0-128-generic i686)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
New release '20.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

They should do a little update to not way New release available if it is 32-bit that is what this is. So can't install the new release.

Thank you for all your help it works now.

-Raymond Day

---

### Post by CelticWarrior on 2020-12-22
32-bit is dead for all practical purposes.

If you really need 32-bit releases Debian is an option, along with no more than an handful of other releases. Nothing Ubuntu or Ubuntu based will have 32-bit releases going forward.

---

### Post by Raymond Day on 2020-12-23
> **CelticWarrior said:**
> 32-bit is dead for all practical purposes.

If you really need 32-bit releases Debian is an option, along with no more than an handful of other releases. Nothing Ubuntu or Ubuntu based will have 32-bit releases going forward.

That is good to know. But just can't do some command to update to Debian?

-Raymond Day

---

### Post by CelticWarrior on 2020-12-25
If by update you mean form 32-bit to 64-bit then no.

---

### Post by Raymond Day on 2020-12-25
> **CelticWarrior said:**
> 32-bit is dead for all practical purposes.

If you really need 32-bit releases Debian is an option, along with no more than an handful of other releases. Nothing Ubuntu or Ubuntu based will have 32-bit releases going forward.

Went to install a Debian with a CD ROM. That is the only USB drive that seems to boot with on the **Toshiba Inc. Magnia SG30.**

I picked LVM to install and it could not find the 2 10/100 cards. **Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller** and the other built in one is a **Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter** I put a USB to Ethernet on it and that worked. Installed it and worked about a hour looking on Google how to install the driver for them but nothing worked. I gave up and put the drives for Ubuntu back in it. Ubuntu had the Ethernet drives all the way back when I 1st installed it like Ubuntu 15 I think.

The USB drive that works with it is only a CD not a DVD reader.

-Raymond Day

---

### Post by TheFu on 2020-12-25
> **Raymond Day said:**
> That is good to know. But just can't do some command to update to Debian?

-Raymond Day

debian is a different distro with sllghtly different versions for many libraries. Many are compiled with different options. If it works, you will have a franken-distro that is neither ubuntu nor debian. There will be issues and some will not be fixable. The best answer is to find a way to backup all data, settings and shortest possible list of manually installed software, then wipe everything and start fresh. With the new, desired, OS.  This applies for many migration paths and is a good skill to have even when moving ubuntu releases to new hardware.

---

### Post by darkod on 2020-12-25
If I understood correctly the main problem here is that the CPU is 32bit. If you insist to keep using the machine then you will face very limited number of new OSs with 32bit support.

For example Ubuntu does not publish 32bit images any more I think. This is why it is not just a matter of wipe + reinstall.

---

### Post by Raymond Day on 2020-12-25
Yes that is why it is a 32 bit CPU and a post in here says Debian is still update with 32 bit CPU.

I put a new 1 TB SD NAND and install it. But said can't find Ethernet. It has 2 Ethernet only 10/100 no 1000. I just don't know why Debian does not have Ethernet drives. It showed a lot and I went on the line and pressed Enter and it just went back to the lines of drivers. So I give up.

I installed it with server not desktop.

Does anyone know how I could install the right driver for Ethernet? I posted what they are here. If I can get it work I guess it will update for years then. It was Debian 10. I guess that is the lasted one.

-Raymond Day

---

### Post by rsteinmetz70112 on 2020-12-27
It may be time to get a new machine. Even a raspberry pi is likely more powerful that what you have now.

---

