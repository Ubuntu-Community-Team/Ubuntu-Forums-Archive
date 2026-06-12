---
title: "Where is my space"
date: 2019-02-02
forum: Server Platforms
---

### Post by pirlea on 2019-02-02
Hello everyone,

I am running virtual Ubuntu 18 server on the ESXi. To be honest didn't really pay attention to the new installer durung installation but I was sure I have alocated enough space for my needs (home automation).
Today I decided to install MySQL server and the system is telling me:
ERROR: There's not enough space in /var/lib/mysql/
So I checked with:
```

# lshw -C
  *-disk
       description: SCSI Disk
       product: Virtual disk
       vendor: VMware
       physical id: 0.0.0
       bus info: scsi@32:0.0.0
       logical name: /dev/sda
       version: 2.0
       size: 16GiB (17GB)
       capabilities: 7200rpm gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=6 guid=aad93d6a-0817-4aac-9136-42b20d13f6f6 logicalsectorsize=512 sectorsize=512
  *-cdrom
       description: DVD-RAM writer
       product: VMware SATA CD00
       vendor: NECVMWar
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

```
But here is another check:
```

# df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               464M     0  464M   0% /dev
tmpfs                               99M  1.2M   98M   2% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  3.9G  3.5G  195M  95% /
tmpfs                              493M     0  493M   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              493M     0  493M   0% /sys/fs/cgroup
/dev/loop0                          92M   92M     0 100% /snap/core/6259
/dev/loop1                          91M   91M     0 100% /snap/core/6350
/dev/loop2                         1.9M  1.9M     0 100% /snap/mosquitto/121
/dev/loop3                          90M   90M     0 100% /snap/core/6130
/dev/sda2                          976M  207M  703M  23% /boot
tmpfs                               99M     0   99M   0% /run/user/1000

```
Fdisk is telling me that most of my space is allocated to sda3 but where is it?
```

 fdisk -l
Disk /dev/loop0: 91.1 MiB, 95494144 bytes, 186512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 1.8 MiB, 1896448 bytes, 3704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 89.5 MiB, 93835264 bytes, 183272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 16 GiB, 17179869184 bytes, 33554432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AAD93D6A-0817-4AAC-9136-42B20D13F6F6

Device       Start      End  Sectors Size Type
/dev/sda1     2048     4095     2048   1M BIOS boot
/dev/sda2     4096  2101247  2097152   1G Linux filesystem
/dev/sda3  2101248 33552383 31451136  15G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 4 GiB, 4294967296 bytes, 8388608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

At this point I gave up and have absolutely no desire to reinstall the system as I just got Mosquitto up and running and all iOT devices connected.
Please help!
Thank you.

---

### Post by TheFu on 2019-02-02
3.5G is tight for any full server install if you don't remove most of the automatic packages.
Much easier to just give a server 8G assuming there isn't any data stored there and you won't load any GUI stuff.

Use VMware tools to expand the vHDD. Since you used LVM, you'll need to 
* expand the partition
* increase the PEs
* increase the VGs
* resize the LV  with ext4, you can do this on the running system.

The output from **sudo pvs**, **sudo vgs** and **sudo lvs** will confirm stuff.  If you need more detailed data, the old-school LVM commands are still there - vgdisplay, lvdisplay and pvdisplay.

BTW, no need to show loop devices ever, unless you are working a snap-specific issue.  Snaps probably aren't very useful for most things in the setup and they do use extra storage.  

I don't know anything about home automation - that would be the only things where using a snap could make life much easier and I'd use it, if available.  I don't use snaps and have removed all the snap-based packages and the snap-infrastructure so they don't get installed again.  Snaps are all bad and there definitely are some great uses for them.

---

### Post by darkod on 2019-02-03
Like TheFu says, check the LVM size and status and you should find your "lost" space.

In short, it look like you have the 15GB in the VG but the root LV is only 4GB as it is. If you are happy having only 16GB for this server (otherwise why would you assign it so small disk in vmware???), then you don't even need to expand the disk and partition.

Simply extend the root LV to use all the 15GB in the VG. That is unless you plan to create other LVs.

---

### Post by pirlea on 2019-02-03
> **darkod said:**
>  why would you assign it so small disk in vmware???

This is where my frustration is coming from because it was not intensional.
I completely relied on the installer to use entire disk and looks like it didn't.

---

### Post by pirlea on 2019-02-03
Here are the outputs:
 ```

 PV         VG        Fmt  Attr PSize   PFree
  /dev/sda3  ubuntu-vg lvm2 a--  <15.00g <11.00g

```

```

  VG        #PV #LV #SN Attr   VSize   VFree
  ubuntu-vg   1   1   0 wz--n- <15.00g <11.00g

```

```

  LV        VG        Attr       LSize Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 4.00g

```

This is frustrating. Since when installer doesn't default to entire disk? I know it's still my fault because I dodn't check during installation but...
Thank you all.

INTERESTING :)
```

sudo resize2fs /dev/sda3
resize2fs 1.44.1 (24-Mar-2018)
resize2fs: Device or resource busy while trying to open /dev/sda3
Couldn't find valid filesystem superblock.

```

---

### Post by TheFu on 2019-02-03
It is new to me too, but it has been a complaint of mine that they did use the whole space for the root-vg for many years now.  On a server like you intend, it wouldn't be bad, but for most business server needs, having the entire VG take the entire disk isn't what I want.  Also, I'd like to have multiple LVs for different parts of the OS.  Definitely split out /var and /home into their own LVs, for example.  And if they leave lots of extra space in the VG, getting the correct sizing would be relatively easy.   For all the issues with 18.04 that I don't really like, this LVM setup change actually has me excited.

At install time, using LVM was selected.  It wasn't mandatory.  I've not installed 18.04 enough to know what those defaults choose.  I always choose LVM for the added flexibility it provides.  Nice not to have to boot from alternate media to change partitions around. LVM is so much more convenient almost always.  But it is a hassle for anyone unfamiliar with LVM capabilities and extra complexities, that is certain.  But when it comes time to change out hardware, the LVM move commands totally make up for that.

Thanks for the output. There is **good news**.  You only need to use 1 command to increase the space AND increase the file system at the same time.  No downtime is needed either.  No need to umount or boot from alternate media.  **lvextend**.  Use the -L and -r options. The file system can be online and in use.  This assumes ext4 is the file system. Other file systems cannot be extended in the single command and some can't be extended while online.  You can check that ext4 is being used with the **df -hT** command or **mount** command.

LVM rocks.

---

### Post by pirlea on 2019-02-03
Here is the output of df

```

 df -hT
Filesystem                        Type      Size  Used Avail Use% Mounted on
udev                              devtmpfs  464M     0  464M   0% /dev
tmpfs                             tmpfs      99M  1.2M   98M   2% /run
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      3.9G  3.6G  112M  98% /
tmpfs                             tmpfs     493M     0  493M   0% /dev/shm
tmpfs                             tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs                             tmpfs     493M     0  493M   0% /sys/fs/cgroup
/dev/loop0                        squashfs   92M   92M     0 100% /snap/core/6259
/dev/loop1                        squashfs   91M   91M     0 100% /snap/core/6350
/dev/loop2                        squashfs  1.9M  1.9M     0 100% /snap/mosquitto/121
/dev/loop3                        squashfs   90M   90M     0 100% /snap/core/6130
/dev/sda2                         ext4      976M  207M  703M  23% /boot
tmpfs                             tmpfs      99M     0   99M   0% /run/user/1000

```

LVM is new to me and looks like lvextend is waiting for more arguments
Would you mind guiding me through please?

```

 sudo lvextend -L -r
  Size requires number argument.
  Invalid argument for --size: -r
  Error during parsing of command line.

```

---

### Post by pirlea on 2019-02-03
Here is mount output:
```

 mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=474212k,nr_inodes=118553,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=100964k,mode=755)
/dev/mapper/ubuntu--vg-ubuntu--lv on / type ext4 (rw,relatime,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14057)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/core_6259.snap on /snap/core/6259 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_6350.snap on /snap/core/6350 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/mosquitto_121.snap on /snap/mosquitto/121 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_6130.snap on /snap/core/6130 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda2 on /boot type ext4 (rw,relatime,data=ordered)
lxcfs on /var/lib/lxcfs type fuse.lxcfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)
tmpfs on /run/snapd/ns type tmpfs (rw,nosuid,noexec,relatime,size=100964k,mode=755)
nsfs on /run/snapd/ns/mosquitto.mnt type nsfs (rw)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=100960k,mode=700,uid=1000,gid=1000)


```

---

### Post by pirlea on 2019-02-03
I get your point about server installation where host OS should not consume all the space. This makes complete sense. What could be done though in this all new and fancy installer - add a note of that: "Default space allocation seetings have been changed..." Because someone experienced (like you) will figure this out and someone who is using it at home - most likely doesn't have all that knowledge. 

> **TheFu said:**
>  **lvextend**.  Use the -L and -r options. 

This worked to allocate all available space:

```
lvextend -l +100%FREE -r /dev/mapper/ubuntu--vg-ubuntu--lv
```


Thank you.

---

### Post by TheFu on 2019-02-03
> **pirlea said:**
> I get your point about server installation where host OS should not consume all the space. This makes complete sense. What could be done though in this all new and fancy installer - add a note of that: "Default space allocation seetings have been changed..." Because someone experienced (like you) will figure this out and someone who is using it at home - most likely doesn't have all that knowledge. 

This worked to allocate all available space:

```
lvextend -l +100%FREE -r /dev/mapper/ubuntu--vg-ubuntu--lv
```


Thank you.

Please use the **Thread Tools button** near the top to mark this as "SOLVED" - it helps the community out.

I knew you'd figure it out.  I wouldn't have allocated all of it. Leaving a little, say 1G would give you time to fix it quickly for a short period when it fills up again, so you can plan some down-time to expand it into a larger vHDD.

Also, I would have used the -L , not -l.  They are different. From the manpage on my system:
```
       -l, --extents [+]LogicalExtentsNumber[%{VG|LV|PVS|FREE|ORIGIN}]
              Extend or set the  logical  volume  size  in  units  of  logical
              extents.   With  the  '+'  sign the value is added to the actual
              size of the logical volume and without it, the value is taken as
              an absolute one.  The total number of physical extents allocated
              will be greater than this, for example, if the  volume  is  mir-
              rored.   The number can also be expressed as a percentage of the
              total space in the Volume Group with the suffix %VG, relative to
              the  existing size of the Logical Volume with the suffix %LV, of
              the remaining free space  for  the  specified  PhysicalVolume(s)
              with  the  suffix  %PVS,  as  a percentage of the remaining free
              space in the Volume Group with the suffix %FREE, or (for a snap-
              shot)  as  a percentage of the total space in the Origin Logical
              Volume with the suffix %ORIGIN.  The resulting value is  rounded
              upward.   N.B. In a future release, when expressed as a percent-
              age with PVS, VG or FREE, the  number  will  be  treated  as  an
              approximate upper limit for the total number of physical extents
              to be allocated (including extents  used  by  any  mirrors,  for
              example).   The  code may currently allocate more space than you
              might otherwise expect.

       -L, --size [+]LogicalVolumeSize[bBsSkKmMgGtTpPeE]
              Extend or set the logical volume size in units of megabytes.   A
              size  suffix  of  M  for  megabytes, G for gigabytes, T for ter-
              abytes, P for petabytes or E for exabytes is optional.  With the
              + sign the value is added to the actual size of the logical vol-
              ume and without it, the value is taken as an absolute one.
```

The Canonical guys have been trying to simplify things in the installer to make it less intimidating. People get overwhelmed with lots of text.  The release notes for the disto did highlight changes to the installer.  [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
**Server**
>  LVM Entire Disk option does not use entire disk (1785321)

    Partitioning step allows to configure LVM across multiple devices without requiring to setup a separate /boot partition. This may lead to failure to install the bootloader at the end of the installation, and failures to boot the resultant installations. (1680101)

    LVM configuration cannot be removed when volume groups with the same name are found during installation. Partitioner does not support installation when multiple conflicting/identical volume groups have been detected. For example reinstalling Ubuntu with LVM across multiple disk drives that had individual LVM installations of Ubuntu. As a workaround, please format disk drives prior to installation, or from the built in shell provided in the installer. (1679184) 
On Unix servers, reading the release notes is important.

---

