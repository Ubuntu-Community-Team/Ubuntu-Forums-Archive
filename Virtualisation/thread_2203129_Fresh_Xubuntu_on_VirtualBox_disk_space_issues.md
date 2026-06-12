---
title: "Fresh Xubuntu on VirtualBox disk space issues"
date: 2014-02-01
forum: Virtualisation
---

### Post by synek on 2014-02-01
I've just created VM with 8GB disk space and 4GB RAM and installed there xubuntu. I've ran out of space very fast, after downloading ~200 MB. df -h says:
```

Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root  3,7G  3,5G  736K 100% /
none                          4,0K     0  4,0K   0% /sys/fs/cgroup
udev                          2,0G  4,0K  2,0G   1% /dev
tmpfs                         404M  852K  404M   1% /run
none                          5,0M     0  5,0M   0% /run/lock
none                          2,0G   80K  2,0G   1% /run/shm
none                          100M   24K  100M   1% /run/user
/dev/sda1                     236M   68M  156M  31% /boot

```
I've read here and there that /run/shm doesn't use disk space, but if I sum up 3.5G (/) + 2G (/dev) + 2G (/run/shm) + others, it makes smthg about 8G. What is more, virtual box says the disk usage is about 3.9GB.
I cannot resize any partitions, gparted says everything full (/dev/sda5 ~7.5GB, all in use).

My host machine uses small ssd disk so I would like to stick with that 8GB virtual disk. Is it achievable?

---

### Post by TheFu on 2014-02-02
Only sda1 and the LVM are actually using disk storage. The other things in that list are virtual file system .. in RAM.
Post the output of **sudo parted -l**. Please use the "Adv Reply" and "code" tags so things line up.

I wouldn't bother with LVM inside a clientOS. Not worth the hassle there - definitely use it on the hostOS for the flexibility but not in clients.

Allocating 4G of RAM seems excessive. 1-2G is fine almost always.  Over allocation of CPU, RAM, and other resources doesn't help the VM.

---

