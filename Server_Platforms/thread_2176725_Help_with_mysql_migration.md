---
title: "Help with mysql migration"
date: 2013-09-25
forum: Server Platforms
---

### Post by ant3 on 2013-09-25
migrating from natty 11.04 server mysql 5.1.54, apache 2.2.17,  phpmyadmin 3.3.10 deb1 to ubuntu 12.04 LTS, mysql 5.5.32, apache 2.2.22  phpmyadmin 3.4.10 1deb1.
With that said i have tried to backup and restore, export and import,  save and copy, our mysql and this is what has happened each time looking  at screen shots. [[IMG]http://s5.postimage.org/cec1iuzoz/Scr_old_server.png[/IMG]]("http://postimage.org/image/cec1iuzoz/")[[IMG]http://s5.postimage.org/i3wvgwv8z/scr_new_server.png[/IMG]]("http://postimage.org/image/i3wvgwv8z/")
  what have i missed to move ???

---

### Post by nerdtron on 2013-09-25
> **ant3 said:**
> 
With that said i have tried to backup and restore, export and import,  save and copy, our mysql and this is what has happened each time looking  at screen shots. 
  what have i missed to move ???

What commands have you tried for backup and restore? Did you tried mysqldump to dump the database?
You can also try stopping the mysql service, then copy the whole /var/lib/mysql folder to the new server and then start the mysql service. (worked on mine twice)

---

### Post by ant3 on 2013-09-26
so i have done the mysqldump command, and the server has to be stopped to use it. i have exported thru phpmyadmin then imported thru phpmyadmin, i have copied the entire/var/www file then placed it on the new server all three process have came up with the same result, so i know all the database is all there. so it leaves me thinking that its phpmyadmin is not reading something ....

---

### Post by nerdtron on 2013-09-26
Investigate the databases and tables from the source and destination. If there are missing tables on you restoration you might need to import them manually.

From the source dump the database to data.sql file
```
**#mysqldump -u username -p databasename > /root/data.sql**
```

Copy the data.sql to the new server. Then restore on the destination.
```
mysql -u username -p
```
Create the database for restoration
```
mysql> create database databasename;
mysql>exit;
```
Restore the database.
```
mysql -u username -p databasename < /path/to/data.sql
```
If you have multiple databases, repeat the procedure.

Also, make sure that you webpage config files have the correct username and password when connecting to the database. It could be that the databases are all restored, but the webpages can't read the database. And also check the permissions on the webpage files, if their permissions changed you need to change them too.

---

### Post by Habitual on 2013-09-27
> **ant3 said:**
> what have i missed to move ???
Did you backup and restore the DOCUMENTROOTs?

---

