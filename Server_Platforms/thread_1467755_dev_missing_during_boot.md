---
title: "/dev missing during boot"
date: 2010-05-01
forum: Server Platforms
---

### Post by ian dobson on 2010-05-01
Hi All,

I've just updated my backend server to 10.04 and am having problems. When I try and boot 10.04 I end up at the recovery prompt, the system displays an error message about not being able to change directory then drops to the recovery prompt. If I go to single user mode (in 10.04) everything seems to be OK.

If I boot the old kernel (9.10) the system displays an error about /dev missing but after afew seconds it appears to boot and all my filesystems are mounted/services started.

So it looks as if the boot system/scripts are looking for /dev before it's actually available.

System information:-
Quad Core with 8Gb ram
6 2Tb WD harddisks (3 Raid partitions - md0 / RAID mirror, md1 data RAID5,md2 backup)

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>  <type>      <options>                                                    <dump>  <pass>
proc            /proc          proc        defaults                                                       0       0
/dev/md0        /              ext3        defaults,noatime,nodiratime,data=writeback                     0       1  ##Root device
/dev/scd0       /media/cdrom0  udf,iso9660 user,noauto                                                    0       0
/dev/fd0        /media/floppy0 auto        rw,user,noauto                                                 0       0
/dev/md1        /data          ext4        rw,noatime,nodiratime,data=writeback,nobh,barrier=0,commit=15  0       0  ##RAID 5 array

```

Any ideas what the problem is? This box has been running in the hardware configuration for over a year now, apart from ubuntu 10.04.

If you need any further information let me know.

Regards
Ian Dobson

---

### Post by ian dobson on 2010-05-01
Hi All,

Problem found, mount_all/mount in 9.10 accepted that there was an error in my fstab but 10.04 they died instead of ignoring the error.

I think mount/ext3 fs in 10.04 doesn't like the option data=writeback.

Regards
Ian Dobson

---

