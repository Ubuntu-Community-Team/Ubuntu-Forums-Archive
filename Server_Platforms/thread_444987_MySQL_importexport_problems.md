---
title: "MySQL import/export problems"
date: 2007-05-15
forum: Server Platforms
---

### Post by tocleora on 2007-05-15
I'm trying to export data from a MySQL 4.1.20 Server and import the data into a MySQL 5.0.22 Server, and I'm getting errors.  The code I'm using to export from 4.1.20:

```

mysqldump -uusername -ppassword databasename > filename

```

and the code I'm using to import into 5.0.22:

```

mysql -uusername -p databasename < filename
Enter Password: password

```

It works for a long time and then eventually gives me this error:

> 
ERROR 1064 (42000) at line 1132: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''\nCardType = M\nTransAmount = 1.95\nTxnNumber = XXX\nReceiptId = XXX' at line 1


I made no change to the code what-so-ever, just straight from one step to the other.  Shouldn't MySQL 5.0.22 be downward compatible with sql files?  Any ideas on how to get this to work?

---

### Post by craigp84 on 2007-05-15
Hi tocleora,

I had similar issues too. This: [http://www.hackszine.com/blog/archive/2007/05/mysql_database_migration_latin.html?CMP=OTC-7G2N43923558](http://www.hackszine.com/blog/archive/2007/05/mysql_database_migration_latin.html?CMP=OTC-7G2N43923558) really helped me out.

It turns out the default char set changed to UTF8 in MySQL5, whereas it would have been latin1 before.

-c

---

