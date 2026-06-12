---
title: "working with mdadm"
date: 2009-05-13
forum: Server Platforms
---

### Post by andyrowe on 2009-05-13
Hi all:
really trying to get the hang of ubuntu server, but still just a noob. The site where the server is located has power issues. I equipped the server with a UPS as I quickly learned Linux has a fit if it is shutdown unexpectedly. A few mornings when I get in the server apparently has lost power longer then the UPS can hold it up and the RAID has dropped down into degraded mode. First time it happened I removed the falled drive then readded it, the drive resynced and all was well. This morning when I tried to remoe or add the device I get a couple different errors such as:
/dev/sdb2 does not appear to be an md device
device or resource busy
permission denied
I'm going to get a UPS with an interface cable to tell the server to shutdown when the battery is getting low. Any help on how to implement a script/whatever on the server to do this would be appreciated
thanks in advance
andy

---

### Post by andyrowe on 2009-05-13
A syntatical error in typing the command seems to have been my problem. I was failling to put the MD in the remove command
mdadm --manage --remove /dev/sdb2
instead of
mdadm --manage --remove /dev/md1 /dev/sdb2
thus the /dev/sdb2 does not appear to be an md device messsage

---

