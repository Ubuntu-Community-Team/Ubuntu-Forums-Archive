---
title: "MySQL inconsistent with table listing"
date: 2009-11-21
forum: Server Platforms
---

### Post by cmkrause on 2009-11-21
Using the MySQL GUI Admin or phpMyAdmin, it only shows 87 tables in a particular database of mine.  However when I go into the text console and do a ```
show tables;
``` it shows 2323 tables.  2323 is the number of tables that it should have, but regardless of what user I use, I can only access the data in those 87 tables.  I am pretty sure that I have correctly adjusted the file permissions, since the owner and the group are both "mysql"

Any suggestions of how to access to all the reminder of these files?

---

