---
title: "Mysql Throws unknown variable error"
date: 2010-08-06
forum: Server Platforms
---

### Post by coolparth on 2010-08-06
Hi everyone,

I have searched high & low for a solution to this.. But looks like no one has had this issue yet.. 

When i try to start mysql server, i get the following error : [ERROR] mysqld: unknown variable 'general_log_file=/var/log/mysql/mysql.log'

Please help !

---

### Post by bschelst on 2010-08-06
Uncomment general_log_file in /etc/mysql/my.cnf
(as the value is default anyway)
then try again

---

