---
title: "mysql user troubles help plz"
date: 2005-12-19
forum: Server Platforms
---

### Post by pedrotuga on 2005-12-19
Ok, no user has previleges to create a new database.. not even the root in the localhost :(

i tryed to uninstal mysql-server but when i installed it it had the same users settings :(
How can i reset the users?

thx

---

### Post by LordHunter317 on 2005-12-19
Your database root and your system user root aren't the same use.

Connect to mysql as root:```
mysql -u root 
```By default, the root DB user has no password.

---

### Post by pedrotuga on 2005-12-20
I've been messing around with the pirmitions and now the root has no privileges :(

can i connect as "debian-sys-maint"?

that user also came by default..

---

### Post by pedrotuga on 2005-12-20
yep!
it worked

---

