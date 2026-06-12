---
title: "multipath causes system to not boot, 10.04 server x86_64"
date: 2010-08-28
forum: Server Platforms
---

### Post by ghettofreeryder on 2010-08-28
I have an iscsi san that I am trying to get multipathing set up for.  It all seemed to work fine until I rebooted for the first time since installing the multipath-tools package.  It seems that on boot, multipathing and iscsi start before mounting the / partition, and that multipathing takes control of sda1, sda2, and sda5, causing the mount to fail.  Does anyone know how to prevent the multipath driver from doing this, or how to change the boot sequence to mount the /dev/mapper entry that multipath gives my sda partitions?

---

### Post by JMOUSE on 2012-05-13
Did you ever figure this out.. to get it to work with multipath?  For anyone who runs into a similar issue:  To get your system to boot again,  just go into grub (hold shift at boot)  and boot from an earlier kernel,  initramfs gets updated with a new kernel install and pulls info from /etc/multipath.conf

---

