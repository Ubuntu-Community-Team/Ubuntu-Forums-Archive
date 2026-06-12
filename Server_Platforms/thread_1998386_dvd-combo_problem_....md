---
title: "dvd-combo problem ..."
date: 2012-06-06
forum: Server Platforms
---

### Post by dschinn1001 on 2012-06-06
Hello pangolins,

it is obviously because of my exotic dvd-combo-drive, with which
ubuntu 12.04 has no problems, but ubuntu-server 12.04 has ?

dvd-combo-drive (/dev/sdb) is recognized during booting installation of ubuntu-server.
All went well until end of installation and then after reboot ...
... ubuntu-server installed on harddisk, cannot recognize /dev/sdb any more ...

solution would be, to remove /dev/sdb out of booting - list of ubuntu-server, and
only booting from hard-disk. but /dev/sdb is not written in /etc/fstab ?
Means then: 
a) I remove /dev/sdb out of booting - list (but where is that ?)
or: 
b) I add /dev/sdb into /etc/fstab

I think a) makes server more secure ?
Or ?

Regards.
dschinn1001

---

### Post by rubylaser on 2012-06-06
I'm not sure what piece of hardware you're talking about. Please post the name and model number of what you're trying to get working.

---

### Post by dschinn1001 on 2012-06-18
Sorry for delay. Was busy here.
This device is a MatshitaBD-CMB UJ-120

Hint for you. e.g. Debian Installation-CD with Debian 6.0 resp. Debian 6.0.3 was working
fine and has no trouble with this device. Installation-CD with Debian 6.0.4 is behaving same
like the Ubuntu-Server-12.04-CD. This problem was solved with Kernel 3.4.x

Happy Coding.
Regards.
dschinn1001

---

