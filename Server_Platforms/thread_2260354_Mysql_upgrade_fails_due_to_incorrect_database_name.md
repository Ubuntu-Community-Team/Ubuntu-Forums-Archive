---
title: "Mysql_upgrade fails due to incorrect database name"
date: 2015-01-11
forum: Server Platforms
---

### Post by isecore on 2015-01-11
So, I've been sitting all morning trying to do a dump of a database. First I got this error:

```
mysqldump: Couldn't execute 'SHOW FUNCTION STATUS WHERE Db = 'fullcrimp'': Cannot load from mysql.proc. The table is probably corrupted (1548)
```

After some googling, this seems to be related to some kind of mysql bug, and the solution for it is to run mysql_upgrade and let it do its magic.

However, this fails because when I run it, I get the following error:

```
: Got error: 1102: Incorrect database name '' when executing 'CHECK TABLE ...  FOR UPGRADE'
```

I've tried all kinds of things to try to fix this. None worked. I feel as if I'm caught in some weird database Catch 22.

I'm stuck, what do I try now?

---

### Post by MAFoElffen on 2015-01-11
From looking through MySQL Bugs and the Oracle MySQL forum, I see a common theme...

On diagnostics, looking through the ouput of these two queries:
```

show create table mysql.proc\G;
check table mysql.proc extended;

```
Seeing where one of those stops, may point to an offending object, which may need to be repaired of delted for it to go on...

Most seemed to be fixed with:
```

mysql_upgrade -uroot -p
/* But if you ran the upgrade procedure already, then */
mysql_upgrade -uroot -p --force

```

<Still looking through this, more to come...>

---

### Post by isecore on 2015-01-11
I have tried --force on the mysql_upgrade with bupkus change in results. It still fails with the same errors.

Note that this is on a production LAMP-server, and everything works fine except that I can't dump some of the databases and get the above mentioned series of errors.

---

### Post by MAFoElffen on 2015-01-11
Can you please post the output of the errors (thinking the errors could be on some .*.tmp or .*.Trash.x files)

Seeing that when it comes up with the error that of incorrect db name, but that name came up as being null.

If you physically look at the the directory your db and tables are located, do you see files there that are hidden directory or files (start the name with a dot ('.filename.ext")?

Just trying to thing of ways MySQL would see a db or table, but not be able to return it's name... or get it's name but not be able to work with it...

Just brainstorming-- If you query the names and get a count of... and compare to what is physically there in those directories, what is the difference? That may point to what is coming back as a null pointer.

---

