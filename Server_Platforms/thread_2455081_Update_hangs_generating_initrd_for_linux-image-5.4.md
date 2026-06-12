---
title: "Update hangs generating initrd for linux-image-5.4.0-54-generic (5.4.0-54.60)"
date: 2020-12-11
forum: Server Platforms
---

### Post by mike-1169 on 2020-12-11
Hi all,

I've just installed Ubuntu 20.04.1 LTS on a VM and performed an upgrade.

The upgrade process was running fine until it was generating the new initrd:

```
root@dm:~# dpkg --configure -a
Setting up linux-image-5.4.0-54-generic (5.4.0-54.60) ...
Processing triggers for initramfs-tools (0.136ubuntu6.3) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-53-generic

```

I left the upgrade process to run overnight, but it wasn't moving when I checked on it in the morning (around 10+ hours).  I killed the upgrade process and re-ran dpkg --configure -a.  

Anyone knows what could be the issue?



Thanks.

---

### Post by TheFu on 2020-12-12
Out of storage in /boot/ or inodes is the first thing to check.

I patched this morning and saw one of the kernel updates get stuff for about 3 minutes in the same place, but it finished. After that, I went through all my systems and cleared out old kernels.

BTW, 5.4.0-54 is a few weeks old. On 20.04, vmlinuz-5.4.0-56-generic  vmlinuz-5.4.0-58-generic are current. I don't have -54 on my systems anymore.

---

