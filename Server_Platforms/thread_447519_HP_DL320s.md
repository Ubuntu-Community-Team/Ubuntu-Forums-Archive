---
title: "HP DL320s"
date: 2007-05-18
forum: Server Platforms
---

### Post by mjrobertshaw on 2007-05-18
Hi There

We have purchased an HP DL320s Storage Server and were hoping to get Ubuntu Server (Any version) up and running.  We have a P400 SATA Controller with a 3TB array over 6 disks.  The installation succeeds for Ubuntu version 7.0.4. when using LVM with 3 partitons (/boot, /swap, /) but upon reboot we get a kernel panic (not syncing) where it appears that the kernel cannot read anything from /root

Does anybody know what might be going on?  Do we need to recompile the kernel with specific raid drivers?

Thanks in advance

Mark Robertshaw (Oxford Information Labs)

---

### Post by craigp84 on 2007-05-18
It sounds like one of those enumeration type issues.

Show us your /etc/fstab - up until feisty, ubuntu was really braindead about how it listed disks in /etc/fstab. No worries though, that's a quick fix :)

Show us your /boot/grub/menu.lst

Paste in output of a "dmesg".

You can get all of these by following these instructions (i know you can't boot properly right now):

```
Boot off the install CD, get as far as the "configure your network interfaces" bit - but don't go any further. Then ALT+F2 onto the console, then do:

mount -o bind /proc /target/proc
mount -o bind /dev /target/dev
chroot /target /bin/bash
mount -a # mounts any other partitions such as /var etc. if you've set it up that way
```

---

