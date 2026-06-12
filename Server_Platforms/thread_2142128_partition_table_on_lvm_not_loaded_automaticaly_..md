---
title: "partition table on lvm not loaded automaticaly ."
date: 2013-05-04
forum: Server Platforms
---

### Post by ali abry on 2013-05-04
Hi
when ever i restart the Vm i should run partprobe , to system could find out that there is some partition on my lvm .
i have these partitions on my lvm 
```
# fdisk -l /dev/mapper/lvm--backup-backup--ubuntu--server 

Disk /dev/mapper/lvm--backup-backup--ubuntu--server: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25791a7c

                                         Device Boot      Start         End      Blocks   Id  System
/dev/mapper/lvm--backup-backup--ubuntu--server1            2048     3074047     1536000   83  Linux
/dev/mapper/lvm--backup-backup--ubuntu--server2         3074048     4194303      560128    5  Extended
/dev/mapper/lvm--backup-backup--ubuntu--server5         3076096     4194303      559104   83  Linux
```


before running partprobe :
```
# ls /dev/mapper/
control                             ubuntu--server-root-real             ubuntu--server-ubuntu--root--snappy-cow
lvm--backup-backup--ubuntu--server  ubuntu--server-swap_1
ubuntu--server-root                 ubuntu--server-ubuntu--root--snappy

```

after running partprobe :
```
# partprobe
root@ubuntu-server:/# ls /dev/mapper/
control                              lvm--backup-backup--ubuntu--server5  ubuntu--server-ubuntu--root--snappy
lvm--backup-backup--ubuntu--server   ubuntu--server-root                  ubuntu--server-ubuntu--root--snappy-cow
lvm--backup-backup--ubuntu--server1  ubuntu--server-root-real
lvm--backup-backup--ubuntu--server2  ubuntu--server-swap_1

```

---

### Post by darkod on 2013-05-04
I haven't used partprobe, but if the LVM is not automatically activated, have you tried once to activate it by hand and update the initramfs?
```
sudo vgchange -ay
sudo update-initramfs -u
```

See if that helps.

---

### Post by ali abry on 2013-05-04
thanks for reply.
nothing changed . steel it doesn't find partitions by it self .

---

