---
title: "Mysql debian-sys-maint user"
date: 2012-06-13
forum: Server Platforms
---

### Post by Jake.Debord on 2012-06-13
I am wondering if anyone can give me some insight as to what all typically uses debian-sys-maint username under mysql...

I get this error.

/etc/cron.daily/logrotate:
error: error running shared postrotate script for /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log
run-parts: /etc/cron.daily/logrotate exited with return code 1

I've discovered this is related to /etc/mysql/debian.cnf and I can change the password to match the debian-sys-maint password in mysql database. If I knew it. Since I don't I *could* change the password in mysql, however what all will that affect? I'm worried about changing it and breaking more than I'm fixing. The log rotate isn't a huge deal, although annoying I can deal.

Thanks in advance!

---

### Post by Jake.Debord on 2012-06-14
Bump. :(

---

