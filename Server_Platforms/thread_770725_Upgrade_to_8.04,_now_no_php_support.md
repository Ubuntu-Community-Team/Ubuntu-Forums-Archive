---
title: "Upgrade to 8.04, now no php support"
date: 2008-04-27
forum: Server Platforms
---

### Post by fije on 2008-04-27
I just upgraded my server from 7.10 to 8.04, and now it has lost php-support. html-files is displayed OK, but any php-file it will just ask what firefox should do with it, so the Apache is not working correct. Any ideas to what went wrong in the upgrade. Working ok in 7.10??

---

### Post by cdtech on 2008-04-28
The first thing I would check in apache is the mods enabled directory to see if the php5.conf and php5.load links are there.

See if the apache2.conf file was altered and that the AddType is listed.

```
whereis php5
```

---

