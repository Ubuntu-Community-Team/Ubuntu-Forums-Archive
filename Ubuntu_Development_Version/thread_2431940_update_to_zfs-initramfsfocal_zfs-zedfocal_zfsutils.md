---
title: "update to zfs-initramfs/focal zfs-zed/focal zfsutils-linux/focal but not modules?"
date: 2019-11-24
forum: Ubuntu Development Version
---

### Post by jidar on 2019-11-24
Ok so the following packages have upgrades:

```
zfs-initramfs/focal 0.8.2-3ubuntu1 amd64 [upgradable from: 0.8.1-1ubuntu17] 
zfs-zed/focal 0.8.2-3ubuntu1 amd64 [upgradable from: 0.8.1-1ubuntu17] 
zfsutils-linux/focal 0.8.2-3ubuntu1 amd64 [upgradable from: 0.8.1-1ubuntu17] 

```
and that's all fine and well, it's a update from 0.8.1 to 0.8.2, which is great! However:

```
$ modinfo zfs | head -5 
filename:       /lib/modules/5.3.0-18-generic/kernel/zfs/zfs.ko 
version:        0.8.1-1ubuntu12
```

The ZFS module itself, that's loaded by the kernel is version 0.8.1, and I don't see the package it belongs too being updated:

```
dpkg -S 5.3.0-18-generic/kernel/zfs/zfs.ko 
linux-modules-5.3.0-18-generic: /lib/modules/5.3.0-18-generic/kernel/zfs/zfs.ko

$ sudo apt list --upgradable | grep linux-modules 
 
WARNING: apt does not have a stable CLI interface. Use with caution in scripts. 
 
....
```

So umm, if the packages that control how to **talk** to zfs and the **utilities** are updated but the **kernel module isn't**, how in the world is that supposed to work?

Thanks!

---

### Post by kevdog on 2019-12-04
I believe the kernel needs to be compiled with the appropriate module.

---

