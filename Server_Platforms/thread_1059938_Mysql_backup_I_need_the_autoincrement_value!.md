---
title: "Mysql backup: I need the autoincrement value!"
date: 2009-02-04
forum: Server Platforms
---

### Post by Satrapo on 2009-02-04
Hello,

it seems that mysqldump doesn't backup the autoincrement value, I've tried some php backup script too but I cannot find out how to include the autoincrement value in my automatic-backup.

If I backup manually from phpmyadmin ok, I check the option to include tha autoincrement and works fine but I need to automate the backup and I need to have my autoincrement value stored in the backup.

Ubuntu server 6.06
PHP Version 5.1.2
Mysql Client API version 5.0.22

I've tried this:

mysqldump --add-drop-table -e -u[user] -p[passw] [databsename] > [backup_databasename].sql

but the autoincrement value is not stored in the backup

Thanks!

---

### Post by daily jobs on 2009-02-05
There are times when you have a lot of data in a database (let’s say wp_posts for a Wordpress blog like Ariejan.net). When you need to find and replace certain strings, this can be a very tedious task. Find all posts containing the “needle” string and manually replace all these occurrences with “chocolate”. With about 200 posts, you can imagine how long this would take to do manually.But, as I always say: “You’re a programmer! You should script the hell out of everything!”So, I found this: MySQL has built-in support to find and replace! Just a simple query will do:

---

### Post by hyper_ch on 2009-02-05
are you sure it doesn't? can you show the database structure from a dump?

try this:

```

mysqldump -u[user] -p[pwd] -hlocalhost -Q -c -C --add-drop-table --add-locks --quick --lock-tables [database] > [backup].sql;

```

---

### Post by Satrapo on 2009-02-09
> **hyper_ch said:**
> are you sure it doesn't? can you show the database structure from a dump?

try this:

```

mysqldump -u[user] -p[pwd] -hlocalhost -Q -c -C --add-drop-table --add-locks --quick --lock-tables [database] > [backup].sql;

```

Thanks but I tried it just now and yes I can confirm to you that it doesn't restore the autoincrement value.

I had a table with 18004 records and 18010 as autoincrement value before the backup, I've restored it from the backup and now the table has 18005 as autoincrement value.

Any suggestion?

---

### Post by unutbu on 2009-02-09
If you backup the /var/lib/mysql/DATABASE directory directly, then the autoincrement value will be preserved.

For example,
```

sudo rsync -a /var/lib/mysql/DATABASE/ /backup/DATABASE/
```

would copy DATABASE to /backup/DATABASE.

You could then restore DATABASE by typing
```

sudo invoke-rc.d mysql stop
sudo rsync -a --delete /backup/DATABASE/ /var/lib/mysql/DATABASE/
sudo invoke-rc.d mysql start
```

---

### Post by Satrapo on 2009-02-09
> **unutbu said:**
> If you backup the /var/lib/mysql/DATABASE directory directly, then the autoincrement value will be preserved.

For example,
```

sudo rsync -a /var/lib/mysql/DATABASE/ /backup/DATABASE/
```

would copy DATABASE to /backup/DATABASE.

You could then restore DATABASE by typing
```

sudo invoke-rc.d mysql stop
sudo rsync -a --delete /backup/DATABASE/ /var/lib/mysql/DATABASE/
sudo invoke-rc.d mysql start
```

Nice suggestion, I've tried and it seems to work fine!

Thanks a lot :p

---

### Post by hyper_ch on 2009-02-09
what about the --create-options for mysqldump=?

---

