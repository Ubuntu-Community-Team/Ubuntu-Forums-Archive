---
title: "export mysql using phpmyadmin"
date: 2006-06-23
forum: Server Platforms
---

### Post by verbatim210 on 2006-06-23
i am using 2 machines with identical software.
dapper, LAMP and phpmyadmin.

1. on my first machine, i **EXPORT**ed my forum database using phpmyadmin.
2. on my second machine, i **IMPORT**ed my forum database using phpmyadmin.

here is the error...

basically i am trying to backup my forum successfully, all ideas solutions appreciated!!

---

### Post by matko on 2006-06-23
look here
[http://fragments.turtlemeat.com/mysql-database-backup-restore-phpmyadmin.php](http://fragments.turtlemeat.com/mysql-database-backup-restore-phpmyadmin.php)

i dont have phpmyadmin, so i use simple

mysqldump --opt -a -u USERNAME -p DATABASE > FILENAME.mysql


it works well for me. my database have 500MB and worked fire while i was migrating from gentoo machine to ubuntu

---

### Post by verbatim210 on 2006-06-23
hi matko,

i just tried your command-line version of the export/import and the problem still remains.  mysql says...

**You didn't enter any data to import!**

does anyone know what this means?

---

### Post by matko on 2006-06-23
[QUOTE=verbatim210]hi matko,

i just tried your command-line version of the export/import and the problem still remains.  mysql says...

**You didn't enter any data to import!**

does anyone know what this means?[/QUOTE]


dont know why. exactly this i used on my server 

mysqldump -u root -pPASSWD --opt verlihub > backupfile.sql

or install

sudo apt-get install mysql-admin

---

### Post by lamego on 2006-06-23
After looking at the error I would say the problem is that the php myadmin import function does not support a file has big as yours. 
phpmyadmin does work for quick import/export but is not really the best tool for this.
Create the export with mysqldump (as you did), and import using the mysql file with 
```
mysql db -u user -p pass < yourfile.sql
```

---

### Post by verbatim210 on 2006-06-24
3 cheers, thank you lamego...  you were right on the dot 100%
however, i had to make a modification to the command.

lamego said:
mysql db -u user -p pass < yourfile.sql
verbatim used:
mysql --database=forum -u user -p forum < yourfile.sql

---

