---
title: "Removing an FTP server"
date: 2007-03-31
forum: Server Platforms
---

### Post by Blazeix on 2007-03-31
Hi, I recently installed proftp server for experimentation. I finished experimenting with it, and now I'm trying to remove it. I uninstalled proftpd, and I no longer have a proftpd entry into /etc/init.d/. Whenever I reboot, however, a folder called 'ftp' is created in my /home/ directory.  I figured a user was left over, so I tried this:

```

sudo deluser ftp
/usr/sbin/deluser: The user `ftp' does not exist.

```

Anybody have any ideas on what is creating the 'ftp' folder? Thanks.

---

### Post by elst on 2007-04-01
Weird. There must be something in one of the startup scripts - home directories aren't automatically regenerated. Try running a grep against the /etc/rc2.d/ directory, and the file /etc/rc.local. The listed owner of the "ftp" home directory may also give you a clue.

---

