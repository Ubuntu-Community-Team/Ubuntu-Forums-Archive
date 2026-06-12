---
title: "Need help with Cacti installation"
date: 2006-08-19
forum: Server Platforms
---

### Post by MatsB on 2006-08-19
I've been following this guide [https://help.ubuntu.com/community/Cacti?action=show&redirect=CactiHowTo](https://help.ubuntu.com/community/Cacti?action=show&redirect=CactiHowTo) and everything seems to be working ok so far (I'm running Ubuntu Server 6.06 Dapper Drake).

I've done these steps:
[B]-Installing Cacti on Ubuntu Server 6.06 (Dapper Drake)
-Setup Cacti
-Recommended: Create a root password for MySQL[/B]

root@cacti:/usr/share/cacti/site# zcat /usr/share/doc/cacti/cacti.sql.gz |mysql -u cacti -p cacti
Enter password:
ERROR 1050 (42S01) at line 5: Table 'cdef' already exists

??

---

### Post by herman_munster on 2006-08-29
Ran into the same problem. This post indicates that cacti does not run on MySQL 5.

[http://forums.cacti.net/about9550.html](http://forums.cacti.net/about9550.html)

---

### Post by jimm on 2006-08-29
Hi,

I recently upgraded from my Redhat Cacti install to an Ubuntu one and moved my data across from one to the other. It worked fine but I did need to do a few tweaks. It does work fine with MySql 5 as well.

First thing I recomend you do is go to the cacti site and install the patches that they have there for the latest version. This fixed one issue I had with table permissions.

Secondly it looks like the cacti tables have already been created before you are running the database setup script. You could try dropping the cacti database, recrating it (I think you have to do this first? If not just do the install) and run the table install again. The error suggests that the install cant create the tables because the already exist... You could also hack the install script to drop the tables before creating them.

Start with the patches though as that might fix it up.

Let me know if it doesnt work and I can hopefully help out further!

Thanks,
James

---

