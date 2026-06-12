---
title: "Karmic 'minimal virtual server' does not support NFS"
date: 2010-02-02
forum: Server Platforms
---

### Post by rhael on 2010-02-02
Hi guys

I had a problem of not being able to make an nfs mount on my virtual servers that i installed with 9.10. All similar servers running on 9.04 were working fine. The problem turned out to be the fact that the generic-pae kernel does not have nfs support on board. The simplest solution i could find out was to switch the kernel. Here's how

In most cases, you might end up with this:

```
root@thebe:/# mount myhost:/myfolder /mymount
mount.nfs: No such device
```

In my case, this problem was caused by the fact that i was running a kernel without nfs support. You can check it with this command:

```
root@thebe:/# modprobe nfs
FATAL: Module nfs not found.
```

Solution is to install the module, or easier, install a kernel that has the module. I chose the 'server' flavour of my kernel:

```
root@thebe:/# apt-get install linux-image-generic
```

Next, look in /boot/grub/grub.cfg and find your kernel. Edit /etc/default/grub and set the value GRUB_DEFAULT to the id of your kernel in grub.cfg (0 being the first, 1 the second, etc)

Reboot and try modprobe nfs again, you should be able to use nfs now

---

