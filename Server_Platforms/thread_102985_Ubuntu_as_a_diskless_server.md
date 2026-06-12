---
title: "Ubuntu as a diskless server?"
date: 2005-12-13
forum: Server Platforms
---

### Post by Legenda on 2005-12-13
I'm trying to make Ubuntu boot from an nfsroot. I have a working 2.6 kernel with UnionFS support and initramfs image for it. I have previously used it to boot Debian Etch succesfully. Now I would like to try booting into an nfsroot with Ubuntu Breezy.

I have now bumped into a problem: It seems Ubuntu's ifupdown shuts down an ethernet interface before starting it. This causes a big problem for me, because I need to configure the server's ethernet interface in the initramfs stage with dhcpcd. Then I mount the nfsroot via that interface. After this, the interface must not shut down at any stage, otherwise the system will crash as the rootfs is lost.

Is there any way to prevent ifupdown from shutting down the ethernet interfaces before attempting to bring them up?

---

### Post by eudoxos on 2006-01-04
Hi,

I would like to deploy the NFS+unionfs scenario but what made me not do it yet is the necessity of going into initram and scripting in there. Could you post here some (overall) HOWTO how to proceed? Or even some config files? Before I go ahead... 

Thanks - VS

---

### Post by nagilum on 2006-01-08
Since you already configured the interface in the initrd there is no need to let Ubuntu do so again. Disabling the configuration of that particular device in /etc/network/interfaces (of your real root fs) should solve your problem.

---

