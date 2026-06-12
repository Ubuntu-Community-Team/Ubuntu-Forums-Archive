---
title: "File descriptors"
date: 2016-03-23
forum: Server Platforms
---

### Post by Random20220612 on 2016-03-23
Hi, 

I'm trying to get the opened file descriptors by users httpd and jboss. My intention is write a script to be used as nagios plugin to monitor fds for apache and jboss. There are some plugins for fds but not for specific users. 

Any idea? 

Thanks.

---

### Post by Graham_Willis on 2016-03-31
How about using lsof? But be sure to read about possible security issues related to this tool first.

---

### Post by Random20220612 on 2016-04-01
Yes I tryied using LSOF with sudo privs for nrpe user but selinux problems forced me to run the check with ssh instead nrpe.

---

