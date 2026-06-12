---
title: "easy fix bug between virt-builder in libguestfs-tools and linux kernel package."
date: 2014-05-21
forum: Virtualisation
---

### Post by pixelfairy2 on 2014-05-21
Using 14.04 amd64

supermin, part of libguestfs uses the host kernel and looks for it in /boot/vmlinuz... but, the kernel is readable only by root. in the mean time, if virt-builder give you this,

 ```
:~$ virt-builder ubuntu-14.04 -o testbuild.img
[   0.0] Downloading: http://libguestfs.org/download/builder/ubuntu-14.04.xz
[   2.0] Creating disk image: testbuild.img
[   2.0] Uncompressing: http://libguestfs.org/download/builder/ubuntu-14.04.xz
^Cvirt-builder: error: failed to uncompress template
pixel@hivecluster:~$ script
Script started, file is typescript
pixel@hivecluster:~$ virt-builder ubuntu-14.04 -o testbuild.img
[   0.0] Downloading: http://libguestfs.org/download/builder/ubuntu-14.04.xz
[   2.0] Creating disk image: testbuild.img
[   2.0] Uncompressing: http://libguestfs.org/download/builder/ubuntu-14.04.xz
[  36.0] Running virt-resize to expand the disk to 4.2G
Fatal error: exception Guestfs.Error("/usr/bin/supermin-helper exited with error status 1.
To see full error messages you may need to enable debugging.
See http://libguestfs.org/guestfs-faq.1.html#debugging-libguestfs")
virt-builder: error: virt-resize failed

```

just do this to fix it.
```
sudo chmod +r /boot/vmlinuz-`uname -r`
```

Dont know if they intended only root to read the kernel, but ill bug them about it anyway

---

### Post by rjones-redhat on 2014-05-22
FYI there is an open Ubuntu bug about this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/759725](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/759725)

---

