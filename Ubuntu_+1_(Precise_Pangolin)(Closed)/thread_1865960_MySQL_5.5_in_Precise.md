---
title: "MySQL 5.5 in Precise"
date: 2011-10-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rv65 on 2011-10-20
It's about time MySQL v5.5 is in Ubuntu. I have a linode running MySQl 5.1, but 5.5 would be even better.

---

### Post by cariboo on 2011-10-20
How much longer are we going to be seeing Mysql now that Oracle owns it? I would assume we'll see [MariaDB]("http://mariadb.org/") as a replacement, just like LibreOffice replaced OpenOffice.

---

### Post by effenberg0x0 on 2011-10-21
MariaDB is said to be faster than MySQL in many situations because all the code is fresh, modern programming, no legacy. Has anyone tried it? If it support all of MySQL, transition should be easy. Just checked its not in repos.

EDIT: Found the repos:
# MariaDB repository list - created 2011-10-21 16:57 UTC # [http://downloads.askmonty.org/mariadb/repositories/](http://downloads.askmonty.org/mariadb/repositories/) deb [http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu](http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu) natty main deb-src [http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu](http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu) natty main

---

### Post by rv65 on 2011-10-21
> **effenberg0x0 said:**
> MariaDB is said to be faster than MySQL in many situations because all the code is fresh, modern programming, no legacy. Has anyone tried it? If it support all of MySQL, transition should be easy. Just checked its not in repos.

EDIT: Found the repos:
# MariaDB repository list - created 2011-10-21 16:57 UTC # [http://downloads.askmonty.org/mariadb/repositories/](http://downloads.askmonty.org/mariadb/repositories/) deb [http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu](http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu) natty main deb-src [http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu](http://mirror.de.gsnw.de:56431/mariadb/repo/5.3/ubuntu) natty main

Now how would I be able to transition from MySQL to MariaDB.

---

### Post by cariboo on 2011-10-21
MariaDB is a drop in replacement for Mysql, they were both written by the same person/team.

---

### Post by rv65 on 2011-10-22
Thats good to hear.

---

### Post by rv65 on 2012-01-15
I spotted a mysql-5.5 package in the precise repo, according to launchpad. This is alongside mysql 5.1. I think 5.5 could  very well be the version for Precise Pangolin until MariaDB replaces it.

---

