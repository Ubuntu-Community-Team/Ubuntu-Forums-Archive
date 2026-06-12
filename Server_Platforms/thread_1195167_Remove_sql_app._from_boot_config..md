---
title: "Remove sql app. from boot config."
date: 2009-06-23
forum: Server Platforms
---

### Post by VipX1 on 2009-06-23
[SIZE=3]I use XAMPP on my Ubuntu 9.04 Jaunty.[/SIZE]
[SIZE=3]There is a another SQL app. running on the system when I start XAMPP. I use [/SIZE]```
/etc/init.d/mysql stop
``` [SIZE=3]and that sorts it. Can I change something in the [/SIZE]```
/etc/mysql/my.cnf
``` [SIZE=3]file so as that this sql isn't running after a reboot.[/SIZE]
[SIZE=3]I know I should be able to find answer to this somewhere but I have looked....alot.....[/SIZE]
[SIZE=3]TY in advance.[/SIZE]

---

### Post by alastair on 2009-06-23
You can probably do this via the GUI :

System / Administration / Services

and uncheck the "mysql" components. Or open a terminal and do a :

man update-rc.d

and read about the "remove" option.

---

