---
title: "MySQL not starting"
date: 2008-04-10
forum: Server Platforms
---

### Post by Darkmatter5 on 2008-04-10
I had MySQL working this morning, but the account I had setup wasn't able to do everything in the database.  So I tried logging in through the root account, no passwords worked.  So I used the following link to recover my root password.

[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

After I got to step 3, running "mysqld_safe --skip-grant-tables &" it'll say started and then just sit there.  If I then type the next command/step "mysql -u root" it'll state "ERROR 2002 (HY000): Can't connect to local MySQL server through socket 'var/run/mysqld/mysqld.sock' (2)".  So I then ran "/etc/init.d/mysql stop" and then "/etc/init.d/mysql start", but instead of "[ OK ]" it now reports" [fail]".

Any ideas?

---

### Post by jonabyte on 2008-04-10
have you rebooted the server and see what errors if any when the system tries to start it?

---

