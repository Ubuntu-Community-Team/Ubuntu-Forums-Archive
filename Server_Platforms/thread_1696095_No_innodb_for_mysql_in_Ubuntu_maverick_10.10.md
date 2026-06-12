---
title: "No innodb for mysql in Ubuntu maverick 10.10?"
date: 2011-02-26
forum: Server Platforms
---

### Post by ianfp on 2011-02-26
I've just noticed that my MySQL server does not have the InnoDB storage engine enabled.  I cannot believe this is the case -- this makes Ubuntu completely unusable for my purposes.

Does anyone know why this is or how to fix it?

---

### Post by t3r0 on 2011-02-27
Hi,

At least on my installations the InnoDB is there... This sounds like a configuration issue with your setup.. Did you make any changes to the default my.cnf? Just a guess, that you adjusted the innodb_log_file_size ?

t. Tero

```

mysql> show engines;
+------------+---------+----------------------------------------------------------------+--------------+------+------------+
| Engine     | Support | Comment                                                        | Transactions | XA   | Savepoints |
+------------+---------+----------------------------------------------------------------+--------------+------+------------+
| InnoDB     | YES     | Supports transactions, row-level locking, and foreign keys     | YES          | YES  | YES        |
| MRG_MYISAM | YES     | Collection of identical MyISAM tables                          | NO           | NO   | NO         |
| BLACKHOLE  | YES     | /dev/null storage engine (anything you write to it disappears) | NO           | NO   | NO         |
| CSV        | YES     | CSV storage engine                                             | NO           | NO   | NO         |
| MEMORY     | YES     | Hash based, stored in memory, useful for temporary tables      | NO           | NO   | NO         |
| FEDERATED  | NO      | Federated MySQL storage engine                                 | NULL         | NULL | NULL       |
| ARCHIVE    | YES     | Archive storage engine                                         | NO           | NO   | NO         |
| MyISAM     | DEFAULT | Default engine as of MySQL 3.23 with great performance         | NO           | NO   | NO         |
+------------+---------+----------------------------------------------------------------+--------------+------+------------+
8 rows in set (0.11 sec)



```

---

### Post by ianfp on 2011-02-27
Thanks for the quick reply, Tero.  I did indeed customize my settings.  I'll reset them to the defaults and post the results here.

---

### Post by t3r0 on 2011-02-27
> **ianfp said:**
> Thanks for the quick reply, Tero.  I did indeed customize my settings.  I'll reset them to the defaults and post the results here.

If you did change the innodb log file size then you need to clear the old innodb log files and restart mysql to make it work.. innodb log files of different size than configured will cause innodb to fail "silently"... 

so you need to remove the old log files before... eg: 

```

$ sudo service mysql stop
$ sudo mv /var/lib/mysql/ib_logfile* /some/safe/location/
$ sudo service mysql start

```

- Tero

---

### Post by ianfp on 2011-02-27
Tero, you are a saint.  You were exactly right.  Thank you so much for your help.  You've saved me a lot of trouble (and taught me something in the process).

---

