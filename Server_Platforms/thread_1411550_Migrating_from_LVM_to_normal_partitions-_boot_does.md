---
title: "Migrating from LVM to normal partitions- boot does not complete"
date: 2010-02-20
forum: Server Platforms
---

### Post by ezacon on 2010-02-20
I have an Ubuntu 9.10/64 Server configured with LVM in a 1Tb sata disk in my home server.
For a simple server, LVM adds complexity if you need to recover your system, so i decided to migrate from LVM to normal partitions.
I have another 1Tb disk to copy my system disk.
In the backup disk, i have created same size partitions and trasfered files from /boot and root volumes with rsync, presenving perms etc... and excluding /dev /proc /sys etc...
I have then modified /etc/fstab to mount new UUID's and reinstaled grub via live CD and chroot.

At this point, when i replace my system disk with backup one, the boot process start as usual, but when it starts loading services the boot process does not continue.
The system is not "frozen". If i press intro, there is a line feed on screen
If i mount the backup disk in another system, there is nothing writed to /var/log/syslog or dmesg files during the boot process.
I can change terminal with <alt>F2 but there is no login.

In console, with backup disk i get:
```
....type 1505 audit.... operation="profile_load".....
.
.
Done.
Done.
fsck from util-linux-ng 2.16
/dev/sda1: clean ......
fsck from util-linux-ng 2.16
/dev/sda5: clean ......
 * Stopping remote control daemon(s): LIRC
 * Loading LIRC modules
 lircd-0.8.6[1057]: lircd(default) ready, using /var/run/lirc/litcd
 * could not access PID file for nmbd
 * could not access PID file for nmbd
```

And with original system disk:
```
....type 1505 audit.... operation="profile_load".....
.
.
Done.
Done.
 fsck from util-linux-ng 2.16
/dev/sda5: clean ......
fsck from util-linux-ng 2.16
 * Stopping remote control daemon(s): LIRC
 * Loading LIRC modules
 lircd-0.8.6[1057]: lircd(default) ready, using /var/run/lirc/litcd
/dev/mapper/coll-root: clean ......
 * could not access PID file for nmbd
 * Setting preliminary keumap...
 Ubuntu 9.10 coll tty1
 
 coll login:
```

---

### Post by ezacon on 2010-02-20
It is now working.
The problem was i was excluding /dev

---

