---
title: "dovecot starts too soon"
date: 2012-04-24
forum: Server Platforms
---

### Post by Skaperen on 2012-04-24
The dovecot daemon is starting too soon.  Trouble is, it is an upstart job and that means no symlinks in /etc/rc{2,3,4,5}.d to control the order.  So how do I control the order in upstart so that my script to add extra IP addresses always runs before any of the daemons?

---

