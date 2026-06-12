---
title: "ftp server is slow"
date: 2008-07-01
forum: Server Platforms
---

### Post by hirohitosan on 2008-07-01
Hi there
On my box I have proftpd as a ftp server. In my office network I have another ftp server (freeBSD) and it respond faster that my proftpd. Both servers have a real IP.

It is possible to decrease the time for connection?

---

### Post by we_r_disturbed on 2008-07-10
Try adding the following line to your /etc/proftpd/proftpd.conf file.

IdentLookups off

Restart proftpd and try to login.  That should fix it.

---

