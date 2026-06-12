---
title: "mysql administrator"
date: 2008-12-15
forum: Server Platforms
---

### Post by Geran on 2008-12-15
I've been having a problem restoring mysql backups. I create a backup with mysql administrator, but I can't restore them, the entire restore section is grey-ed out.

Does anyone know about this?

---

### Post by cariboo on 2008-12-15
Have you tried in a terminal:

```
mysql -u <user> -p <database> < backup.sql
```

It sounds like you have a permission problem with your backup files. Check to see if your database user has at least read permissions on the backup files.

Jim

---

