---
title: "Configuring Mysql for Bugzilla"
date: 2007-10-18
forum: Server Platforms
---

### Post by infinitezero on 2007-10-18
Does anyone have a quick howto for configuring mysql for bugzilla? Step by step would be nice.



Thanks,
iz

---

### Post by tkharris on 2007-10-19
apt-get install mysql-server?

bugzilla should have it's own .sql file to create the tables.  You'd set up the tables as root "mysql -uroot [database_if_not_defined_in_sql_file] < whatever.sql" then go into the console and do grant all on database.* to 'user'@'hostname' identified by 'password';.  Make sure to also change the root user's password as there is none by default.

---

