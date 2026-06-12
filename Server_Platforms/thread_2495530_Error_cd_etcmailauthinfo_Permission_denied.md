---
title: "Error cd: /etc/mail/authinfo: Permission denied"
date: 2024-02-22
forum: Server Platforms
---

### Post by WhiteTigerIT on 2024-02-22
I need to install Sendmail on Ubuntu 22.04.3 server
I type
```
sudo mkdir /etc/mail/authinfo
sudo chmod -R 700 /etc/mail/authinfo
cd /etc/mail/authinfo
```
but I get the error
```
-bash: cd: /etc/mail/authinfo: Permission denied
```


Where am I wrong?

---

### Post by TheFu on 2024-02-23
File permissions.

Learn Unix file and directory permissions. Find a tutorial. Work through it. Usually this takes 15 minutes, but you'll need another 30-45 minutes of self-testing ideas before the permissions will "click" and you finally understand what works and what doesn't.

When you are testing your skills, open 3 terminals, create 3 test userids, put 2 into the same group, but leave the other outside that group.  Mix and match test directories and files inside those directories. Try every octal permission setting with all three users, and both the inclusive and exclusive groups.  Start with 000 and add a binary 1 until you reach 777 permissions. After each change, see which user(s) can and cannot access the files, directories, and which can edit, delete, create files.

You'll want/need to learn about **umask** settings too.

Helpful commands for this task:  touch, chmod, chgrp, chown, mkdir, rm, cp, less, and whatever editor you like most.

---

