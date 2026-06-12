---
title: "Odd mount error for /dev/cdrom: /dev/eth0 is not a block device"
date: 2009-07-05
forum: Server Platforms
---

### Post by jmoorse on 2009-07-05
EDIT: It looks like this is a problem with our ESX server.

Hi Folks,

When I issue a:

# mount /dev/cdrom /media/cdrom

The console responds:

# mount: /dev/eth0 is not a block device

This happens both as root and when sudo'ing

2.6.28-13-server
Ubuntu 9.04 Server

Any help would be greatly appreciated!

Thanks in advance,
Jeff

---

