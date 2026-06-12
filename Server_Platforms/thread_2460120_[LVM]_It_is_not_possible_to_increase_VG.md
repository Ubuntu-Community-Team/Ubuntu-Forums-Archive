---
title: "[LVM] It is not possible to increase VG"
date: 2021-04-02
forum: Server Platforms
---

### Post by jonnathanclay on 2021-04-02
Hello community
I am trying to increase the size of a VG and I ran into several problems, these are the steps that I executed:

Add additional disk space. When executing **fdisk -l** to verify the space it showed me this message:


```
[COLOR=#ff0000]**GPT PMBR size mismatch (41943039 != 62914559) will be corrected by write.**[/COLOR][COLOR=#ff0000]**The backup GPT table is not on the end of the device. This problem will be corrected by write.**[/COLOR]
Disk /dev/sda: 30 GiB, 32212254720 bytes, 62914560 sectors
Disk model: QEMU HARDDISK   
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FA3DBA3B-C8B5-45A6-AE60-8FA3EF5C9794


Device       Start      End  Sectors Size Type
/dev/sda1     2048     4095     2048   1M BIOS boot
/dev/sda2     4096  2101247  2097152   1G Linux filesystem
**/dev/sda3  2101248 25163775 23062528  11G Linux filesystem**
```

I googled and found that I had to enter the parted application to correct it, then I did the following:

```
root@container:~# **parted**GNU Parted 3.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) help                                                             
  align-check TYPE N                       check partition N for TYPE(min|opt) alignment
  help [COMMAND]                           print general help, or help on COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition table)
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table, available devices, free space, all found partitions, or a particular partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START and END
  resizepart NUMBER END                    resize partition NUMBER
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  disk_set FLAG STATE                      change the FLAG on selected device
  disk_toggle [FLAG]                       toggle the state of FLAG on selected device
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and copyright information of GNU Parted
(parted) **print**                                                            
**Warning: Not all of the space available to /dev/sda appears to be used, you can fix the GPT to use all of the space (an extra 20971520 blocks) or continue with the current setting? **


Fix/Ignore? **Fix**                                                           
Model: QEMU QEMU HARDDISK (scsi)
Disk /dev/sda: 32.2GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2097kB  1049kB                     bios_grub
 2      2097kB  1076MB  1074MB  ext4
 3      1076MB  12.9GB  11.8GB
```

It no longer shows me the GPT PMBR message, so I check the volume information

```
root@container:~# df -h |grep ubuntu--vg-ubuntu
/dev/mapper/ubuntu--vg-ubuntu--lv   11G  8.8G  1.5G  86% /

root@container:~# lvs
  LV        VG        Attr       LSize    Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao----  <11.00g                                                    
  lv-0      vg0       -wi-ao---- <500.00g

root@container:~# vgs
  VG        #PV #LV #SN Attr   VSize    VFree
  **ubuntu-vg**   1   1   0 wz--n-  <11.00g    **0** 
  vg0         1   1   0 wz--n- <500.00g    0
```

I try to extend the space of the ubuntu-vg

```
root@container:~# vgextend ubuntu-vg /dev/sda
  **Device /dev/sda excluded by a filter.**
```

I check inside the /etc/lvm/lvm.conf file if there is any uncommented filter and I can't find any

Of course this doesn't work either since I don't have free space on the VG

```
root@container:~# lvextend /dev/ubuntu-vg/ubuntu-lv -l +100%FREE -r  Size of logical volume ubuntu-vg/ubuntu-lv unchanged from <11.00 GiB (2815 extents).
  Logical volume ubuntu-vg/ubuntu-lv successfully resized.
resize2fs 1.45.5 (07-Jan-2020)
The filesystem is already 2882560 (4k) blocks long.  Nothing to do!
```

I tried this that I read in a corner of the internet that could work

```
root@container:~# wipefs -a /dev/sda
wipefs: error: /dev/sda: probing initialization failed: Device or resource busy
```

I don't know what to do anymore, could someone please help me 

All of this is happening under [COLOR=#a9a9a9]*Ubuntu 20.04.2*[/COLOR]

---

### Post by volkswagner on 2021-04-02
I'm no expert but at a quick glance, I expected to see a pvextend command.
You grew the partition but didn't grow the physical volume before extending
the volume group. 

I look at LVM as hierarchal:
PV
--VG
----LV

---

### Post by darkod on 2021-04-03
After you tried the fix in parted, is that output how currently the disk is? I mean it says sda3 is 12GB but you made the disk to be 30GB I understand. So you would want now to resize the partition, yes?

Before you even get to LVM tools, you need to take care of the disk first. You have two options:

1). Resize current sda3 partition.
2). Create new sda4 partition and use it as PV for LVM too.

Depending what you choose to do, the commands for LVM after that will be slightly different.

1). You need to use pvresize to make it use the new size of sda3.
2). You use pvcreate to start the process to use sda4 in the LVM.

If you need more help after completing these steps, ask here. Be careful of not running any command that you see fit unless you really know what it is for. That is if you care for the data on the disk. Otherwise simply format it and start from zero and problem solved.

For example that wipefs is making me nervous. Maybe because I've never seen it before. :) If you have data that you want to keep, I would be very careful with commands having 'wipe' in their name.

---

### Post by jonnathanclay on 2021-04-03
Thanks for the answers

Do the following:


Free space available in **sda **and[B] sda3

[/B]
```
root@container:~# **fdisk /dev/sda**

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.




Command (m for help): F
**Unpartitioned space /dev/sda: 18 GiB**, 19328384512 bytes, 37750751 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


   Start      End  Sectors Size
25163776 62914526 37750751  **18G**
```


```
root@container:~#** fdisk /dev/sda3**

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


[COLOR=#ff0000]The old LVM2_member signature will be removed by a write command.[/COLOR]


Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0x9ad59447.


Command (m for help): F
Unpartitioned space /dev/sda3: 10.102 GiB, 11806965760 bytes, 23060480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Start      End  Sectors Size
 2048 23062527 23060480  11G
```

```
root@container:~# pvdisplay
 [COLOR=#a9a9a9]  --- Physical volume ---[/COLOR]
[COLOR=#a9a9a9]  PV Name               /dev/sdb[/COLOR]
[COLOR=#a9a9a9]  VG Name               vg0[/COLOR]
[COLOR=#a9a9a9]  PV Size               500.00 GiB / not usable 4.00 MiB[/COLOR]
[COLOR=#a9a9a9]  Allocatable           yes (but full)[/COLOR]
[COLOR=#a9a9a9]  PE Size               4.00 MiB[/COLOR]
[COLOR=#a9a9a9]  Total PE              127999[/COLOR]
[COLOR=#a9a9a9]  Free PE               0[/COLOR]
[COLOR=#a9a9a9]  Allocated PE          127999[/COLOR]
[COLOR=#a9a9a9]  PV UUID               Lkw4CF-yS4I-Vcld-UMuR-eiwz-bwiU-xw3Wgt[/COLOR]
   
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               ubuntu-vg
  PV Size               <11.00 GiB / not usable 1.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              2815
**  Free PE               0**
  Allocated PE          2815
  PV UUID               oFuEAI-onjW-3Gki-J77s-fDSt-PYRJ-7Gc11O
```

It does not make any changes, I understand that sda3 still does not have free space available and I do not know how to allocate it

```
root@container:~#** pvresize /dev/sda3**  Physical volume "/dev/sda3" changed
  1 physical volume(s) resized or updated / 0 physical volume(s) not resized
root@container:~#
```

Maybe something needs to be done on the partition table?

---

### Post by jonnathanclay on 2021-04-03
I made it!
```
root@container:~# df -h |grep ubuntu
/dev/mapper/ubuntu--vg-ubuntu--lv   29G  8.8G   19G  33% /
```


I found a detailed tutorial of the steps to follow, I hope it can help more people

[English]("https://theducks.org/2009/11/expanding-lvm-partitions-in-vmware-on-the-fly/") (ext4 FS)
[Spanish]("https://www.ionos.es/ayuda/servidores-cloud/administracion-del-servidor/adaptar-el-volumen-logico-despues-de-ampliar-la-ssd/adaptar-el-volumen-logico-despues-de-haber-ampliado-el-disco-ssd-en-centos-8-cloud-server/") (xfs FS)

The last command may vary if the FS is ext4 or xfs

---

### Post by TheFu on 2021-04-03
All the *display commands are old-school. Most of the time, we only need summaries of the relevant LVM information.
```
sudo pvs
sudo vgs
sudo lvs
```
provides the complete view of LVM objects and LVM storage.

For a nice overview of all storage, **lsblk -e 7 -o name,size,type,fstype,mountpoint** is a very handy alias, as is **df -hT -x squashfs -x tmpfs -x devtmpfs**

---

