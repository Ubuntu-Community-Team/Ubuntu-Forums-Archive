---
title: "[SOLVED] Restoring MySQL databases from data/ files"
date: 2008-10-04
forum: Server Platforms
---

### Post by botfish on 2008-10-04
A while ago I backed up some MySQL data by copying all the directories and files in the MySQL data/ directory. I do not know what version of MySQL I was using at the time. It was XAMPP on WinXP that I installed about one year ago.

I have recently built Ubuntu Server version 8.04 and want to restore these databases.

What would the best way be to restore my databases? Could there be any problems if my previous version of MySQL differs from my current version?

Cheers.

---

### Post by cariboo on 2008-10-04
You could copy the databases to /var/lib/mysql then make sure that they read/write permissions and are owned by mysql and mysql group.

```
sudo chown mysql.mysql *
```

and for permission:

```
sudo chmod 700 *
```

Jim

---

### Post by botfish on 2008-10-05
Worked a treat.
Thanks.

---

