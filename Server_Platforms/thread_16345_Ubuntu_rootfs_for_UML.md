---
title: "Ubuntu rootfs for UML?"
date: 2005-02-20
forum: Server Platforms
---

### Post by nhoxanh on 2005-02-20
hello,

I am planning to run UserModeLinux on my hosting server, and run Ubuntu on it. Could anybody point me where to get the Ubutu rootfs for UML? I saw some rootfs available on UML homepage, but there is no Ubuntu.

Thank you a lot.
nhoxanh

---

### Post by alfmatos on 2005-09-11
# ubuntu rootfs



dd if=/dev/zero of=rootfs.hoary bs=1M seek=5000 count=0
(5 GB, change the seek value for your own preference)

mkreiserfs rootfs.hoary -f
(use your prefered fs, like mkfs.ext3 rootfs.hoary)

mkdir tmp

sudo mount -o loop rootfs.hoary tmp/

sudo debootstrap hoary tmp file:///media/cdrom0/dists/hoary/

(this is from the cd, run without the file: part to get it from the web)

---

