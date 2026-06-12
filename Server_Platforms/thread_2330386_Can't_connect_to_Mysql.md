---
title: "Can't connect to Mysql"
date: 2016-07-11
forum: Server Platforms
---

### Post by dsashish86 on 2016-07-11
Hi ,

I installed mysql server and client in my system. But i can't connect by using 

sudo mysql -u root -p

shows "mysql: unknown option '--EOF'"

if i run 
$ps -ef|grep mysql 


mysql    13197     1  0 16:13 ?        00:00:02 /usr/sbin/mysqld
trivand  13550  2180  0 16:28 ?        00:00:00 /bin/bash /usr/bin/mysql-workbench
trivand  13553 13550  0 16:28 ?        00:00:00 /bin/sh /usr/bin/catchsegv /usr/bin/mysql-workbench-bin
trivand  13555 13553  0 16:28 ?        00:00:07 /usr/bin/mysql-workbench-bin
trivand  14920 10484  0 17:48 pts/4    00:00:00 grep --color=auto mysql


 $dpkg --get-selections | grep mysql


libdbd-mysql-perl                install
libmysqlclient18:amd64                install
libmysqlcppconn7                deinstall
mysql-client                    install
mysql-client-5.5                install
mysql-client-core-5.5                install
mysql-common                    install
mysql-server                    install
mysql-server-5.5                install
mysql-server-core-5.5                install
mysql-workbench                    deinstall
mysql-workbench-community            install


Please help me on this.
Thanks in advance.

---

### Post by howefield on 2016-07-11
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by nerdtron on 2016-07-11
Did you changed any of the default config in /etc/my.cnf ?

---

### Post by Habitual on 2016-07-11
sudo not necessary to login as the root mysql user, so try
```
mysql -uroot -p
```

---

