---
title: "ulogd  U 12.04 LTS Server"
date: 2012-05-31
forum: Server Platforms
---

### Post by dashpilot79 on 2012-05-31
Hello,
  I have a 64-Bit  12.04 Server I just set up.  I'm trying to get Ulogd up and running, I had it going on my server before I switched from 9.0? to 12.04.  I did a clean install (Reformat Hard Drives, etc) of 12.04.  Now I can't get ulogd to work, it creates the ulog file under /var/log/ulog/ but the only entry in the file is a ulog bunch of time staps and the following entry "ulogd.c 594 sigterm received exiting".  It appears its logging stuff in a file callled syslogemu.log under the /var/log/ulog/ directory.

Anythoughts?

---

### Post by dashpilot79 on 2012-06-23
Upgraded to Kernel -25 and the problem is now fixed.

---

