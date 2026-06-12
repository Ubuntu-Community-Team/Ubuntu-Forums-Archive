---
title: "MySQL Help"
date: 2005-09-07
forum: Server Platforms
---

### Post by zero17 on 2005-09-07
I have a back up file from MySQL database, and the file name is hierm.sql.

and I want to put back or read back into the database, I've tried using:

```
adit@ubuntu:/var/www/hierm$ mysql hierm < hierm.sql
ERROR 1044: Access denied for user: '@localhost' to database 'hierm'

```

do you guys have any idea, why?

even though when I tried to use sudo

```
adit@ubuntu:/var/www/hierm$ sudo mysql hierm < hierm.sql
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)
```

any suggestion...?????

---

### Post by LordHunter317 on 2005-09-07
Is the mysql server running?

Did you set a password for the root user?  If so, you need to run:```
mysql -u roo -p hierm < hierm.sql
```

---

### Post by lao_V on 2005-09-08
mysql's 'access denied' error is nothing to do sudo (ubuntu's root account). Either you need to log into mysql as root (as explained above) or give your mysql user account enough previleges to carry out the task

---

### Post by LordHunter317 on 2005-09-08
[QUOTE=lao_V] or give your mysql user account enough previleges to carry out the task[/QUOTE]Which as I said elsewhere, is generally a very bad idea, unless you can limit those privileges (which you normally can't).

---

