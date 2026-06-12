---
title: "Dhcp3-server fails to start: Can't open /etc/dhcp3/dhcpd.conf: Permission denied"
date: 2010-10-01
forum: Server Platforms
---

### Post by regneva on 2010-10-01
I installed dhcpd using 

```
apt-get install dhcp3-server
```

Now when I try to run it, I get this weird error:

```

root@TonidoPlug:/etc# /etc/init.d/dhcp3-server start
dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Can't open /etc/dhcp3/dhcpd.conf: Permission denied

```

I changed permissions to 777:

```
root@TonidoPlug:/etc# ls -al dhcp3
total 12
drwxrwxrwx  2 root root 4096 2010-10-01 07:43 .
drwxr-xr-x 79 root root 4096 2010-10-01 07:43 ..
-rwxrwxrwx  1 root root 3662 2009-03-31 18:34 dhcpd.conf

```

To no avail!

Google tells me it's got something to do with AppArmor.

I don't think it is installed on this system:

```
root@TonidoPlug:/etc# ls /etc/init.d/a*
ls: cannot access /etc/init.d/a*: No such file or directory
root@TonidoPlug:/etc# ls /etc/init.d/apparmor.d
ls: cannot access /etc/init.d/apparmor.d: No such file or directory
root@TonidoPlug:/etc# ls /etc/init.d/
bootlogd               cron              glibc.sh         killprocs              mountdevsubfs.sh       networking  reboot     skeleton              udev          ushare
bootmisc.sh            cryptdisks        halt             klogd                  mountkernfs.sh         procps      rmnologin  ssh                   udev-finish   x11-common
checkfs.sh             cryptdisks-early  hostname.sh      loopback               mountnfs-bootclean.sh  rc          rsync      stop-bootlogd         umountfs
checkroot.sh           dbus              hwclockfirst.sh  module-init-tools      mountnfs.sh            rc.local    samba      stop-bootlogd-single  umountnfs.sh
console-screen.kbd.sh  ddclient          hwclock.sh       mountall-bootclean.sh  mountoverflowtmp       rcS         sendsigs   sysklogd              umountroot
console-setup          dhcp3-server      keyboard-setup   mountall.sh            mtab.sh                README      single     tonido                urandom
root@TonidoPlug:/etc# 

```

I'm pulling my hair out trying to correct this one. Please help!

---

### Post by regneva on 2010-10-01
Solved it using this:
[http://forum.soft32.com/linux/gentoo-load-libc-permission-denied-ftopict329228.html](http://forum.soft32.com/linux/gentoo-load-libc-permission-denied-ftopict329228.html)

---

