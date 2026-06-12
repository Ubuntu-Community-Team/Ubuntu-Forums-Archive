---
title: "mysql-zrm cannot connect to remote db"
date: 2009-07-15
forum: Server Platforms
---

### Post by bluethundr on 2009-07-15
Hi

 I am a new mysql-zrm user. I am thrilled to begin. :D

 But here is my problem.

 I am able to access my remote mysql db as root from my backup client

```

backup:~# mysql -uroot -p --host=db
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 354
Server version: 5.0.51a-24-log (Debian)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 


```


and i think I configged zmanda properly:

```

password="my533kr3tp455"

# Fully qualified domain name of the MySQL server.
# This parameter is optional. If this parameter is not specified, values from
# my.cnf configuration file.
#
host="db.beta.beezag.com"

# Port to which the MySQL server is listening to. This parameter is optional
# and default value is 3306
#
#port=3306

```

but when I go to run mysql-zrm this is what I get:

```

backup:~# mysql-zrm-scheduler --now --backup-level 0 
Logging to /var/log/mysql-zrm/mysql-zrm-scheduler.log
Use of uninitialized value $zrm_version in concatenation (.) or string at /usr/bin/mysql-zrm line 1305.
INFO: mysql-zrm-version 
WARNING: Could not open file /etc/mysql-zrm/BackupSet1/last_backup. No such file or directory
ERROR: Command returned error
ERROR: Output of command: 'mysqladmin --user=root --password=***** --host=db.beta.beezag.com --ssl --ssl-ca=file1 --ssl-cert=file2 --ssl-key=file3 variables' is
mysqladmin: connect to server at 'db.beta.beezag.com' failed
error: 'Access denied for user 'root'@'backup.beta.beezag.com' (using password: YES)'
ERROR: Cannot connect to mysql server!
ERROR: /usr/bin/mysql-zrm did not finish successfully
backup:~# 

```

I was going by this tutorial, this is how i am trying to learn.

[http://www.howtoforge.com/mysql_zrm_debian_sarge](http://www.howtoforge.com/mysql_zrm_debian_sarge)


Thanks
Tim

---

