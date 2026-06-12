---
title: "MySQL upgrade from 5.0 to 5.1"
date: 2008-01-14
forum: Server Platforms
---

### Post by CLI-Linux on 2008-01-14
I'm needing to upgrade from mysql server 5.0 to 5.1, but I'm not all that in tune with how to do so.  I installed 5.0 from the apt-get repos (and there is no 5.1 in the repo).  I've checked up on the mysql dev site on how to do some of the stuff, but I'm having problems with understanding two things:

1. How do you switch everything so that the mysql and mysqld go to the new server (and can I just untar/gunzip the package anywhere)?

2. I'm having trouble when I run the mysql_upgrade on my existing tables.
```

[checks all my databases...they come back OK]
Running 'mysql_fix_privilege_tables'...
ERROR 1193 (HY000) at line 68: Unknown system variable 'have_csv'
ERROR 1064 (42000) at line 70: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'NULL' at line 1
ERROR 1243 (HY000) at line 71: Unknown prepared statement handler (stmt) given to EXECUTE
ERROR 1243 (HY000) at line 72: Unknown prepared statement handler (stmt) given to DEALLOCATE PREPARE
ERROR 1193 (HY000) at line 76: Unknown system variable 'have_csv'
ERROR 1064 (42000) at line 78: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'NULL' at line 1
ERROR 1243 (HY000) at line 79: Unknown prepared statement handler (stmt) given to EXECUTE
ERROR 1243 (HY000) at line 80: Unknown prepared statement handler (stmt) given to DEALLOCATE PREPARE
FATAL ERROR: Upgrade failed

```](*,)

If anyone has anything to share if they have done this in the past, please let me know.  Thanks.

---

