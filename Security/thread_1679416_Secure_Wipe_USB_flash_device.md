---
title: "Secure Wipe USB flash device"
date: 2011-02-01
forum: Security
---

### Post by twzg on 2011-02-01
Hi. I tried to do 'srm', 'wipe', 'shred'... whatever terminal commands to securely wipe a '/dev/sdc' (USB flash device) but it says that the device is read-only. How should I go about securely wiping it ?

---

### Post by HermanAB on 2011-02-01
Hmm, a flash device doesn't need a 'secure wipe'.  Just overwrite it with zeroes:

Assuming that you have only one disk drive and the flash device is /dev/sdb, with a single partition called sdb1:
$ sudo umount -l /dev/sdb1

$ sudo dd if=/dev/zero of=/dev/sdb1


Thereafter, you need to format it again:
$ sudo fdisk /dev/sdb
n
p
1
enter
enter
w

$ sudo mkfs.vfat /dev/sdb1

---

### Post by bodhi.zazen on 2011-02-01
The "Gutmann theory" has been debunked :

[http://www.springerlink.com/content/408263ql11460147/](http://www.springerlink.com/content/408263ql11460147/)

One pass with dd is sufficient, additional writes / passes simply puts excessive wear on the drive or flash device.

---

