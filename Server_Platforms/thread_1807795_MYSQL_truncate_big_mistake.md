---
title: "MYSQL truncate big mistake"
date: 2011-07-19
forum: Server Platforms
---

### Post by wsonar on 2011-07-19
I was scrolling commands changed the name and accidently truncatd the wrong table in a rush to try to correct this I restored an old back up that was missing alot of information including new members

I really messed up bigtime I was going to set an automatic backkup job but haven't yet any thing I can do to recover?

---

### Post by rubylaser on 2011-07-19
Without backups, and a truncated table, unfortunately you're data is no more. Truncates can't be rolled back as they're not done in a transaction like deletes.

---

### Post by wsonar on 2011-07-19
I have my mysql_history file buut I can't find my new users it dosen't show the insert statements for them I was thinking if I found them in the file I could add them back manually

---

### Post by wsonar on 2011-07-19
apparently the mysql_history is only console commands would there be a php history file that might show this information?

---

### Post by wsonar on 2011-07-19
I have there e-mail I just need to find the md5 password to add them back

---

### Post by wsonar on 2011-07-19
I've tried looking in the apache2 log file but not having luck I'm sure it must be stored somewhere maybe mysql schema logs?

---

### Post by wsonar on 2011-07-19
> **rubylaser said:**
> Without backups, and a truncated table, unfortunately you're data is no more. Truncates can't be rolled back as they're not done in a transaction like deletes.

Is it true with postgreysql you can rollback a truncate?

---

### Post by wsonar on 2011-07-19
Thank the lord I turned on unlimited console scrolling I am able to go back to before I truncated it and had ran a select * from the tables that lost all the information now just a matter of inserting it back and relinking everything. I always the the pc on with the same console and unlimited scrolling

---

