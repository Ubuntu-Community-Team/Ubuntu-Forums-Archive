---
title: "increment value in mysql"
date: 2009-05-12
forum: Server Platforms
---

### Post by bluethundr on 2009-05-12
Hello,

 I need to find out how to increment the uid value in this table creation command:

```

CREATE TABLE `users` ( `id` varchar(128) NOT NULL default '', `name` varchar(128) NOT NULL default '', `uid` smallint(5) unsigned NOT NULL default '5000', `gid` smallint(5) unsigned NOT NULL default '5000', `home` varchar(255) NOT NULL default '/var/spool/mail/virtual', `maildir` varchar(255) NOT NULL default 'blah/', `enabled` tinyint(3) unsigned NOT NULL default '1', `change_password` tinyint(3) unsigned NOT NULL default '1', `clear` varchar(128) NOT NULL default 'ChangeMe', `crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66', `quota` varchar(255) NOT NULL default '', `procmailrc` varchar(128) NOT NULL default '', `spamassassinrc` varchar(128) NOT NULL default '', PRIMARY KEY (`id`), UNIQUE KEY `id` (`id`) ) ;
```

the table looks like this:

```

mysql> select * from users;
+------------------+------+------+------+-------------------------+---------+---------+-----------------+---------------+---------------+-------+------------+----------------+
| id               | name | uid  | gid  | home                    | maildir | enabled | change_password | clear         | crypt         | quota | procmailrc | spamassassinrc |
+------------------+------+------+------+-------------------------+---------+---------+-----------------+---------------+---------------+-------+------------+----------------+
| user@example.com | user | 5000 | 5000 | /var/spool/mail/virtual | timd/   |       1 |               1 | hPNzz15aI9zGHGDk | sd1DusYhyDYHdsijd |       |            |                | 
+------------------+------+------+------+-------------------------+---------+---------+-----------------+---------------+---------------+-------+------------+----------------+
1 row in set (0.00 sec)
```

if you create multiple users the uid does not increment the way the table is currently designed.

thanks.

---

### Post by Alekz_ on 2009-05-12
> **bluethundr said:**
> Hello,

 I need to find out how to increment the uid value in this table creation command:

```

CREATE TABLE `users` ( `id` varchar(128) NOT NULL default '', `name` varchar(128) NOT NULL default '', `uid` smallint(5) unsigned NOT NULL default '5000', `gid` smallint(5) unsigned NOT NULL default '5000', `home` varchar(255) NOT NULL default '/var/spool/mail/virtual', `maildir` varchar(255) NOT NULL default 'blah/', `enabled` tinyint(3) unsigned NOT NULL default '1', `change_password` tinyint(3) unsigned NOT NULL default '1', `clear` varchar(128) NOT NULL default 'ChangeMe', `crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66', `quota` varchar(255) NOT NULL default '', `procmailrc` varchar(128) NOT NULL default '', `spamassassinrc` varchar(128) NOT NULL default '', PRIMARY KEY (`id`), UNIQUE KEY `id` (`id`) ) ;
```

the table looks like this:

```

mysql> select * from users;
+------------------+------+------+------+-------------------------+---------+---------+-----------------+---------------+---------------+-------+------------+----------------+
| id               | name | uid  | gid  | home                    | maildir | enabled | change_password | clear         | crypt         | quota | procmailrc | spamassassinrc |
+------------------+------+------+------+-------------------------+---------+---------+-----------------+---------------+---------------+-------+------------+----------------+
| user@example.com | user | 5000 | 5000 | /var/spool/mail/virtual | timd/   |       1 |               1 | hPNzz15aI9zGHGDk | sd1DusYhyDYHdsijd |       |            |                | 
+------------------+------+------+------+-------------------------+---------+---------+-----------------+---------------+---------------+-------+------------+----------------+
1 row in set (0.00 sec)
```

if you create multiple users the uid does not increment the way the table is currently designed.

thanks.

You miss a command:

```

CREATE TABLE `users` ( 
	`id` varchar(128) NOT NULL default '', 
	`name` varchar(128) NOT NULL default '', 
	`uid` smallint(5) unsigned NOT NULL AUTO_INCREMENT default '5000', 
	`gid` smallint(5) unsigned NOT NULL default '5000', 
	`home` varchar(255) NOT NULL default '/var/spool/mail/virtual', 
	`maildir` varchar(255) NOT NULL default 'blah/', 
	`enabled` tinyint(3) unsigned NOT NULL default '1', 
	`change_password` tinyint(3) unsigned NOT NULL default '1', 
	`clear` varchar(128) NOT NULL default 'ChangeMe', 
	`crypt` varchar(128) NOT NULL default 'sdtrusfX0Jj66', 
	`quota` varchar(255) NOT NULL default '', 
	`procmailrc` varchar(128) NOT NULL default '', 
	`spamassassinrc` varchar(128) NOT NULL default '', 
	PRIMARY KEY (`id`), 
	UNIQUE KEY `id` (`id`) 
) ;

```

Try doing this:

```
alter table users modify uid auto_increment;
```

(should work! :))

By the way.. The default value is set to 5000.. Is it correct?

---

### Post by bluethundr on 2009-05-12
Wonderfull!!!! Thanks incredibly much! Yes I thought it may have been Auto_Increment I just wasn't sure where to put it cuz I'm sorta new at MySQL. 

and yes, 5000 is the correct default. 

thanks again!

---

### Post by bluethundr on 2009-05-13
bummer. tried your command this was the result for table insertion:

```

ERROR 1067 (42000): Invalid default value for 'uid'
mysql> 
```

and the alter didn't work either:

```

mysql> alter table users modify uid auto_increment;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'auto_increment' at line 1

```

further thoughts? :confused:

---

### Post by Alekz_ on 2009-05-13
Take a look here:
[http://dev.mysql.com/doc/refman/5.1/en/alter-table.html](http://dev.mysql.com/doc/refman/5.1/en/alter-table.html)

It may help you!

---

