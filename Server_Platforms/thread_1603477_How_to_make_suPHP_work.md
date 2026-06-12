---
title: "How to make suPHP work?"
date: 2010-10-22
forum: Server Platforms
---

### Post by GreenDance on 2010-10-22
Hi, I've installed suPHP on my ubuntu server, only thing is, there's no examples of php code that I could find that shows how to do a root command (e.g. su useradd ... )

Can anyone help me please. I've been on this for 3 days and it's hurting my head :(

Thank You :KS:popcorn:

---

### Post by GreenDance on 2010-10-23
Anyone? Please :KS

---

### Post by Ryan Dwyer on 2010-10-23
Don't use suPHP. Instead, specify the commands in /etc/sudoers that www-data can run.

Here's an example:
```

Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
Cmnd_Alias WEB_CMDS = /etc/init.d/apache2, /etc/init.d/mysql, SHUTDOWN_CMDS
www-data ALL = (root) NOPASSWD: WEB_CMDS

```

Your web scripts can then execute those shutdown commands and restart Apache/MySQL without needing a password.

Remember to always edit /etc/sudoers by running visudo. Visudo checks your changes before saving to make sure you don't brick the system.

---

