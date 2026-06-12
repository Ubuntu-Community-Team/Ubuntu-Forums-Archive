---
title: "Blocking a service from running"
date: 2012-05-04
forum: Server Platforms
---

### Post by Skaperen on 2012-05-04
It used to be as simple as doing "chmod 644" on the init script in /etc/init.d to block a service from being restarted by a reboot.  Now that does not seem to happen.  Another upstart breakage?  How do I leave an indication to upstart that I do not want this particular script to be running right now, without removing the script.

---

### Post by azzamite on 2012-05-04
Have you tried using chkconfig or sysv-rc-conf, I personally like the later.

---

