---
title: "MySQL Backups and restoring"
date: 2011-08-19
forum: Server Platforms
---

### Post by kerryhall on 2011-08-19
Alright, let's say I've made a backup of my MySQL database with:

mysqldump -u root -ppassword --all-databases | gzip > database

and I want to restore it with 

mysql -u root -ppassword < database

But I want to test the restoration first. How do I do that?

---

### Post by Wim Sturkenboom on 2011-08-20
Easiest would be a second machine ;)

Never tried the following, but it is what I would try
[LIST]
[*]stop the daemon
[*]make a copy (make sure you preserve the permissions) of the current databases (mysql directory) to some directory somewhere (e.g. /home/you/mysql2); make sure mysqld has access to it
[*]start mysqld with a path to the new directory (too lazy to check the syntax, something like --datadir if I recall correctly)
[*]drop all databases (except the mysql database itself ;) ); maybe safer to make some small changes first and see if the 'new' files are affected (check the date/time)
[*]restore your backup
[*]stop the daemon
[*]run a diff between the original and the new one
[*]restart the mysql server the normal way and cleanup the 'temorary' databases
[/LIST]
This might not work for innodb, not sure, it should work for myisam.

---

### Post by dinu90 on 2011-08-20
The easiest would be to backup the databases separately:
```

#!/bin/bash 
 
PASSWORD=ADD_MYSQL_PASSWORD_HERE 
mkdir -p /var/lib/mysql_backups 
 
for database in `echo "show databases;" | mysql -u root -p$PASSWORD|grep -v ^Database$`; do 
   /usr/bin/mysqldump --force -uroot -p$PASSWORD --opt -Q -c $database | gzip -9  > /var/lib/mysql_backups/$database.sql.gz 
done 

```You can then restore each database to some other name and test it as you wish

[**java tutorials**]("http://www.java-forums.org/java-tutorial/")

---

### Post by Wim Sturkenboom on 2011-08-20
> **dinu90 said:**
> ...
You can then restore each database to some other name and test it as you wishRestoring to a new database (name) is OK but e.g. in my setup it will not work as users will not have permissions on the new databases (except for root and dedicated admin users that I granted permissions). So that means adding grants which might be a lot of work.

I agree, by the way, with dumping each db in it's own tar ball; lot easier to restore one.

---

### Post by SeijiSensei on 2011-08-21
You can run a separate instance of MySQL bound to another port.  You'll need to specify a different directory structure as well.  You can probably build another instance from source and keep it in the /usr/local directory.  I've done that with PostgreSQL.

---

