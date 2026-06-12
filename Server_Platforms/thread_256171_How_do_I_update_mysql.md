---
title: "How do I update mysql?"
date: 2006-09-12
forum: Server Platforms
---

### Post by CzarAlex on 2006-09-12
Id like to update mysql to the latest version. How do I do that using the command line? Is there an apt-get command I can run to get the job done? :confused:

---

### Post by WagnerVaz on 2006-09-12
What version of mysql are you using?

---

### Post by CzarAlex on 2006-09-12
MySQL 4.0.24 as far as i can tell based on the notation I see upon loggin in to phpmyadmin

Welcome to phpMyAdmin 2.6.4-pl1-Debian-1ubuntu1
MySQL 4.0.24_Debian-10ubuntu2-log

Note: I am using Breezy Badger (not sure if this matters)

---

### Post by WagnerVaz on 2006-09-12
OK, before you upgrade you MySQL server, you will need backup your databases.
You can do it from PHPMyAdmin or with command line tool `mysqldump`.
After you backup you database(s), go to `synaptic` and remove all packages related with mysql or do apt-get remove "package" where package is mysql-common-4.1 (I think) (to be sure just do double tab to se the options).
After removing package, install the package mysql trought `synaptic` or with `apt-get`.

After instaled try to up the mysqld process.
Restore you database backup and be happpy.

I think what I write is some confusion, (my english is SUX) so ask for any dobout.

Good Look

---

