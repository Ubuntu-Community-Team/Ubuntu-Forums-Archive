---
title: "MySql recompile with default UTF8"
date: 2009-01-27
forum: Server Platforms
---

### Post by kpm on 2009-01-27
I'd like it if the MySQL default collation and character set were all utf8 so that when I run the CREATE DATABASE command, I don't have to add the DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci each time.

I thought this would be a simple configuration file change, but it seems, after reading MySql docs, I have to recompile MySQL ([http://dev.mysql.com/doc/refman/5.1/en/charset-server.html](http://dev.mysql.com/doc/refman/5.1/en/charset-server.html)). As a side, it would be nice if during the MySQL installation, the system would prompt for the desired default character set and collation...

I'm running the latest MySQL on a newly installed Ubuntu 8.10 LAMP server.  The MySQL docs state I have to recompile with "./configure --with-charset=utf8 --with-collation=utf8_general_ci" to change from the latin1 default.  I don't understand why latin1 would be MySQL's choice over utf8 as the default on MySQL5, so if anyone has any comments on that, they would be appreciated, but I'm primarily looking for a howto for recompiling MySQL. I don't know where or when I run "./configure..."

Thanks

---

### Post by squee on 2009-01-27
Bump. This would also be useful for me. Thanks guys.

---

### Post by Spikerok on 2009-04-09
bump, need to know how to change MySQL Chars from utf8 on to cp1251

---

### Post by Spikerok on 2009-04-10
bump

---

### Post by lapinski on 2009-04-30
I ran into the same issue and I think I got it resolved without having to recompile mysql from source.

You just need to add the following 2 lines to your my.cnf option file (usually located under /etc/mysql/my.cnf)

at the end of [client] section, add:

```
default-character-set = utf8
```at the end of [mysqld] section, add:

```
character-set-server = utf8
```then restart your mysql server:

```
> sudo /etc/init.d/mysql restart
```and make sure it says OK with 

```
* Starting MySQL database server mysqld
```then check if it all works out 

```
> mysql -u root -p
mysql> show variables like '%char%';

```you should see the following:

```
+--------------------------+----------------------------+
| Variable_name            | Value                      |
+--------------------------+----------------------------+
| character_set_client     | utf8                       | 
| character_set_connection | utf8                       | 
| character_set_database   | utf8                       | 
| character_set_filesystem | binary                     | 
| character_set_results    | utf8                       | 
| character_set_server     | utf8                       | 
| character_set_system     | utf8                       | 
| character_sets_dir       | /usr/share/mysql/charsets/ | 
+--------------------------+----------------------------+
8 rows in set (0.00 sec)


```then any new database you create should have character set utf8 by default.

--Lapinski

---

