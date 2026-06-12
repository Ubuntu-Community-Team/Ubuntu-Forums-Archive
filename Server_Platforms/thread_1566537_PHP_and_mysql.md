---
title: "PHP and mysql"
date: 2010-09-02
forum: Server Platforms
---

### Post by btowle on 2010-09-02
After updating to 10.04 LTS php files run by apache which connect to mysql databases (all on the same server) can no longer write to the databases.

PHP scripts can connect and see the data, but when the web forms are used to edit data or add new data nothing happens.  I can edit the mysql data using command line, phpmyadmin or navicat, (with the same user as the php web forms use) but not the web browser forms.  The forms have been working for the past 5 years until the upgrade.  This same thing has happened on 2 servers.

I don't get any errors, the writes just seem to fail.  I have used "php -a" to try the scripts and again everything seems to work without error, but the database is not changed.

I am pretty sure that I kept the old mysql config files when asked during the upgrade.

---

### Post by lykwydchykyn on 2010-09-02
- what did you upgrade from (which Ubuntu/mysql/php)?
 - How do your scripts interact with the database?  through a layer like PDO, or directly using mysql_query()?
 - Are you running apparmor?

---

### Post by de0xyrib0se on 2010-09-02
Have you tried issuing 'commit' statements?

---

