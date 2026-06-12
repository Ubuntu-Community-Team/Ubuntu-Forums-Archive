---
title: "mysql acting weird"
date: 2010-11-08
forum: Server Platforms
---

### Post by thegodfaza on 2010-11-08
The command line mysql client has started acting odd. I'm using the latest version of MySql from Canonical and 10.10 amd64 server.

```
justin@singularity:~$ mysql
mysql: unknown option '--This was formally known as [safe_mysqld]. Both versions are currently parsed.'
justin@singularity:~$ sudo mysql -u syslog-ng -p xxxxxxxxxxxxx syslog-ng < /var/log/mysql.pipe
mysql: unknown option '--This was formally known as [safe_mysqld]. Both versions are currently parsed.'

```

The pipe has normal sql statements that execute fine in phpMyAdmin.

EDIT: Looking through my logs, this started on 11-05-2010.

---

### Post by Vegan on 2010-11-08
Looks like your tables might be trashed.

I learned the hard way to make so many backups that its the only way I will ever recover.

I now make daily backups after my own server crapped out into a reboot cycle very 3-5 minutes.

---

### Post by thegodfaza on 2010-11-08
The database it's self is fine. Other applications can read / write just fine and phpMyAdmin works fine. It's just the command line mysql client that doesn't work. The only thing I even use it for is a bash script to take syslog-ng logs and write them to a database.

---

### Post by DaithiF on 2010-11-09
Take a look at /etc/mysql/my.cnf, the section starting with [client]

The text you get in your error message is from the start of the section after that -- makes me guess you have some parameter in quotes in that section without a closing quote, such that the following text gets passed too.


```
[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]

```

---

