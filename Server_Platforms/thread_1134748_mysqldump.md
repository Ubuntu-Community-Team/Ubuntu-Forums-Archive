---
title: "mysqldump"
date: 2009-04-23
forum: Server Platforms
---

### Post by gishaust on 2009-04-23
I have decided to try and backup mysql server but I can't get it to work this is my code below. What is wrong with it?

```

mysqldump -u root -p "my password" wordpress > /home/backup.sql


```

the error I get is this
```

-bash: /home/backup.sql: Permission denied


```

if I try it with sudo I get the same problem

gishaust

---

### Post by gishaust on 2009-04-23
mysqldump --user=root --password=mypassord  wordpress>/home/april2009_backup.sql

go it to work

---

