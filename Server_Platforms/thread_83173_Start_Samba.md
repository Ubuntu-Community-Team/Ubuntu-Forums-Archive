---
title: "Start Samba"
date: 2005-10-28
forum: Server Platforms
---

### Post by janhelge on 2005-10-28
Hi,

How do I start, restart and stop samba under Ubuntu? Where do I configure it to start automatically?

---

### Post by heimo on 2005-10-28
sudo /etc/init.d/samba [start|stop|restart], I believe. And (still guessing) Boot Up Manager (BUM) should be somewhere under Administration, or you could use rcconf or update-rc.d or manually edit symlinks in /etc/rc2.d/ (or whatever initlevel you're using). :) Hopefully I wasn't too confusing.

---

### Post by janhelge on 2005-10-28
Hi,

You're not confusing at all!! I had installed only samba-common... hmm. I installed samba and yes it works. Thanks for your help :D

---

