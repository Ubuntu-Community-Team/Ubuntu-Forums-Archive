---
title: "Ltsp problem"
date: 2008-06-12
forum: Server Platforms
---

### Post by SonicBr on 2008-06-12
I need help my ltsp stop here !!!!

address: 192.168.0.2 broadcast: 192.168.0.255 netmask: 255.255.255.0
gateway 192.168.0.1 dns0: 192.168.0.1 dns1: 0.0.0.0
host: ws001
rootserver: 192.168.0.1 rootpath:192.168.0.1:/opt/ltsp/i386
filename: /ltsp/i386/nbi.img
Begin: Running /scripts/nfs-premount ...
Done.

Done.
Begin: Running /scripts/nfs-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doen't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-4)Built-in shell (ash)
Enter "help" for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by AlexanderDGreat on 2009-09-22
Hi, this happened to me before. Make sure there's only 1 dhcp server running.

---

