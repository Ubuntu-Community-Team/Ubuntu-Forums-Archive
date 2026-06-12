---
title: "SOURCE command"
date: 2012-03-24
forum: Server Platforms
---

### Post by tomdagreek on 2012-03-24
Hi all!

Gawd could someone let me know how to work this SOURCE command?
The details..
I have a decent sized sql file that i have exported from a older server.I have exported this file to my desktop and it was saved as file.sql.
Of course it is too big to import back into phpmyadmin on new server.
What should I do? I have tried to ftp it back to my home dir on the new server.It could easily be transferred to my /var/lib/mysql directory but then its permissions are wrong.(using root ofc)

Help! 
Any suggestions?

---

### Post by Habitual on 2012-03-24
```
mysql -uroot -p <db_name> < /path/to/file.sql
```
will import it.

---

### Post by tomdagreek on 2012-03-25
Ahh..
Thank you! Did the job..

Some of the google searches were not helping me
tom:guitar:

---

### Post by Habitual on 2012-03-25
You're very welcome.

Glad it worked out.

---

