---
title: "You don't have permission to access on this server"
date: 2012-06-19
forum: Server Platforms
---

### Post by chaopoch on 2012-06-19
I just start learnning how to create .html and .php files with Dreamweaver in Windows system, I would like to open these files in Ubuntu, so I install LAMP server and Aptana Studio 3, .html files can be opened without any problem, but there is problem to open .php file.

In order to open .php file, I log into /local/phpmyadmin and create a database, then I import the database that I backup in trainning class, as attached database.png shown, the database is imported.

I copy the whole directory lunh_order_system created with Dreamweaver to /var/www, and type [http://localhost/lunch_order_system/name.php](http://localhost/lunch_order_system/name.php) in browser, but I get error message as attached Forbidden.png shown.

Trying to search solutions on internet, but fail, thanks for any reply.


[ATTACH]219959[/ATTACH]       [ATTACH]219960[/ATTACH]

---

### Post by Tylerjd on 2012-06-20
What is the webserver running as (user/group) and what are the file permissions (user/group and rwx permissions). As PHP is run as (basically) an executable, it will need to be able to execute it, and to make it easier, have the same user/group as the webserver.

---

### Post by chaopoch on 2012-06-20
> **Tylerjd said:**
> What is the webserver running as (user/group) and what are the file permissions (user/group and rwx permissions). As PHP is run as (basically) an executable, it will need to be able to execute it, and to make it easier, have the same user/group as the webserver.

webserver is "localhost".

I change the permissions of directory lunh_order_system and its files from root to user group, but it still does not work.

---

### Post by chaopoch on 2012-06-20
need help, thanks a lot!

---

