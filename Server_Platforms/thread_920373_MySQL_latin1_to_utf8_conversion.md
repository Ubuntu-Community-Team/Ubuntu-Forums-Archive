---
title: "MySQL latin1 to utf8 conversion"
date: 2008-09-15
forum: Server Platforms
---

### Post by porchrat on 2008-09-15
Hi out there in LinuxLand

I am running the Desktop version of 8.04 and am running a MySQL server (5.0) on it.  I'm trying to import a database into MySQL Workbench to create an ERD.  I'm having some problems as MySQL Workbench keeps telling me that my tables have non-utf8 characters and skips practically the entire table when importing.

The table doesn't contain any unique characters that I believe would cause any conversion problems.  The tables are latin1 tables in a MYISAM structure.

I tried converting the tables to utf8 using this method (yes I know not a perfect method, but surely it should work if the table doesn't contain any abnormal characters):

[http://www.hackszine.com/blog/archive/2007/05/mysql_database_migration_latin.html]("http://www.hackszine.com/blog/archive/2007/05/mysql_database_migration_latin.html")

I reran the mysqldump on the newly converted utf8 table (was just using 1 table to test) to create a .sql file and tried importing that, but once again MySQL Workbench sees non-utf8 characters.

Any ideas?

---

