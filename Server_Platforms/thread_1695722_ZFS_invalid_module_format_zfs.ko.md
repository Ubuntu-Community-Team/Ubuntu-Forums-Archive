---
title: "ZFS invalid module format zfs.ko"
date: 2011-02-26
forum: Server Platforms
---

### Post by inckiekage on 2011-02-26
I have compiled and installed the ZFS modules from [http://zfsonlinux.org/](http://zfsonlinux.org/) using their .deb guide.

i got my pool up and running, and everything was fine, also after reboot.

but here the other day i had to power off the machine


when i booted up the machine, it couldn't mount my zpool

and i tried to execute the zpool status command, here is the output:

```
kimse@matilde:~$ sudo zpool status
[sudo] password for kimse: 
Failed to load ZFS module stack.
Load the module manually by running 'insmod <location>/zfs.ko' as root.
kimse@matilde:~$ locate zfs.ko
/lib/modules/2.6.35-22-server/addon/zfs/zfs/zfs.ko
kimse@matilde:~$ sudo insmod /lib/modules/2.6.35-22-server/addon/zfs/zfs/zfs.ko
insmod: error inserting '/lib/modules/2.6.35-22-server/addon/zfs/zfs/zfs.ko': -1 Invalid module format
```

---

### Post by inckiekage on 2011-02-26
Solved - Booted wrong kernel.

---

