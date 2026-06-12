---
title: "Trying to install and run mandos and mandos-client"
date: 2010-08-30
forum: Server Platforms
---

### Post by johnt2010 on 2010-08-30
Hi there,

I am running Ubuntu 10.04 x86_64 Server on a server, and another Ubuntu 10.04 x86_64 server is running in a virtual machine connected to the same local network, both have LVM encrypted disks.

In trying to find a way to remotely unlock the disks after a reboot and I came across [Mandos]("http://wiki.fukt.bsnet.se/wiki/Mandos"). 

After trying for weeks I can't get mandos and mandos-client working together correctly.

I've followed the readme's ([install]("http://bzr.fukt.bsnet.se/loggerhead/mandos/trunk/annotate/head:/INSTALL"),[mandos-client]("http://bzr.fukt.bsnet.se/loggerhead/mandos/trunk/annotate/head:/debian/mandos-client.README.Debian") and [mandos]("http://bzr.fukt.bsnet.se/loggerhead/mandos/trunk/annotate/head:/debian/mandos.README.Debian")) and looked at the man pages, but haven't been able to work out my problem.

I've satisfied all the dependencies and enabled -use-ipv6=yes in avahi-daemon.conf.

The only way I can get it to work is when I test it (when the computer is running, using
```
/usr/lib/mandos/plugins.d/mandos-client --pubkey=/etc/keys/mandos/pubkey.txt --seckey=/etc/keys/mandos/seckey.txt --connect=192.168.1.100:45000; echo
```
) and force ipv4 communication between the two servers, but this isn't suitable as the pc with the mandos server on it isn't always running and the computer still can't automatically reboot.

The mandos-client in debug mode at boot displays
```
sendmsg() to 0:0:ff02:: failed: Invalid argument
```
multiple times after joining the mDNS multicast group.


Any help would be appreciated, hopefully I've just done something silly.:confused:

Thanks,

John

---

