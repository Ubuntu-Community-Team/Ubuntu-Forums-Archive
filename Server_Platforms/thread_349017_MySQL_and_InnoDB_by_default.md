---
title: "MySQL and InnoDB by default"
date: 2007-01-29
forum: Server Platforms
---

### Post by FyreBrand on 2007-01-29
I would like to make InnoDB the default engine for MySQL while still keeping MyISAM available.  I've looked over the forums and also have looked at the MySQL documentation and forums.  I'm not finding the proper way to tell MySQL which engine to use as a default and especially not the Debian way since most info is Gentoo or RPM based.

I have looked through my.cnf and see that innodb is indeed available, but MyISAM is the default.  Where else should I look for global configuration and is there anything I should be careful about when switching engines.  This is for education and development only not for live server-database functionality.

Thanks.

---

### Post by phossal on 2007-01-30
I saw that you've read the documentation, but did you see this: [MySQL 5.0 InnoDB ]("http://dev.mysql.com/doc/refman/5.0/en/innodb.html") & [Startup Options]("http://dev.mysql.com/doc/refman/5.0/en/innodb-parameters.html"). Also, are you asking if you can swap the engines with, like, a command-line argument for a single database at startup?

InnoDB is the default engine when you use:
sudo apt-get install mysql-server mysql-client

And you can verify it by restarting mysqld.

---

### Post by FyreBrand on 2007-01-30
Thanks phossal.  I had read those, but I missed some information on the main page of section 14 "Storage Engines and Table Types".  I've been trying to cram too much information in lately and I'm missing small details.

About the current default:  I may have made a mistake when installing MySQL, althought I followed the instructions on the community help page.  When I do a show engines, this is what I get:
```

mysql> show engines;
+-------------+----------+----------------------------------------------------------------+
| Engine       | Support  | Comment                                                        |
+-------------+----------+----------------------------------------------------------------+
| MyISAM     | DEFAULT  | Default engine as of MySQL 3.23 with great performance         |
| MEMORY    |    YES      | Hash based, stored in memory, useful for temporary tables      |
| InnoDB      |   YES      | Supports transactions, row-level locking, and foreign keys     |
| BerkeleyDB | NO       | Supports transactions and page-level locking                   |
| BLACKHOLE  | NO       | /dev/null storage engine (anything you write to it disappears) |
| EXAMPLE    | NO       | Example storage engine                                         |
| ARCHIVE    | YES      | Archive storage engine                                         |
| CSV        | YES      | CSV storage engine                                             |
| ndbcluster | DISABLED | Clustered, fault-tolerant, memory-based tables                 |
| FEDERATED  | YES      | Federated MySQL storage engine                                 |
| MRG_MYISAM | YES      | Collection of identical MyISAM tables                          |
| ISAM       | NO       | Obsolete storage engine                                        |
+------------+----------+----------------------------------------------------------------+
12 rows in set (0.00 sec)

```
I also verified that by creating a small bunk database putting two tables in it and then checking what engine it was using.  From what I can understand, with my very limited database knowledge, MyISAM is still the default and InnoDB is enabled by default but isn't the default engine.  So the answer seems to be adding the switch:
```
--default-storage-engine=innodb
``` to the /etc/mysql/my.cnf file.

Since I'm a student in an all Windows-IIS class that is using InnoDB I would like to use that as well.  MyISAM's flaws (referential integrity, blah blah) have been pointed out and I can't really disagree with them.  So all of this is trouble is purely for academic purposes.   I'm the old guy in the class and they all think I'm crazy for using Linux.  That only makes me more stubborn to find the answer.

I really appreciate you taking the time to point me back to the documentation for a second look.  It really helped.  I will add that line and restart the server.  I'll post back in a bit with the results.

---

### Post by phossal on 2007-01-30
I killed mysqld, and then restarted it:
```
sudo mysqld --default-storage-engine innodb &
```
Then I checked *your* way of verifying the default engine. Seems to work.

---

### Post by phossal on 2007-01-30
Regarding the documentation, of all the software I use on a day-to-day basis, I've found none that have as a complete and user-friendly documentation as MySQL. It's absolutely a joy, and, like Ubuntu, is as close to perfection in its respective category as I could ever imagine a thing being.

---

### Post by FyreBrand on 2007-01-30
> **phossal said:**
> Regarding the documentation, of all the software I use on a day-to-day basis, I've found none that have as a complete and user-friendly documentation as MySQL. It's absolutely a joy, and, like Ubuntu, is as close to perfection in its respective category as I could ever imagine a thing being.
I agree.  The MySQL documentation is pretty friendly.  I know next to nothing about MySQL and database terminology in general yet their documentation is very clear.

Those aren't really my ways of testing things, but since I know nothing of MySQL it was just what I knew at the time.  I had some problems shutting down and starting the server back up again.  I'm a little cautious about that since it's unfamiliar ground and I see a ton of threads by people who have wrecked their databases by making silly mistakes.

Anyways I did add the line to my.cnf.  The correct syntax does not have the double dashes in front of it.  The proper line to add to the my.cnf file is:
```
default-storage-engine=innodb
```

I had success.  I thank you again for the instruction and time.

---

