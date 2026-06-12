---
title: "mysql ignoring my.cnf"
date: 2010-03-11
forum: Server Platforms
---

### Post by phen0m on 2010-03-11
I need to make some changes to my mysql server configurations.  However, any modifications I make to the file /etc/mysql/my.cnf seem to be ignored by the service when it starts.

```
evan@annie:/etc/mysql$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
```

```
evan@annie:/etc/mysql$ strace mysql 2>&1 | grep cnf
stat("/etc/my.cnf", 0x7fff12afad90)     = -1 ENOENT (No such file or directory)
stat("/etc/mysql/my.cnf", {st_mode=S_IFREG|0644, st_size=3658, ...}) = 0
open("/etc/mysql/my.cnf", O_RDONLY)     = 3
stat("/etc/mysql/conf.d/mysqld_safe_syslog.cnf", {st_mode=S_IFREG|0644, st_size=21, ...}) = 0
open("/etc/mysql/conf.d/mysqld_safe_syslog.cnf", O_RDONLY) = 4
stat("/usr/etc/my.cnf", 0x7fff12afad90) = -1 ENOENT (No such file or directory)
stat("/home/evan/.my.cnf", 0x7fff12afad90) = -1 ENOENT (No such file or directory)
```

```
evan@annie:/etc/mysql$ cat my.cnf | grep lower
lower_case_table_names=1
```

```
evan@annie:/etc/mysql$ mysql -uroot -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 71
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show variables like 'lower%';
+------------------------+-------+
| Variable_name          | Value |
+------------------------+-------+
| lower_case_file_system | OFF   | 
| lower_case_table_names | 0     | 
+------------------------+-------+
2 rows in set (0.00 sec)
```

Any ideas? 

Thanks,
Evan

---

### Post by Ryan Dwyer on 2010-03-11
I just added that option to my /etc/mysql/my.cnf and it's showing up OK, but I'm using Lucid at the moment. The only things I can think of are that you might not be not adding it to the right section (under [mysqld]) or one of the other files in conf.d/ is changing the variable back.

EDIT: Just SSHed to my Karmic PC and tried it. Works fine.

---

### Post by phen0m on 2010-03-11
Thanks muchly!  The hours I spent because I'd put it at the bottom of the file :(((


Edit: although i was changing other values like port to see if changes were being applied but that wasn't getting picked up either.  Oh well, lower_case is working now and my deadline is too close for me to care about much else.

---

