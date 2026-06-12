---
title: "MySQL Server Won't Start"
date: 2005-08-21
forum: Server Platforms
---

### Post by Spudgun on 2005-08-21
Hi there,
I recieve the following error when trying to start the MySQL service:

```
Aug 21 20:59:03 localhost mysqld[9164]: 050821 20:59:03 Fatal error: Can't open privilege tables: Table 'mysql.host' doesn't exist
```

Anyone got any ideas how to fix this?

---

### Post by Spudgun on 2005-08-21
Ah, found the problem. For some reason, I removed 'mysql' database, which contained what the MySQL server couldn't find. A quick re-install has now fixed this.

---

