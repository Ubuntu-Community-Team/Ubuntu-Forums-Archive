---
title: "Bacula Database Setup"
date: 2012-05-28
forum: Server Platforms
---

### Post by ztux on 2012-05-28
I'm trying to setup Bacula to do local backups to a second internal drive. I cannot get bacula-director to test the config file, it always complains that it cannot connect to the database. I see the bacula user on the database in pgadmin3, but it doesn't have rights to make databases. If this is NOT a bug, how do you setup the database? There isn't anything in the Ubuntu documentation about setting up the database, and in Bacula's documentation, there is a reference to a script, create_bacula_database, but I cannot find this script in Ubuntu.

---

### Post by Habitual on 2012-05-28
Assuming you installed using the Software Center or whatever it is...
Terminal>
```
sudo dpkg-reconfigure bacula-director-mysql
```

If that fails, then the recipe I have is terminal >
```

myslq -uroot -p -e "create database bacula;"
mysql -uroot -p -e "grant all privileges on bacula.* to bacula@localhost identified by 'ZWNlOGYyM2Zj';"

```
Where "ZWNlOGYyM2Zj" would be your desired password.

"Catalog {"
in bacula-dir.conf should read something like 
```
dbname = bacula; DB Address = "localhost"; user = bacula; password = "ZWNlOGYyM2Zj"
```and bounce bacula-dir service daemon.

The script you cannot find probably is only included in source distributions of bacula.
The apt package manager should have created the bacula db and created tables in it.

HTH!

---

### Post by ztux on 2012-05-29
Thanks! dpkg-reconfigure bacula-director-pgsql did the trick!

---

### Post by Habitual on 2012-05-30
Rock on!

---

