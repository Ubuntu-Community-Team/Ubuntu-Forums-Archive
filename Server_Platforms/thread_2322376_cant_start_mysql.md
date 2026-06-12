---
title: "cant start mysql"
date: 2016-04-27
forum: Server Platforms
---

### Post by alex533 on 2016-04-27
hello
not sure if this is the right place to create thread but

Im using Ubuntu 15.04 and mysql 
today i found out that my mysql-server is inactive 
when im trying service mysql restart my terminal doesnt print anything, just running process without response
mysql status:
```
artesby@artesby:/etc/init.d$ sudo service mysql status -l
[sudo] password for artesby: 
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (start-post) since &#1057;&#1088;. 2016-04-27 23:07:43 MSK; 3min 51s ago
  Process: 20411 ExecStart=/usr/bin/mysqld_safe (code=exited, status=0/SUCCESS)
  Process: 20409 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 20411 (code=exited, status=0/SUCCESS);         : 20412 (mysql-systemd-s)
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;control
             &#9500;&#9472;20412 /bin/bash /usr/share/mysql/mysql-systemd-start post
             &#9492;&#9472;21552 sleep 1


&#1072;&#1087;&#1088;. 27 23:07:43 artesby systemd[1]: Starting MySQL Community Server...
&#1072;&#1087;&#1088;. 27 23:07:44 artesby mysqld_safe[20411]: 160427 23:07:44  mysqld_safe Can't log to error log and syslog at the same time.  Remove all --log-error configuration options for --syslog to take effect.

&#1072;&#1087;&#1088;. 27 23:07:44 artesby mysqld_safe[20411]: 160427 23:07:44 mysqld_safe Logging to '/var/log/mysql/error.log'.
&#1072;&#1087;&#1088;. 27 23:07:44 artesby mysqld_safe[20411]: 160427 23:07:44 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
Hint: Some lines were ellipsized, use -l to show in full.



```

my /var/log/mysql/error.log contains 
```
160427 23:17:44 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql2016-04-27 23:17:44 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more $
2016-04-27 23:17:44 0 [Note] /usr/sbin/mysqld (mysqld 5.6.28-0ubuntu0.15.04.1) starting as process 23054 ...
^G/usr/sbin/mysqld: Character set 'utf-8' is not a compiled character set and is not specified in the '/usr/share/mysql/charsets/Index.xml' file
2016-04-27 23:17:44 23054 [ERROR] Aborting


2016-04-27 23:17:44 23054 [Note] Binlog end
2016-04-27 23:17:44 23054 [Note] /usr/sbin/mysqld: Shutdown complete


160427 23:17:44 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended



```

last time i worked with database i installed mysql-workbench and created a new table with it, using utf-8
that time i didnt have errors
and now i have this problem

please, help me fix it

---

### Post by cariboo on 2016-04-29
You'll get more help here, than where you originally posted.

---

