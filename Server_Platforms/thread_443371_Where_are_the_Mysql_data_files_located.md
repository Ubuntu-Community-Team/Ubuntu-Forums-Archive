---
title: "Where are the Mysql data files located?"
date: 2007-05-14
forum: Server Platforms
---

### Post by Kulgan on 2007-05-14
I just set up a dual boot between Ubuntu and Ubustu, and I want the server that I originally had on Ubuntu to be available on Ubustu. 

The htdocs are just fine. Apache and ProFTPd are set up so that both can access the files (they are on a separate partition). 

But MySQL is a different matter. They are on the Ubuntu patition, of course. But I have absolutely no idea where on that partition they are, and as a result I don't know where to symlink to. 

Could someone inform me :( 

Cheers,
-K

---

### Post by StarMonkee on 2007-05-14
They're all in /var/lib/mysql

myisam tables have .frm, .myd and .myi files inside the directory for the table, and innodb data is stored usually in a file called ibsomething.

It's prefectly safe to copy myisam tables between servers by just zipping the directory then unzipping it on the new host :D

---

### Post by Kulgan on 2007-05-14
thanks, I'll give it a shot. 
The reason I'm symlinking instead of copying is that I want it to update both servers no matter what OS I boot. Hope there isn't any radical change in the layout of these files... 

/me crosses fingers

---

### Post by StarMonkee on 2007-05-14
I assume they would be the same, if it's the same mysql version.

I've copied the raw files between ubuntu and debian sarge/etch hosts in the past without any problems.

---

### Post by Kulgan on 2007-05-14
Woah... I just figured there's something wrong with the MySQL server, even with the original content. Starting the server fails, and trying to connect through terminal results in:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

Apparently (from the Service Manager), I also have "mysql-ndb" and "mysql-ndb-mg" installed and running. I don't remember installing them, though. Neither return results in the repositories. 

Re-installing mysql to see if it's anything I did that makes it screw up.

---

### Post by Kulgan on 2007-05-14
Ok... so this time, instead of going to /var/lib and symlinking the entire "mysql" directory to the Ubuntu partition, I went to /var/lib/mysql and symlinked the database (iss). Restart MySQL fine, connect well, "show databases;" includes "iss", and I can "use iss". 

When I go "select * from users;", it gives me:
```
ERROR 1017 (HY000): Can't find file: './iss/pages.frm' (errno: 13)
```

so I assume there is something wrong with the symlinking. But ls /var/lib/mysql/iss gives me the exact same content as /media/sda2/var/lib/mysql/iss ... 

I guess I will have to see whether there is some place in the configuration file that I can change to use another directory... 

-K

Update: 
Gotta love monologue threads....

Edited /etc/mysql/my.cnf line "datadir" to equal /media/sda2/var/lib/mysql, restarted and went back to 
> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

So I presume that there is something in the /var/lib/mysql that disagrees with the rest of it :(

---

