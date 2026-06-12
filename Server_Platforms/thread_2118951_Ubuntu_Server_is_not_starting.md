---
title: "Ubuntu Server is not starting"
date: 2013-02-22
forum: Server Platforms
---

### Post by xeerf on 2013-02-22
I had my Ubuntu Server 12.04 running for a few weeks until today, when power cut happened. 
  Since then it's not starting, monitor is displaying unsupported  resolution message (there is no GUI support installed on the server, it  is supposed to boot into text mode). No services are started and  therefore no remote connection is available.
  HW seems to be undamaged, I can access BIOS, also live Ubuntu  distribution is running well. Even the system drive looks fine, I can  access all the files so I made a full backup. I tried to check syslog,  but there are no new records.
  Can you give me an advice how to get it running back? Drive partition is made through LVM.

---

### Post by collisionystm on 2013-02-22
Boot with an Ubuntu-Live CD. Rename your /etc/X11/xorg.conf to xorg.old

reboot the server.

---

### Post by xeerf on 2013-02-22
There is no such file in /etc/X11.

---

### Post by oldos2er on 2013-02-22
Moved to Server Platforms.

---

### Post by xeerf on 2013-02-23
Thanks, I have already solved the problem. Most helpful advice was to set 
GRUB_TERMINAL=console in /etc/default/grub and run update-grub.

---

