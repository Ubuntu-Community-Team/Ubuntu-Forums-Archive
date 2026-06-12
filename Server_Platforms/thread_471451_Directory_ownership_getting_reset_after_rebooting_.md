---
title: "Directory ownership getting reset after rebooting server"
date: 2007-06-12
forum: Server Platforms
---

### Post by tr333 on 2007-06-12
I am having problems with directory ownership.
I have given the user "www-data" the ownership of the /var/lock/apache2 directory, as webdav needs to access this directory, but when i reboot the machine (not very frequently) the ownership reverts back to "root".  Is there any way to prevent this from happening?

I can survive with changing the ownership every time, but I sometimes forget what has gone wrong when webdav stops working which gets annoying.

---

### Post by Mr. C. on 2007-06-12
Edit the file /etc/init.d/apache2.  Find the start) case and add your chown command after the line:

```
[ -d /var/lock/apache2 ] ||  mkdir -p /var/lock/apache2
```

MrC

---

### Post by tr333 on 2007-06-12
Thanks!
Will try this in a few days when I can turn my server back on.

---

