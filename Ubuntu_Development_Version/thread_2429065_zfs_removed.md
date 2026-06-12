---
title: "zfs removed?"
date: 2019-10-13
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-10-13
Today update removed all zfs?```
The following packages were automatically installed and are no longer required:
  libnvpair1linux libuutil1linux libzfs2linux libzpool2linux zfs-initramfs zfs-zed zfsutils-linux
Use 'sudo apt autoremove' to remove them.
```

```
corrado@corrado-p6-ee-1006:~$ apt list --installed | grep -i zfs
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
corrado@corrado-p6-ee-1006:~$ 
```

---

### Post by PaulW2U on 2019-10-13
For new installs, zfs is only installed if it is selected during the installation process.

---

### Post by kansasnoob on 2019-10-13
I probably won't have time to test ZFS so can't be sure but I noticed someone filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1847927](https://bugs.launchpad.net/ubuntu/+source/zfs-linux/+bug/1847927)

It sounds like they had installed using ZFS but it was still removed on update. I haven't checked the logs attached to the report to verify that though.

---

