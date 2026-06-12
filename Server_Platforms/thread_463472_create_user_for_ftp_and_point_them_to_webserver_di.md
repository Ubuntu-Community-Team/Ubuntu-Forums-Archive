---
title: "create user for ftp and point them to webserver directory?"
date: 2007-06-03
forum: Server Platforms
---

### Post by notquitehere188 on 2007-06-03
How do i create a new user for ftp access, and then make it so that when they log in, it will show the \var\www directory

---

### Post by pbw on 2007-06-03
Assuming you have proftpd installed as your ftp server, just edit proftpd.conf and change the default root directory.

As for adding a new user, man useradd or adduser. Both work fine.

You might like to check gproftpd for a userfriendly gui solution to adminning ftp.

---

