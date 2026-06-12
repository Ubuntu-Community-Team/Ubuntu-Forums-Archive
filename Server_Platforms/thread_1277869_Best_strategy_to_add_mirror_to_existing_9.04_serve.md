---
title: "Best strategy to add mirror to existing 9.04 server boot drive"
date: 2009-09-28
forum: Server Platforms
---

### Post by atconc on 2009-09-28
Hi

I recently installed Ubuntu server that boots and runs from an 8gb USB flah drive (as I have 6 SATA drives in 2 RAID 5 arrays and therefore no free drive bays!) I installed from the alternate CD with just the flash drive connected and accepted the default options, which used LVM (which I don't really have a good handle on to be honest). Everything is working great but I have some concerns about durability using the flash drive as the boot and root drive, so I would like to add a second 8gb drive as a RAID 1 mirror to this system.

Could anyone suggest what the most graceful way to do this would be? Can I do it without reinstalling the O/S or do I need to backup and repartition the drives?

I've spent a fair amount of time configuring the box and would like to avoid loosing my configuration and would also appreciate some guidance on what to back up to be able to recover my boot drive / OS / services as I realise RAID is no substitute for actual backups too.

Thanks in advance for any help offered

Here's the output of mount:
```
/dev/mapper/triad-root on / type ext3 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-server/volatile type tmpfs (rw,mode=755)
/dev/sdg5 on /boot type ext2 (rw,noatime)
tmpfs on /tmp type tmpfs (rw)
tmpfs on /var/tmp type tmpfs (rw)
tmpfs on /var/lock type tmpfs (rw)
/dev/md0 on /media/raid type ext3 (rw,noatime,nodiratime)
/dev/md1 on /media/tera type ext3 (rw,noatime,nodiratime)
securityfs on /sys/kernel/security type securityfs (rw)
```

Here's the fstab

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/triad-root during installation
UUID=e2365fb7-1387-4e1d-871a-5b50e9b5a12c /               ext3    defaults,noatime,errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=621f0028-1a29-4bf4-aab6-64a76432b593 /boot           ext2    noatime        0       2
# swap was on /dev/mapper/triad-swap_1 during installation
UUID=bb83765e-1c66-4b55-993a-5aac5be8e372 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
tmpfs           /tmp            tmpfs   defaults                0       0
tmpfs           /var/tmp        tmpfs   defaults                0       0
tmpfs           /var/lock       tmpfs   defaults                0       0
#tmpfs          /var/log        tmpfs   defaults                0       0
/dev/md0        /media/raid     auto    noatime,nodiratime      0       1
/dev/md1        /media/tera     auto    noatime,nodiratime      0       1

```

and fdisk details for the usb drive

```
sudo fdisk -l /dev/sdg

Disk /dev/sdg: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d51719e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1         944     7582648+  8e  Linux LVM
/dev/sdg2             945         974      240975    5  Extended
/dev/sdg5             945         974      240943+  83  Linux

```

---

