---
title: "Status of Common Unix Printing System: cupsd is not running but /var/run/cups ..."
date: 2011-03-29
forum: Server Platforms
---

### Post by msingh123 on 2011-03-29
I am running a CUPS server on a fileserver that runs Samba.

CUPS keeps dying at intermittent (~ once every 2 days) intervals.

$sudo service cups status
Status of Common Unix Printing System: cupsd is not running but /var/run/cups/cupsd.pid exists.


$ uname -a
Linux device 2.6.32-30-server #59-Ubuntu SMP Tue Mar 1 22:46:09 UTC 2011 x86_64 GNU/Linux

The situation rectifies through a CUPS restart but I am getting a little tired of having to do this.

Please help me debug this situation.

---

### Post by evil39c on 2011-03-30
What about your cupsd.conf ?
Maybe you set wrong.

---

