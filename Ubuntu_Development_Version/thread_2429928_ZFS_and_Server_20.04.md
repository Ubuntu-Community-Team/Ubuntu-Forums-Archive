---
title: "ZFS and Server 20.04"
date: 2019-10-25
forum: Ubuntu Development Version
---

### Post by cruzer001 on 2019-10-25
Seems I'm having my first let down.  ZFS does not appear to be available on the server (standard) installer.

---

### Post by PaulW2U on 2019-10-25
Quoting from [https://ubuntu.com/blog/enhancing-our-zfs-support-on-ubuntu-19-10-an-introduction](https://ubuntu.com/blog/enhancing-our-zfs-support-on-ubuntu-19-10-an-introduction)
> We want to support ZFS on root as an experimental installer option, initially for desktop, but keeping the layout extensible for server later on.

---

### Post by cruzer001 on 2019-10-25
Well nuts

I wonder if the mini.iso has ZFS support

---

### Post by mrfelker on 2019-10-28
I am using ZFS as my FS  chosen during the installation.    It is quite fast on my NVme SSD.   The one problem I have is that I can't figure out how to upgrade the kernel.

---

### Post by #&amp;thj^% on 2019-10-28
Define upgrade?
```
sudo apt update
sudo apt upgrade
```
should keep you current.
If your speaking of the mainline kernels: [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
You'll have to install those by hand.
EDIT: your kernel will stay as updated as your zfs allows it.
EDIT2:
```
zpool status && df -h /me1
  pool: me1
 state: ONLINE
  scan: none requested
config:

	NAME        STATE     READ WRITE CKSUM
	me1         ONLINE       0     0     0
	  sdb       ONLINE       0     0     0

errors: No known data errors
Filesystem      Size  Used Avail Use% Mounted on
me1              56G  128K   56G   1% /me1

```

---

### Post by mrfelker on 2019-11-02
Yes.   That is a significant problem.  Until it is solved I have to pass on this.

---

### Post by lammert-nijhof on 2019-11-09
I even had problems with ZFS during the HWE stack upgrade of 18.04. Upgrading to a not yet supported version of Linux is suicidal. ZFS on Linux latest supported kernel is Linux 5.3 for their release 0.8.2 and that is one version higher than the official version of Ubuntu. However many bugs solved in 0.8.2 have been integrated in the Ubuntu ZFS release 0.8.1.

---

