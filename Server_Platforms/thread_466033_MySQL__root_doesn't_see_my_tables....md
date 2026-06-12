---
title: "MySQL : root doesn't see my tables..."
date: 2007-06-06
forum: Server Platforms
---

### Post by ThaNerd on 2007-06-06
To make the story short, i goofed a few weeks ago... Wanted to chown /var/www recursively to apache user, but instead, i actually chowned the whole /var tree. I could fix a few things so that the website still works, but i didn't check further as i didn't have much more concern.

But now i noticed that for some reason, when i login as root in mysql (with password, either from console or from phpmyadmin), root user only see the "information_shema" table. However, my website's CMS still can access its own tables with its own user...

I guess my chown goof is the source of the issue.

Could anyone tell me what directories i should chown, and to which user? I didn't touch anything outside of the /var tree.

Final note : i'm under feisty, using most recent version of all programs available thru apt-get (apache 2, php 5, phpmyadmin, mysql...)

Thanks in advance!

[FONT="Lucida Console"]-------------------8<-----------------
user@machine:/var/lib/mysql$ mysql -u root -p
Enter password: *******************
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 87
Server version: 5.0.38-Ubuntu_0ubuntu1-log Ubuntu 7.04 distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
+--------------------+
1 row in set (0.00 sec)

mysql> use wordpress;
Database changed
mysql> show tables;
ERROR 1018 (HY000): Can't read dir of './wordpress/' (errno: 13)
mysql>
[/FONT]

---

### Post by jscrilla on 2007-06-06
Well, I'm not entirely sure, but I would check to see who owns the mysql folder under /var/lib

It should be set to mysql.mysql. On my server all other folders in that directory are owned by root. 

sudo chown mysql.mysql /var/lib/mysql

And all files and folders in that directory should also be owned by mysql user.

---

### Post by ThaNerd on 2007-06-06
I've found the error and it was not about the user... I didn't remember, but it seems that in a panic, i had tried to fix that before (the chown episode was like 8 weeks ago)...

Apparently, i did a chmod -r instead of chmod -R...
One removes read rights, the other does stuff recursively.

So i only hat do chmod -R +r * in /var/lib/mysql

Thanks for the try ;-)

---

