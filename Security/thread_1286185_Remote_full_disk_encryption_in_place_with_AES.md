---
title: "Remote full disk encryption in place with AES"
date: 2009-10-08
forum: Security
---

### Post by Bilg on 2009-10-08
I have a dedicated server running Ubuntu 8.04 LTS (hardy) at a remote location to which I do not have physical access. I can only perform a remote install so encryption has to come after installation, not prior. I have partitioned the disk as follows:

```
/dev/sda1       /boot   ext3    errors=remount-ro       0       1
/dev/sda2       /       ext3    errors=remount-ro       0       1
/dev/sda3       swap    swap    defaults        0       0
/dev/sda4       /home   ext3    defaults        1       2
```Excluding the boot partition (sda1), I wish to encrypt sda2 and sda4 in-place without modifying the data, and sda3, with AES. What is the best way to accomplish this?

Later, I will need to be able to boot the system using an SSH server embedded into initrd to boot the encrypted filesystem, but I guess I might have to make a separate thread about that problem.

---

### Post by HermanAB on 2009-10-09
Just encrypt your data, e.g. /home.  Encrypting the whole system is mostly useless, for various reasons and it makes the machine slightly slower.  

Here are some LUKS wizards that you can use or pull apart to see how it works: [http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by Bilg on 2009-10-09
I am looking to achieve full disk encryption, so not doing full disk encryption is not a solution.

It might help to note that I can do a net boot using a selection of precompiled kernels, a rescue mode boot in which a rescue filesystem is root mounted in RAM and a vKVM boot which allows me to view the boot process. However, all of these options besides vKVM will boot a kernel precompiled by the host which are all non-modular and do not support encryption so they may all be useless anyway.

---

