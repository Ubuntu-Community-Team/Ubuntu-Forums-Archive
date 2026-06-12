---
title: "LVM Bug or Mistake?"
date: 2010-07-20
forum: Server Platforms
---

### Post by LepeKaname on 2010-07-20
I have this (working fine) setup (two twins disks in RAID 1) in VirtualBox:

```
/dev/md0: /boot 1GB  ext2 
/dev/md1: /     50GB ext4
/dev/md2: FREE SPACE (50GB)
```

I followed (just to add the LVM into the FREE SPACE) the guide posted here: 
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

```
1) pvcreate /dev/md2  (OK!)
2) vgcreate datavg /dev/md2 (OK!)
3) lvcreate --name datalv --size 30G datavg (OK!)
4) mkfs.ext3 /dev/datavg/datalv (OK!)
5) "df" command shows the virtual disk correctly.
6) added in "fstab": /dev/mapper/datavg-datalv /mnt/data ext3 rw,noatime 0 0
7) cat /proc/mdstat shows the sync process and finish without a problem.
```

Everything seems to work perfectly! however when I reboot, I got an error and fails to continue:

> /dev/md1: clean ...
/dev/md0: clean ...
mountall: fsck /boot [284] terminated with status 1.

So my question is, am I doing something wrong, or is a LVM bug?

**NOTE:** Tested in Ubuntu Server 10.04 (Lucid) 32 and 64bits.

---

### Post by richardjh on 2010-07-20
This appears to be a bug here are some relevant links

[B][https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/487744](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/487744)
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/582035](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/582035)
[http://ubuntuforums.org/showthread.php?t=1444639](http://ubuntuforums.org/showthread.php?t=1444639)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/454712](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/454712)

[/B]

---

### Post by LepeKaname on 2010-07-20
Thank you Richard (again) for pointing that. 

Hmm... so its a bug in fsck? I entered in recovery mode and I was able to mount it manually to /mnt/data and "df" states:

```
/dev/mapper/datavg-datalv ### ### ### 3% /mnt/data
```

which seems fine.

(### means some numbers that I'm too laze to copy them by hand :P)

I unmounted it and check it with fsck:
```

fsck /dev/mapper/datavg-datalv
/dev/mapper/datavg-datalv: clean 11/6656 files ###/### blocks
```

dmesg errors (recovery mode) show these messages for each partition, for example:
```

md: md0 stopped
md: bind<sdb1>
md: bind<sda1>
md0: detected capacity change from 0 to ###
md0: unknown partition table
```

(the same for md1 and md2).

Still no clue how to fix this problem :(

---

### Post by richardjh on 2010-07-21
I haven't investigated fully but I don't think there is a fix at this time. 

As reluctant as I am to say it, perhaps a reinstall is required.
If I were you I would chase this up on the bug reports to see if you can get any additional help there.

---

