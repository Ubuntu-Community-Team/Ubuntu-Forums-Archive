---
title: "[MariaDB] Have I broken my DB?"
date: 2017-06-30
forum: Server Platforms
---

### Post by calby on 2017-06-30
Hi,
I was going to clean up my MariaDB for Seafile but it did not work and I can't find out what use seahub-db; does and according to MariaDB it did change something in the DB but I do find it hard to belive that I did break something in the DB with just the command "use seahub-db;" or did I?

Here is the output from the console:
```

MariaDB [(none)]> use seahub_db;
ERROR 1049 (42000): Unknown database 'seahub_db'

MariaDB [(none)]> use seahub-db;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A
Database changed

MariaDB [seahub-db]> DELETE FROM Event WHERE to_days(now()) - to_days(timestamp) > 90;
ERROR 1146 (42S02): Table 'seahub-db.Event' doesn't exist

```

---

### Post by darkod on 2017-06-30
First of all you have to be more specific about your question. By have you broken something in the DB you mean the database seahub-db or the whole DB server? The difference is big...

If you only ran the commands posted I do not see anything too problematic (but I'm not DB expert). You first told it to use the seahub-db database, and then the delete command failed because the table Event doesn't exist. So because the table doesn't exist the command couldn't have done any damage. It doesn't delete something you didn't tell it to delete.

PS. Once you are using a specific database, you should be able to see its tables with:
```
show tables;
```

---

