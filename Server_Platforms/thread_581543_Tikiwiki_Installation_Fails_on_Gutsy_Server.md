---
title: "Tikiwiki Installation Fails on Gutsy Server"
date: 2007-10-19
forum: Server Platforms
---

### Post by atrdallas on 2007-10-19
I have a clean install of Gutsy Server with LAMP and Postgres.  When I install Tikiwiki using aptitude, it fails regardless of selecting MySQL or Postgres for Tikiwiki's database.  The database password prompt fails both when I enter the db root or sudo root password.

---

### Post by tkharris on 2007-10-19
Are you using the system root password?  MySQL has a different "root" user and thus uses a different password than the system root user.  The password for the root user of myself is left blank on a default install.

To set it you will want to open a terminal and connect to mysql as root ( msql -uroot )

SET PASSWORD FOR 'root'@'localhost' = PASSWORD('MyNewPassword');

Then try the password you've set.

---

