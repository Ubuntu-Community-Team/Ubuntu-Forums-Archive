---
title: "PXE Boot: tftp, ftp or http?"
date: 2010-07-28
forum: Server Platforms
---

### Post by xzased on 2010-07-28
Hi. Im having a problem with our pxe environment. We have around 200 clients per server to boot from tftp and when we hit 250 the service just freezes. So, our options are to either add more servers or move to a more robust protocol. Is this feasible?? How can clients boot from ftp? Thanks

---

### Post by chopinhauer on 2010-07-29
You can also switch to a more robust TFTP server, there is quite a bunch of them out there.

The PXE environment contains only a TFTP client, but after the first part of the boot process you can fall back on an NFS server.

---

### Post by xzased on 2010-07-29
Thanks for your response Chopinhauer. Thats exactly the route we want to take. Could you provide some pointers on how to do this?

EDIT:
I stumble upon [THIS]("http://wiki.robotz.com/index.php/PXE_Boot_Server_Configuration_Using_Linux") guide. I plan to use PXE + Samba to install win-pe images. But I would like some feeback from someone who has done this before. Thanks

---

### Post by chopinhauer on 2010-07-30
> **xzased said:**
> Could you provide some pointers on how to do this?

PXELINUX works just as Grub, but through a network environment. You have can find a guide on how to boot a machine with an NFS root filesystem on [Digital Peer](http://www.digitalpeer.com/id/linuxnfs). Otherwise the [PXELINUX Documentation](http://syslinux.zytor.com/wiki/index.php/PXELINUX) allows you to fill the blanks.

---

