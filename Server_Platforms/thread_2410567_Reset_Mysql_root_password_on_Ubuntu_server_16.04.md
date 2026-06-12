---
title: "Reset Mysql root password on Ubuntu server 16.04"
date: 2019-01-17
forum: Server Platforms
---

### Post by peterterbe on 2019-01-17
I have already found the Mysql Password Reset page here: [https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

My problem is that when I stop mysql server the /var/run/mysqld folder has been removed immediately and ```
sudo /usr/sbin/mysqld --skip-grant-tables --skip-networking &
```  doesn't create one so the next command where I should connect to the mysql server without password can't connect to the socket because it isn't exists.

---

### Post by LHammonds on 2019-01-18
I have not seen that problem before.  Might be helpful to post the exact error message you get when you issue the "mysql -u root" command as well as post log results after starting mysql in single-user mode.

LHammonds

---

