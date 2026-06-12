---
title: "Add User: phpMyAdmin - LAMP Server"
date: 2014-02-02
forum: Server Platforms
---

### Post by jda8818 on 2014-02-02
Hello everyone:

New LAMP installation; apache2 ok, php ok, mySQL ok until I try to use phpMyAdmin.  phpMyAdmin won't persist in granting database-specific priveliges to a new user when I attempt to access mysql through the command-line monitor or by logging into phpMyAdmin with the new user credentials I have created.

Seems common problem with "ERROR 1045 (28000): Access denied for user 'southside'@'localhost' (using password: YES)

I can access the terminal monitor (mysql) and the browser-based phpMyAdmin with users 'root' and 'phpmyadmin' (both using passwords) but when I tried to create a user with privleges limited to one database (same name as user) I'm unable to get the privleges to persist as granted.   Or maybe I'm not granting these privleges properly.  I have deleted the anonomous users. New user southside at localhost wants to work with database southside but is unable to login.  

Thanks to everyone for their interest and comments or suggestions ...

jda8818

---

