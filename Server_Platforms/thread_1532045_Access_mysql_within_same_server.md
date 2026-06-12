---
title: "Access mysql within same server"
date: 2010-07-15
forum: Server Platforms
---

### Post by mlinux on 2010-07-15
When you access mysql within the same Apache server (same ip address) via php, do you need to GRANT user ip in order to login  to mysql?

Where are the log files for php, mysql etc?

---

### Post by LepeKaname on 2010-07-16
If you use the mysql "root" account, you don't need. However that is not recommendable. You need to grant access to a user, like this (in case you don't know):

```
> GRANT ALL PRIVILEGES ON mydatabase.* TO myuser@localhost IDENTIFIED BY 'mysecretpass';
```

Note the "@localhost", which is where you set where the access will come from.

All the logs can be found at /var/log:

**Apache: **/var/log/apache2
**MySQL: **/var/log/mysql or /var/log/mysql.log and /var/log/mysql.err (you need to specify it in /etc/mysql/my.cnf as by default is turned off)

---

### Post by mlinux on 2010-07-16
Thanks. Grant access is only part of the problem. Now by reading into the Apache2 error.log, found the error is cause by undefined mysql_connect(). I believe something not set properly for php. Will google for solution.

---

### Post by Ryan Dwyer on 2010-07-16
You need to apt-get install php5-mysql.

---

### Post by mlinux on 2010-07-16
You save my day. Thanks again.

---

