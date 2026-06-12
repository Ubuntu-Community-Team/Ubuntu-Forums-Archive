---
title: "i forgot to addd my array to Mdadm.conf"
date: 2020-10-21
forum: Server Platforms
---

### Post by gimpacause on 2020-10-21
hi all i set up a new array @ /dev/md1
got it all synced and started copying data, it was only then that i realized i forgot to add the array to mdadm.conf, so now the array is showing up as /dev/d127

```
ben@themachine:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md127 : active raid6 sdb1[0] sdd1[1] sdj1[4] sdf1[2] sdac1[14] sdh1[3] sdy1[12] sdaa1[13] sdu1[10] sds1[9] sdw1[11] sdp1[8] sdn1[7] sdk1[5] sdm1[6]
      228516527616 blocks super 1.2 level 6, 512k chunk, algorithm 2 [15/15] [UUUUUUUUUUUUUUU]
      bitmap: 1/131 pages [4KB], 65536KB chunk


md0 : active raid6 sdg[4] sde[10] sdi[13] sda[5] sdc[1] sdad[2] sdab[6] sdz[14] sdx[8] sdv[11] sdt[0] sdr[3] sdq[7] sdo[9] sdl[12]
      76185088512 blocks super 1.2 level 6, 512k chunk, algorithm 2 [15/15] [UUUUUUUUUUUUUUU]
      bitmap: 0/44 pages [0KB], 65536KB chunk

```


my contents of mdadm.conf are as follows

```
ben@themachine:~$ cat /etc/mdadm/mdadm.conf
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


# This configuration was auto-generated on Thu, 06 Aug 2020 22:39:44 +0000 by mk                                                                                                                                                             conf
ARRAY /dev/md0  metadata=1.2 UUID=0a62c2c5:6ca30a41:e6f132f9:11bef5db name=ubunt                                                                                                                                                             u:0
ben@themachine:~$

```

contents of fstab

```
ben@themachine:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-Bcc2NhfpG9RXkblowtjhfZffTA6FmsrrVdbGJOMcvCS6bZV730w8p8c2aoTMZznl / ext4 defaults 0 0
# /boot was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/2bdc9ea0-4cbf-4b2a-a065-0fa6562071e9 /boot ext4 defaults 0 0
/swap.img       none    swap    sw      0       0
/dev/data0/lvm0 /mnt/files xfs auto,rw 0 0
/dev/data1/lvm1 /mnt/media xfs auto,rw 0 0
ben@themachine:~$





```

df -h results

```
ben@themachine:~$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                                16G     0   16G   0% /dev
tmpfs                              3.2G   13M  3.2G   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   55G   42G   11G  81% /
tmpfs                               16G   20K   16G   1% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                               16G     0   16G   0% /sys/fs/cgroup
/dev/sdae2                         976M  145M  765M  16% /boot
/dev/mapper/data0-lvm0              71T   71T  768G  99% /mnt/files
/dev/mapper/data1-lvm1             213T   58T  155T  28% /mnt/media
tmpfs                              3.2G     0  3.2G   0% /run/user/1000
/dev/loop0                          31M   31M     0 100% /snap/snapd/9607
/dev/loop1                          56M   56M     0 100% /snap/core18/1885
/dev/loop2                          31M   31M     0 100% /snap/snapd/9721
ben@themachine:~$

```

once the curernt transfer is complete

can i stop /dev/md127

add the array to my mdadm.conf , update initramfs and reboot, should everything be ok, or will the arrays start a re-sync??

thank you for your help, Ben

---

### Post by darkod on 2020-10-21
You don't need to stop it and it won't start a resync.

Just edit the mdadm.conf and add a new ARRAY line for md1 and adjust the UUID to use the correct one.

You don't need the name= parameter. And the metadata= is also not necessary but you can leave it.

After reboot the array should assemble as md1. I think the update-initramfs should be done after, when it is already assembled as md1.

---

### Post by gimpacause on 2020-10-21
Thank you Once again for your help darkod

That worked perfectly , I think the mistake I made was as you said, I should of waited to run update initramfs after array was set to md1,

Again many thanks

---

### Post by darkod on 2020-10-22
No problem.

Please mark the thread as SOLVED. You can do that in Thread Tools above the first post, on the right.

---

