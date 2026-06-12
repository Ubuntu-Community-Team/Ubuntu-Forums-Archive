---
title: "Apt Sources"
date: 2005-02-26
forum: Server Platforms
---

### Post by Lift0 on 2005-02-26
I have this sources from ubuntuguide.org
But they don't work with example mysql-admin, should be nice not be forced to download them manually...?!

---

### Post by alastair on 2005-02-26
Seems to be around for my if I list available - either synaptic or :

apt-cache search mysql-admin

What errors? How are you getting them, doing what?

---

### Post by Lift0 on 2005-02-26
[QUOTE=alastair]Seems to be around for my if I list available - either synaptic or :

apt-cache search mysql-admin

What errors? How are you getting them, doing what?[/QUOTE]


I think apt-get install mysql-server installs the mysqladmin program...
but i can't do anything with it...getting "ACCESS denied" on every command i make and also everyone can login via phpmyadmin script, don't need to have any user at all...this was when i installed so that setup is in the install pretty scary, anyone knowing howto come through all this access denied?

---

### Post by alastair on 2005-02-27
Check the mysql manuals but you need a user and password set for the database, it looks like.

This is/was new to me (new to Debian), but there is a debian admin user called "debian-sys-maint" - see :

/etc/mysql/debian.cnf

There should be a password in there for this user.

See if you can login to the mysql database using this - if so, you can create other users and their access privileges - see the mysql manual.

mysql -u debian-sys-maint -p mysql

>> password as in debian.cnf

---

