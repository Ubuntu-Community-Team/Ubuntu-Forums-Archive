---
title: "MySQL &quot;duplicate entry&quot; error"
date: 2010-06-14
forum: Server Platforms
---

### Post by pytheas22 on 2010-06-14
I'm trying to migrate a physical server to virtual hardware.  The old server runs RHEL 4 with MySQL version 4.1.12.  The new server runs Ubuntu 10.04 with MySQL 5.1.41.

In order to export all the MySQL databases from the old server to the new server, I ran the following command on the old server:
```

mysqldump -u mysql_root -p --opt --all-databases > dump.sql
```

I then attempted to import them on the new server with:
```

mysql -u mysql_root -p < dump.sql
```

The command successfully imports about half the databases, but then fails when it gets to a particular table in a database for one of our custom web applications.  The error message is:
```

ERROR 1062 (23000) at line 30268: Duplicate entry 'mostermeier-Member, PhD Thesis Committee (1 student)  ' for key 'pa_description'
```

I've located that line in the dump.sql file, and as far as I can tell it's not actually a duplicate entry.  I've also gone through dozens of bug reports and forum posts about an issue where this situation arises because a key is not set to auto-increment, but in this case the key is set to auto-increment.

I'd be very grateful for any assistance with this, as I'm not exactly a database guy and I've already tried everything I know to solve this, without success.

---

### Post by DaithiF on 2010-06-14
Hi,
I would experiment a little to decide definitively if there is indeed a duplicate key or if something weirder is going on.

So, first I would get a dump of just the problematic table:
mysqldump -h host  --database databasename --tables tablename > table.sql

then take a look at the table.sql file, in particular look for the KEY `pa_description`line -- what fields does it contain -- and are you 100% sure there are no records with duplicate values for those fields?  One way to confirm this is to delete this line from the file, then try loading this table into a test database.  With the definition for this index removed, does the table load succesfully?  If so then run some sql to check for duplicates: 
select field1, field2, count(field1) from table group by field1, field2 having count(field1) > 1; 
where field1, field2, etc are whatever fields make up the index.

if you need help with this let me know, in particular if you are ok to share the table dump file I can do these checks for you, but quite likely you won't be able to share the data I guess.

---

### Post by pytheas22 on 2010-06-15
Thanks so much for your response and help.  We had to take the new server done temporarily so I can't work on this any more right now, but it should be back up by Thursday.  I'll follow your recommendations then and report back.

---

