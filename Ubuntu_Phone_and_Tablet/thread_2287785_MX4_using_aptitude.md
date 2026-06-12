---
title: "MX4 using aptitude"
date: 2015-07-22
forum: Ubuntu Phone and Tablet
---

### Post by constantin.karl.mu on 2015-07-22
Hi,

I am generally very happy with my MX4 ubuntu phone, but in order to increase the functionality tremendously I want to use aptitude in the same way I use it on my laptop.
After ```
sudo mount -o remount,rw /
``` I managed to run ```
sudo apt-get update
``` etc. however soon the terminal threw
```

Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: Can't mmap an empty file
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
```
I checked with df
```

Filesystem                      1K-blocks    Used Available Use% Mounted on
/dev/disk/by-partlabel/system     2046272 2029876         0 100% /
udev                               966528       4    966524   1% /dev
tmpfs                              193796     552    193244   1% /run
/dev/disk/by-partlabel/userdata  12112568  267924  11206308   3% /home
/dev/loop0                         173136  172008         0 100% /etc/gps.conf
none                                    4       0         4   0% /android
tmpfs                              968968       4    968964   1% /etc/fstab
tmpfs                              968968    1388    967580   1% /var/lib/lxc/android/rootfs
/dev/disk/by-partlabel/cache       693152    6156    636536   1% /android/cache
none                                    4       0         4   0% /sys/fs/cgroup
cgmfs                                 100       0       100   0% /run/cgmanager/fs
tmpfs                              968968      56    968912   1% /tmp
none                                 5120       0      5120   0% /run/lock
none                               968968  367096    601872  38% /run/shm
none                               102400       0    102400   0% /run/user
tmpfs                              968968       0    968968   0% /media
tmpfs                              968968       4    968964   1% /var/lib/sudo
tmpfs                              193796      44    193752   1% /run/user/32011
tmpfs                              193796       0    193796   0% /run/user/0
```
only to find out that the root filesystem is full. I tried resizing with ```
resize2fs
``` but the partition size is only 2GB which is silly considering I have 12GB spare memory.
I suppose the partition size can't be increased while the phone is turned on so the only option I see is through the recovery mode that I can start by booting holding Power + VolUp but nothing happens; adb just says "offline" and all I see on my phone is the Ubuntu logo.

Sooo my question is, is there a possibility to change partition sizes or any other way to use aptitude for that matter?

Cheers :)

---

### Post by constantin.karl.mu on 2015-07-23
I managed to use adb in recovery mode by flashing a different recovery.img.
Still, most likely it is a very bad idea.
Has anyone got any experience with resizing phone partitions?

---

