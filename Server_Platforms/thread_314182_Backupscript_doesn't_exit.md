---
title: "Backupscript doesn't exit"
date: 2006-12-07
forum: Server Platforms
---

### Post by StarQuake on 2006-12-07
I have a backupscript that is supposed to backup to tape.

It does work correctly if I do this:

```
mysqldump -uroot mysql > /root/mysqldump.sql
tar -cf /dev/nst0 /root/mysqldump.sql
rm /root/mysqldump.sql
```

The problem is I want to use mkfifo so it doesn't take any temporary disk space. Like this:

```
mkfifo /root/mysqldump.sql
mysqldump -uroot mysql > /root/mysqldump.sql &
tar -cf /dev/nst0 /root/mysqldump.sql
rm /root/mysqldump.sql
```

It runs alright till the end, but it doesn't exit. Any suggestions?

---

