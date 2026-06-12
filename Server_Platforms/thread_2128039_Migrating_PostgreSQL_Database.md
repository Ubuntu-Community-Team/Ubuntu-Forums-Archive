---
title: "Migrating PostgreSQL Database"
date: 2013-03-21
forum: Server Platforms
---

### Post by nerdtron on 2013-03-21
Hello experts :) PostgreSQL

We have and old server running postgreSQL 7.4 and  CentOS 4.4 (pretty old, its been up since about 2005) with its hard  drive at about 3% free. We have a new server at hand (Ubuntu 12.04,  PostgreSQL isn't installed yet) and I would like to ask your advice on  how can we migrate the database from the old with no downtime or minimal downtime as  possible.

Any steps on how we can migrate safely and immediately?

Thank you in advance.

---

### Post by sandyd on 2013-03-21
moved to server platforms

---

### Post by CharlesA on 2013-03-23
This should work:
[http://stackoverflow.com/questions/3498877/how-do-i-move-a-database-from-one-server-to-another-in-pgsql](http://stackoverflow.com/questions/3498877/how-do-i-move-a-database-from-one-server-to-another-in-pgsql)
[http://stackoverflow.com/questions/1237725/how-to-copy-postgres-database-to-another-server](http://stackoverflow.com/questions/1237725/how-to-copy-postgres-database-to-another-server)

---

### Post by SeijiSensei on 2013-03-23
To move an entire server you should use pg_dumpall.  pg_dump is designed to back up a single database.  

If you're not running this utility to back up your database every night, I strongly recommend writing a script to do so.  I once lost a PG database with no backup and now write backups with pg_dumpall every night and suck them to a server in my office with rsync.

---

### Post by nerdtron on 2013-03-24
> **CharlesA said:**
> This should work:
[http://stackoverflow.com/questions/3498877/how-do-i-move-a-database-from-one-server-to-another-in-pgsql](http://stackoverflow.com/questions/3498877/how-do-i-move-a-database-from-one-server-to-another-in-pgsql)
[http://stackoverflow.com/questions/1237725/how-to-copy-postgres-database-to-another-server](http://stackoverflow.com/questions/1237725/how-to-copy-postgres-database-to-another-server)

Thanks! I'll try it first on a test server and see how it works. While using this command, will the new database from version 7.4 usable to the new version 9.1?

---

### Post by nerdtron on 2013-03-24
> **SeijiSensei said:**
> To move an entire server you should use pg_dumpall.  pg_dump is designed to back up a single database.  

If you're not running this utility to back up your database every night, I strongly recommend writing a script to do so.  I once lost a PG database with no backup and now write backups with pg_dumpall every night and suck them to a server in my office with rsync.

Thanks! We do have a script to backup the old server but the backup copy hard drive is also full because they are identical hard drives. By the way, is there any difference between pg_dumpall and pg_dump databasename if you only have one database?

---

### Post by CharlesA on 2013-03-24
> **nerdtron said:**
> Thanks! We do have a script to backup the old server but the backup copy hard drive is also full because they are identical hard drives. By the way, is there any difference between pg_dumpall and pg_dump databasename if you only have one database?

There shouldn't be, but I'm used to MySQL, myself.

---

### Post by SeijiSensei on 2013-03-26
No, I don't think so.  I dump and restore specific databases all the time, like when I'm working on a site.  I use pg_dump to create the backup, then create a new empty database for development with createdb and populate it from the backup with "psql -U username dbname < /path/to/backup.sql".

I haven't encountered any problems moving a backup from an older version of PostgreSQL to a newer one. Most of the information in the backup uses pretty stock commands like CREATE TABLE, CREATE INDEX, and COPY.

---

