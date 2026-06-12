---
title: "Webmin closing network access ?"
date: 2014-07-24
forum: Server Platforms
---

### Post by waloshin on 2014-07-24
It seems like Webmin closes apache, ftp, and its self on port 10000 after awhile. I have to keep rebooting the virtual server a few times an hour!

---

### Post by nerdtron on 2014-07-25
A system admin always checks the logs. Try checking the syslog and apache logs.

Any relevant information during the outage? Can you still access the local console of the virtual machine when this occurs?

---

