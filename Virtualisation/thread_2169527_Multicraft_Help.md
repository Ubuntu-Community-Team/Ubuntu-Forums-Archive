---
title: "Multicraft Help"
date: 2013-08-22
forum: Virtualisation
---

### Post by caison2 on 2013-08-22
I am not sure if this is where this goes. My problem is I installed SQLite. It now gives me this error.
Trying to connect to the panel database
Connection successful
Initializing database from: /var/www/multicraft/protected/controllers/../data/panel/schema.sqlite.sql
Opening database in production mode
Applying updates
Error re-opening database: Failed to update panel database from version 0 to 1 (latest: 10).
 If you believe that this update has already been applied or if you applied it manually using an "update.*.*.sql" file, please change the entry in the "version" table to 1.

 Detailed error message:
Update query failed: CDbCommand failed to execute the SQL statement: CDbCommand failed to prepare the SQL statement: SQLSTATE[HY000]: General error: 1 no such table: server_config. The SQL statement executed was: alter table `server_config` add `user_jar` integer not null default 0;

How do I fix this?
 Thanks

---

