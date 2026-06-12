---
title: "PhpMyAdmin error 1045"
date: 2009-12-21
forum: Server Platforms
---

### Post by Skidbladniir on 2009-12-21
```
#1045 - Access denied for user 'zac'@'localhost' (using password: YES)
```I have a fresh installation of MySQL and PhpMyAdmin.  I've created the user Zac, gave him all permissions.

---

### Post by MontelEdwards on 2009-12-24
Users on MySQL are different then Linux users on the machine.
You should of been prompted for a password the a "root" account.
If you do not remember, you can run ```
sudo dpkg-reconfigure mysql-server-5.0
``` or, if you are on Karmic then you'll do ```
sudo dpkg-reconfigure mysql-server-5.1
```

---

