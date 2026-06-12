---
title: "cannot print from thin client in ltsp 8.04: &quot;/usr/bin/jetpipe not found&quot;"
date: 2008-04-30
forum: Server Platforms
---

### Post by lanhelp on 2008-04-30
Hello, Im using ltsp with Ubuntu 8.04 desktop edition (Gnome). I press ctrl + alt + f1 in thin client and get this message:

/usr/bin/jetpipe: not found

Ive tried rebuild, update image and no success. seems to be a missing file bug on ltsp-client-core ?

options in lts.conf that causes the problem:

[ws013]
PRINTER_0_TYPE = U
PRINTER_0_DEVICE = /dev/usblp0

thanks a lot guys.

---

### Post by DATAndrews on 2008-08-29
This bit me too, and took forever for me to find the problem.

You should look at the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/224259](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/224259)

Follow the instructions (download script, make executable, remake client image) and reboot the client.  Voila!

---

