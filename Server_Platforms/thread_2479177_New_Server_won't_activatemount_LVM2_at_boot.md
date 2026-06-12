---
title: "New Server won't activate/mount LVM2 at boot"
date: 2022-09-16
forum: Server Platforms
---

### Post by gimpacause on 2022-09-16
Hi all i recently replaced my boot drive and one of the PSU's in my ubuntu server consisting of 3 RAID Arrays
upon setting everything up i can only get one array (md4) to mount on boot




md4 consisting of 2 SSD's in Raid 0 this mounts and works every reboot no issues
md0 consisting of 15 6TB drives,Raid6 with LVM on top, this is giving me issues 
md1 consisting of 15 - 18TB drives, these are disconnected until i can get md0 working


if i try to mount md0 I get the following




```
ben@themachine:/mnt/files$ sudo mount -a
mount: /mnt/files: /dev/md0 already mounted or mount point busy.
ben@themachine:/mnt/files$

```
the content of my fstab is as follows
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-btSD40Ct9ACHlNUsRyHgIxCUbP3augnvPW1CWMW03zSSVTBfask>
# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/e888c9f1-7cf6-4c3c-965e-cf1a9d7fe97a /boot ext4 defaults 0 1
/swap.img       none    swap    sw      0       0
/dev/md0 /mnt/files  xfs defaults,nofail,discard 0 0
/dev/md4 /mnt/sabssd xfs defaults,nofail,discard 0 0
```


contents of mdadm.conf is


```

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


# This configuration was auto-generated on Tue, 09 Aug 2022 11:56:48 +0000 by mkconf
ARRAY /dev/md0 metadata=1.2 name=ubuntu:0 UUID=0a62c2c5:6ca30a41:e6f132f9:11bef5db
ARRAY /dev/md4 metadata=1.2 name=themachine:4 UUID=3af8c717:4691cf13:15f63753:ca57b0e1
```


details of the array are 


```

/dev/md0:
           Version : 1.2
     Creation Time : Tue Dec 30 08:46:32 2014
        Raid Level : raid6
        Array Size : 76185088512 (70.95 TiB 78.01 TB)
     Used Dev Size : 5860391424 (5.46 TiB 6.00 TB)
      Raid Devices : 15
     Total Devices : 15
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Fri Sep 16 08:58:38 2022
             State : clean
    Active Devices : 15
   Working Devices : 15
    Failed Devices : 0
     Spare Devices : 0


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : ubuntu:0
              UUID : 0a62c2c5:6ca30a41:e6f132f9:11bef5db
            Events : 1118627


    Number   Major   Minor   RaidDevice State
       0       8       96        0      active sync   /dev/sdg
       1       8      112        1      active sync   /dev/sdh
       2       8      208        2      active sync   /dev/sdn
       3       8       80        3      active sync   /dev/sdf
       4       8      224        4      active sync   /dev/sdo
       5       8       16        5      active sync   /dev/sdb
       6       8      176        6      active sync   /dev/sdl
       7       8      192        7      active sync   /dev/sdm
       8       8      160        8      active sync   /dev/sdk
       9       8       48        9      active sync   /dev/sdd
      10       8        0       10      active sync   /dev/sda
      11       8      144       11      active sync   /dev/sdj
      12       8       32       12      active sync   /dev/sdc
      13       8       64       13      active sync   /dev/sde
      14       8      128       14      active sync   /dev/sdi
```


browsing the web  I found a way to get the array mounted and working fine, but after each reboot, md0 is not mounted, the following is what works to mount it and write to it


```

root@themachine:/mnt# sudo vgchange -a y data0
  1 logical volume(s) in volume group "data0" now active
root@themachine:/mnt# mount -t xfs /dev/data0/lvm0 /mnt/files
```


I am assuming the fact that i am marking the VG as active is what is allowing me to mount it, my question is how do I permanently  make it active, in all my server upgrades/moves with these array's I have not come across this, my last fresh install was for ubuntu 18.04 LTS, now since going to 22.04
i have to manually mark the VG as active


any help would be greatly appreciated ,

thank you

---

### Post by TheFu on 2022-09-16
You aren't using LVM.  
You are using mdadm.  
Very different.

You could have used LVM, without mdadm, but didn't.  At least that's what I'm seeing above.  If you think you setup LVM over mdadm RAID stuff, then please post the output from 

```
sudo pvs
sudo vgs
sudo lvs

```
so we can actually see the LVM stuff.

Also, ensure that the mount points already exist.  I think systemd-mount doesn't require that, but pre-systemd-mount, it was mandatory.  I never expect systemd-mount to actually work. Perhaps it is just working in ways that aren't like it has been the last 30 yrs? IDK. The systemd guys tend to change things for completely unknown reasons rather than leave the interfaces that worked before alone.  For example, I really miss the **sudo touch  /forcefsck ** method to get / fsck'd on the next boot.  It is 100x harder now.

---

