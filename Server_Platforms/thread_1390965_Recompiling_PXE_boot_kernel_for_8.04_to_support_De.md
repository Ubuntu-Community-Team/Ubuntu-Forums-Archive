---
title: "Recompiling PXE boot kernel for 8.04 to support Dell PE R410"
date: 2010-01-26
forum: Server Platforms
---

### Post by rsv on 2010-01-26
Hello 

I have a problem pxe installing Dell PE R410 serverv, this is due to the bnx2 driver:
[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/435185/comments/5](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/435185/comments/5)

I can pxeboot the server but when the installer tries to detect the network interface it fails.

So i would like to change my pxeboot kernel and update the bnx2.c so it supports the new hardware.

I have these files on my pxebootserver:
 /var/lib/tftpboot/ubuntu/hardy/amd64/
boot-screens  initrd.gz  linux  pxelinux.0  pxelinux.cfg  pxelinux.cfg.serial-9600

How can i modify and then recompile the linux pxeboot kernel ?

I hope this makes sense to someone ;-)

Thanks

---

