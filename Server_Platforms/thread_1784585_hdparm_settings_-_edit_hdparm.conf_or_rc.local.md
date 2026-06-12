---
title: "hdparm settings - edit hdparm.conf or rc.local?"
date: 2011-06-17
forum: Server Platforms
---

### Post by PrestonD on 2011-06-17
Hi all, having fun with my new ubuntu server (Natty) setup at home and have an hdparm question...

I would like my drives to spin down after a period of time and would like the hdparm settings to persist after a reboot.

Is is better to edit the /etc/hdparm.conf file to set the spin down time, or could I just add an hdparm entry in the /ect/rc.local file?

Which would be the preferred method, or does it matter?

---

### Post by ian dobson on 2011-06-17
Hi,

It doesn't really matter. I prefer to add options to rc.local as this file won't be updated when the OS is updated. Configuration files from packages might get updated.

Regards
Ian Dobson

---

