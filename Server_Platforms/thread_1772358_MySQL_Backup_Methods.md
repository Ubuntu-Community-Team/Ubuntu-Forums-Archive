---
title: "MySQL Backup Methods"
date: 2011-05-31
forum: Server Platforms
---

### Post by DanHorniblow on 2011-05-31
Hi, I have a ubuntu 11.04 LAMP server running.
How would I go about backing up my MySQL database, do I need another server to mirror them to?

---

### Post by ruffEdgz on 2011-05-31
You can run another server of MySQL if you wish if you need a bit of 'high availability' but if you just need to have a backup of your database, you can just dump data from the database you want to save into a file and rsync it to another server for safe keeping.
```

mysqldump -u [username] --password=[password] -C -e --create-options [database name] > backup.sql

```
The options I am using don't have to be the same as mine but I hope this helps with giving you an idea.

---

### Post by DanHorniblow on 2011-05-31
Brilliant that works perfectly.

Would it be possible to schedule it to run every day, and save each backup as a different name?

---

### Post by ruffEdgz on 2011-05-31
This is a basic way of completing what you requested. Run 'crontab' probably as root then add the following code:
```

@daily mysqldump -u [username] --password=[password] -C -e --create-options [database name] > /location/of/backup/backup.$(date +%F).sql

```
This isn't the best practice since this leaves the password out in the open. I would suggest looking at this article if you want to not show your password in the crontab:

[http://www.serveridol.com/2010/04/12/mysql-passwordless-root-login/](http://www.serveridol.com/2010/04/12/mysql-passwordless-root-login/)

Hope this helps.

---

### Post by tension_ on 2011-06-01
You can use this script work perfect .:)

---

