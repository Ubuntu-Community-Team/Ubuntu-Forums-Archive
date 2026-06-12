---
title: "apparmor and mysql at odds, how to troubleshoot?"
date: 2012-06-20
forum: Server Platforms
---

### Post by lykwydchykyn on 2012-06-20
I have on my development laptop an install of mysql-server.  As far as I can remember, it's just a vanilla, straight-from the repositories install.  I haven't moved data directories or done anything weird (or anything really at all) with the config.

Yet, I cannot start mysql-server unless I first disable its apparmor profile.  The apparmor profile is also unaltered from the repositories.

I'm not really sure how to troubleshoot this, though, since /var/log/apparmor is empty, and trying to start mysql with it on only puts this generic error in syslog:
```

kernel: [344087.267725] init: mysql pre-start process (31897) terminated with status 1

```

---

### Post by lykwydchykyn on 2012-06-20
Nevermind.  I found the error when I restarted apparmor.  I was looking for a file /etc/apparmor.d/local/usr.sbin.mysqld, which is a local include file for the profile.  It was missing.

I created a blank file there, restarted apparmor, and all is happy.

weird.

---

