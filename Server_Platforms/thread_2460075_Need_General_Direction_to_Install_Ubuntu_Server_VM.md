---
title: "Need General Direction to Install Ubuntu Server VM Host and Boot From ZFS"
date: 2021-04-01
forum: Server Platforms
---

### Post by opposablegums on 2021-04-01
I'm not a complete novice.  I've been using the command-line since pre-PC days, some 40 years ago.  I was an early Macintosh user, and then spent most of the last 30 years managing Windows servers and networks.  I've played with the Linux command-line from time to time for the past 5 years.  Nevertheless, I'm a novice concerning Linux, and particularly Ubuntu Server.

The goal is to replace a Windows Server featuring Hyper-V host, and three Server VM Guests.  The new hardware is based on a SuperMicro MBD-H12SSL-NT motherboard with 128GB RAM.  This motherboard does NOT include the RAID controller, but rather interfaces the disks directly.   The CPU is a single Epyc 7262, Rome, 7002 series, with 8 cores.

When I say "Need General Direction", **_I'm asking for help to find documentation_** on ZFS and using it to install Ubuntu Server as a VM Host using as many built-in tools as possible.  

My current understanding is that it's possible to boot from ZFS.  It's possible to create a VM Host using KVM and QEMU without using a third party Host.  It would be ideal to find technical manuals on these specific subjects and white papers which include example procedures.  Also, I welcome your comments, suggestions, and advice.

I've spent a few weeks investigating and now feel totally confused over conflicting information.  I recognize that ZFS is considered experimental on Ubuntu Server and that some tools are non-existent, for example to add additional disks after the original configuration.  However, it appears to me that it's possible to boot from a Live flash drive, define the ZFS array, install GRUB, and then install Ubuntu Server.  

The rest of my new hardware will arrive in about a week, and since the current Microsoft Server is still functioning fine, there's no rush.  I have time to experiment, including any experiments that you may suggest.  I expect to try multiple installations while writing my own white paper.  Thank you ahead of time for your gentle guidance.

---

### Post by guiverc on 2021-04-02
Have you tried looking at the Tutorials available on Ubuntu, 

[https://ubuntu.com/tutorials/install-ubuntu-server#1-overview](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview) is the first I see

With the introduction of ZFS in Ubuntu, loads of tutorials & introductions have been written in the last six months (not full  [tutorials]("https://ubuntu.com/tutorials") but introductory with links sending you elsewhere if you needed more) as I recall reading & summarizing some for the UWN (Ubuntu Weekly Newsletter), and that's were I'd look up details on ZFS (they were a pretty useful primer).

If you remember the pre-PC days; you should feel at home; as I think of GNU/Linux (Ubuntu etc) as just a unix OS just like I learnt in the early 80s (pre-DOS let alone pre-windows; when microsoft sold Xenix but IBM didn't want it)

---

### Post by TheFu on 2021-04-02
**A warning that I hope you'll hear and pay attention to.**

**[COLOR="#FF0000"]Don't use ZFS as a boot drive for the OS.  Don't.  [/COLOR]**

At your stage, it won't turn out good when there is an issue. The 20.04 installer will let you do this - it is marked as "experimental". Probably not a good idea on a system that will become production in a week.  I tried the ZFS experiment for a few hours on a fresh 20.04 install.  All sorts of things were just bad. I couldn't directly trace the issues back to ZFS.  After having terrible performance and unable to solve that, I did another install using LVM. The performance was blazing. This was last June. Maybe things are better now?  I'll wait until Canonical says ZFS is production ready for the OS in an LTS release (22.04 is the next one) before I try that again.

Definitely use ZFS for data and VM storage.  Linux doesn't have 1 file system. We can use 1, 5, 20 on the same system without problems, but for the boot and OS storage, please, please use ext4  OR ext4 on LVM.  ZFS should be used for data, if possible.  These ideas of different file systems is one that Windows people sometimes don't consider.  It isn't an all or nothing choice.

If you've used Veritas on your Windows Servers, then LVM won't be hard. Exactly the same ideas - PEs, VGs, LVs.  LVM works fantastic to provide enterprise storage management for the OS.  Do a base Ubuntu Server install, have only the boot/OS SSD installed for that, select LVM during the install. Bob's your uncle.  Immediately after the install, boot from the install media and resize the "root" LV to be 25-35G, create a "swap" LV and enable that in the fstab for on the SSD, remove the swapfile from the now-mounted "root" LV.  You'll probably want a "var" LV too - start with 5G.  Why?  The installer is lazy and usually creates a huge "root" LV - perhaps 200G.  That's just crazy. Keeping the OS, /home, /var, and swap separate has been a time-proven solution to common Unix needs. If you don't have really good reasons, stick with that outline and keep the LVs small to start and mount them into those places after you migrate the specific directories from the huge "root" LV as needed.  It should take just a few minutes on current hardware.  Storage design is all about backups and planned OS upgrades for me. Keeping the OS separate makes clear delineations between different types of data.

With LVM, the trick is to allocate only the storage you need for the next 3 months.  Extending LVs is 5 seconds while the system is up, busy, working.  Shrinking them requires that the storage not be mounted, that often means downtime. Also, some guides will say to use XFS - but XFS doesn't allow shrinking. Ext4 does. The lvreduce and lvextend commands both can grow and shrink ext4 file systems with just an extra option.

Next connect the other storage devices and tell ZFS about them. Hopefully you'll run those as RAID1 or RAIDz2. I wouldn't use any other choices.

KVM supports block storage devices, so LVM or ZFS can be used to provide a VM with storage.  I've never used ZFS in that way, so I can't help. I do know that KVM + libvirt + virt-manager make creating a new LV for each VM that needs storage pretty trivial, provided the VG has room.  An example for a KVM server using LVM storage:

```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
sdb                               477G disk             
&#9500;&#9472;sdb1                            731M part ext2        /boot
&#9500;&#9472;sdb2                              1K part             
&#9492;&#9472;sdb5                          476.2G part LVM2_member 
  &#9500;&#9472;hadar--vg-root               32.3G lvm  ext4        /
  &#9500;&#9472;hadar--vg-swap_1              4.3G lvm  swap        [SWAP]
  &#9500;&#9472;hadar--vg-libvirt--lv         175G lvm  ext4        /var/lib/libvirt
  &#9500;&#9472;hadar--vg-lv--vpn09--1804     7.5G lvm              
  &#9500;&#9472;hadar--vg-lv--xen41--1804    12.5G lvm              
  &#9500;&#9472;hadar--vg-lv--blog44--1804   16.2G lvm              
  &#9500;&#9472;hadar--vg-lv--zcs45--1804      25G lvm              
  &#9500;&#9472;hadar--vg-lv--spam3            10G lvm              
  &#9500;&#9472;hadar--vg-lxd--lv              60G lvm  ext4        /var/lib/lxd
  &#9500;&#9472;hadar--vg-lv--regulus          30G lvm              
  &#9500;&#9472;hadar--vg-lv--regulus--2       10G lvm              
  &#9500;&#9472;hadar--vg-lv--opnsense          5G lvm              
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tmeta   108M lvm              
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm              
  &#9492;&#9472;hadar--vg-lv--tp--lxd_tdata  32.2G lvm              
    &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm
```
See how there aren't mounts for much of the LVs? Those are presented to VMs directly.

I've only played with ZFS and only when forced to use it for LXD containers.  I'm too stupid to figure out how to have LXD use LVs directly and ZFS is what the LXD team has decided everyone should use.  That's fine.  LVM --> PV-->VG-->LV -->file for ZFS --> LXD containers

I'm a big believer in keeping things, especially production things, simple. I prefer NOT to mix file systems, especially for RAID purposes, across different physical storage ... unless 100% of the storage will be used (well, I always create partitions to hold RAID or LVM stuff).

Both LVM and ZFS support real snapshots, so you won't have to give up that capability.  Of course, with both, you'll need to manage snapshots so storage doesn't run out.  It is nice to make a snapshot just before doing any upgrade to a system. Should anything bad happen, you have a nearly instance fall-back solution. Of course, snapshots are great tools to help with backups too.

---

### Post by indstrlmtlhd on 2021-04-03
A few things about using ZFS, you really need to use ECC memory to ensure the file system integrity due to the nature of how ZFS works; so the Epyc CPU will be perfect for this.
Don't bother using hardware RAID controllers but instead use HBA's since you need direct access to each drive that RAID controllers will typically not give you.

You might not want to use ZFS on the boot/OS drive right now but using ZFS RAID z1/z2/z3 on your data will be just fine.
Here's a quick start for implementing ZFS for a file server, this comes from me testing using ZFS on Ubuntu Server in VMWare on multiple VM's before using this info for deploying a ZFS based file server:

sudo apt -y install zfsutils-linux
ls /dev/disk/by-id/ata*
sudo zpool create -o ashift=12 -o autoexpand=on -o autoreplace=on -f shares raidz1 /dev/disk/by-id/ata-VMware_Virtual_SATA_Hard_Drive_01000000000000000001 /dev/disk/by-id/ata-VMware_Virtual_SATA_Hard_Drive_02000000000000000001 /dev/disk/by-id/ata-VMware_Virtual_SATA_Hard_Drive_03000000000000000001
zpool status
zfs list

Some notes:
This will create and mount the ZFS pool to /shares
"ashift=12" will force the use of 4k blocks, this is dependent on your hard drives.
"autoexpand=on" will resize your ZFS pool based on the smallest size drive in your system, for example if you eventually replace all your 4tb drives one at a time with 8tb then your ZFS pool will match the new size.
"autoreplace=on" by using disk id's this allows you to auto replace failed drives so much easier.


As always do more of your own research but hopefully this will help get you and others started.

BTW, once the server is online on your network, you can use ssh in Windows Powershell to remote in, including using these commands.

---

### Post by TheFu on 2021-04-03
ECC RAM is strongly recommended, but even without it, ZFS validates that what was sent to the storage was actually written to the storage.
[https://serverfault.com/questions/454736/non-ecc-memory-with-zfs-a-stupid-idea](https://serverfault.com/questions/454736/non-ecc-memory-with-zfs-a-stupid-idea)

The old-school recommendation that ECC RAM is mandatory isn't reality.  Lots of desktop users have been using ZFS on their non-ECC capable systems for years.  How is this any worse than using ext4 or xfs without ECC?

Of course, you'll still need solid, versioned, backups. That never stops.

---

