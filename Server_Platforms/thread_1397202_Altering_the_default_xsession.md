---
title: "Altering the default xsession"
date: 2010-02-03
forum: Server Platforms
---

### Post by morrcahn on 2010-02-03
I work in a Linux lab, and we use a server for the home directories. After adding a new user they login in for the first time and it checks for the .dmrc file to see which xsession to use. Since there is no file (since they are new) it creates the .dmrc file and defaults to xfce. How can I change the default to gnome for the new users?

---

### Post by lykwydchykyn on 2010-02-03
There may be a better way to do it, but have you tried putting a .dmrc file set to gnome in "/etc/skel"?

---

### Post by morrcahn on 2010-02-03
No, I haven't but will. What exactly would that do? Does a new user (when they login the first time) access that directory? Thanks.

---

### Post by lykwydchykyn on 2010-02-03
> **morrcahn said:**
> No, I haven't but will. What exactly would that do? Does a new user (when they login the first time) access that directory? Thanks.

/etc/skel is a template for the default user's home directory.  When you create a new user with adduser or some similar tool, the contents of /etc/skel are copied to that user's newly created home directory.

---

### Post by morrcahn on 2010-02-03
Thanks. I will create a new user to test it.

---

