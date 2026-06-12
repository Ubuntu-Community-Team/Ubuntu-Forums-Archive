---
title: "[SOLVED] Problem connecting bacula with it's mysql database"
date: 2008-07-17
forum: Server Platforms
---

### Post by Biochem on 2008-07-17
I've just installed bacula from the repository with the mysql database (the default). It didn't installed a bacula-dir.conf so I created one, but I can't connect to the mysql database.

I have no clue on how mysql work so I'm a little stuck on this. Reading the bacula manual didn't help since it doesn't say how to connect to a mysql database and the appropriate installation parts refers to some scripts that are not found with a locate command.

 The database should be on the same computer as the bacula director.

I would appreciate any insight provided.

```
root@computer:/etc/bacula# bacula-dir -t -c bacula-dir.conf
bacula-dir: dird.c:877 Could not open Catalog "some-catalog", database "bacula".
bacula-dir: dird.c:882 mysql.c:194 Unable to connect to MySQL server.
Database=bacula User=bacula
MySQL connect failed either server not running or your authorization is incorrect.
17-Jul 14:00 bacula-dir ERROR TERMINATION
Please correct configuration file: bacula-dir.conf

```

Here is the relevant director entry
```
Catalog {
	Name = some-catalog
	password = "SomePassword"
	user = bacula
	DB Name = bacula
	#DB address = 127.0.0.1
}
```

---

### Post by Biochem on 2008-07-17
OK fooling around d I managed to get it work.

I add to install mysql-server, create a bacula database and user, grant the bacula user access right and create the table using /usr/share/bacula-director/make_mysql_tables.

I would have thought that apt-get would have take care of this.

---

### Post by linuxcorp on 2009-01-28
Hi There

Please can you explane how you got bacula to connect to the mysql database

---

