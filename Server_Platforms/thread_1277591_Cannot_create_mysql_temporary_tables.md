---
title: "Cannot create mysql temporary tables"
date: 2009-09-28
forum: Server Platforms
---

### Post by pdragon04 on 2009-09-28
Running Ubuntu 8.04.3 LTS with the standard version of MySQL that comes with it. Trying to create a temporary table in MySQL using the following command:

```
CREATE TEMPORARY TABLE IF NOT EXISTS dnc_temp (
    areacode INT(3), phonenumber INT(7), add_delete CHAR(1), source_id INT DEFAULT '1');
```

And getting the following error:

```
ERROR 1005 (HY000): Can't create table '/tmp/#sql1089_55_0.frm' (errno: -1)
```

Removing the TEMPORARY flag to make it a real table works perfectly fine. I'm logged in as the database root user just to make sure it's not a permissions problem. 

The only thing I came across myself that might explain it had something to do with the MySQL profile in AppArmor, but gave no solutions to the problem. If that's even the cause in my case.

---

### Post by pdragon04 on 2009-09-28
Found the answer in the following thread. Definitely was AppArmor.

[http://ubuntuforums.org/showthread.php?t=1203454&highlight=mysql+temporary+table](http://ubuntuforums.org/showthread.php?t=1203454&highlight=mysql+temporary+table)

Figures I find it after I post the question. :)

---

