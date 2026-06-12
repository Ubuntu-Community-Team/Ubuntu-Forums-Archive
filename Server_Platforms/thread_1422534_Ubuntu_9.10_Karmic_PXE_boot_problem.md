---
title: "Ubuntu 9.10 Karmic PXE boot problem"
date: 2010-03-05
forum: Server Platforms
---

### Post by sarcoma on 2010-03-05
Hello

I am trying to make a distribution for diskless station based on Ubuntu 9.10 Karmic.
I read this documentation [http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless](http://developer.novell.com/wiki/index.php/HOWTO:_Convert_Ubuntu_to_Diskless)

I had already working PXE server, so I just moved the whole installed system from HDD to PXE-server into the nfs-shared directory.

Everythig was fine but when I tried to boot from PXE the system got frozen with this message (see screenshot) after the kernel loaded:

mount.nfs: remote share not in 'host:dir' format
mountall: mount / [1386] terminated with status 32

[IMG]http://img171.imageshack.us/img171/254/27326031.png[/IMG]


What's the reason of that could it be?

---

### Post by sarcoma on 2010-03-09
any ideas?

---

### Post by romut on 2010-04-20
you got two options to specify the root for your netbooted system

1) in /etc/initramfs-tools/initramfs.conf where you changed the system flavour to BOOT=nfs add a NFSROOT=10.0.0.1:/tftpboot/nfsroot
And don't forget to run update-initramfs -u

2) on the kernel command line in the default file.
append ro initrd=nfsroot/initrd.img root=/dev/nfs ip=dhcp nfsroot=10.0.0.1:/tftpboot/nfsroot/

---

### Post by romut on 2010-04-20
sorry I forgot something. There is a third place to look at

3) /etc/fstab

in case of /dev/nfs not working

10.0.0.1:/tftboot/nfsroot  /   nolooks,ro 0 0

is the better choice

(and 10.0.0.1:/tftpboot/nfsroot is only an example)

---

### Post by romut on 2010-04-20
And there was a bug in the /sbin/mountall in karmic they got finally fixed in lucid, but in karmic I only got the system up and running with this fix:


```
mv /sbin/mountall /sbin/mountall.bin

echo '#!/bin/bash' > /sbin/mountall
echo '/bin/mount -o remount,ro /' >> /sbin/mountall
echo "/sbin/mountall.bin '\$@'" >> /sbin/mountall

chmod a+x /sbin/mountall
```

---

