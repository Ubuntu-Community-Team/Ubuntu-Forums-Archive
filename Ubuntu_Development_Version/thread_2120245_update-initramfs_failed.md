---
title: "update-initramfs failed"
date: 2013-02-26
forum: Ubuntu Development Version
---

### Post by lucazade on 2013-02-26
```
$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.8.0-7-generic
modprobe: ../tools/modprobe.c:550: print_action: Assertion `kmod_module_get_initstate(m) == KMOD_MODULE_BUILTIN' failed.
Aborted
```

Known issue?!

---

### Post by dino99 on 2013-02-26
Long list 

[https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062](https://bugs.launchpad.net/ubuntu/+source/kmod/+bug/1073062)

---

### Post by lucazade on 2013-02-26
thanks Dino
subscribed!

---

