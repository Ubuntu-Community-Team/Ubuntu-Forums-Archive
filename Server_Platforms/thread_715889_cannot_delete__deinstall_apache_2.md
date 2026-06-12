---
title: "cannot delete / deinstall apache 2"
date: 2008-03-05
forum: Server Platforms
---

### Post by ben22 on 2008-03-05
Hello,

I want to remove Apache 2 and Lamp - so I run this command

sudo apt-get remove apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql && sudo apt-get autoremove

- HOWEVER, /etc/apache2 still exists afterwards.
How is that possible???

ben

---

### Post by rapiscan on 2008-03-05
That's the configuration directory for apache, and it's not related to the actual binaries and libraries that allow apache to run.   If you did successfully reomve  with apt-get, I suspect that it left the configuration directory behind on purpose.  Try typing:

```
whereis apache2
```

This will tell you where the package is installed on your system, if it is still installed.

---

### Post by sciurus on 2008-03-13
Use *apt-get --purge* if you want to remove the configuration files.

---

