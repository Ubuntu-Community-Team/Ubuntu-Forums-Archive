---
title: "/var/lib/samba/secrets.tdb"
date: 2011-08-17
forum: Server Platforms
---

### Post by cmervine on 2011-08-17
Hi, 
I am running Ubuntu Server 11.04 and I am getting the message "Failed to open /var/lib/samba/secrets.tdb" when running pdbedit -w -L. This is not allowing it to connect to my Ldap Server. Does anyone have a fix for this?

Thanks

---

### Post by luvshines on 2011-08-19
You'll have to 'sudo' the command since secrets.tdb contains sensitive info which is available to 'root' user only

---

