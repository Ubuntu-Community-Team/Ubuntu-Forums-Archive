---
title: "MySQL and phpBB2 problem..."
date: 2006-01-31
forum: Server Platforms
---

### Post by TriggerHappyChewie on 2006-01-31
I installed Apache2 and Php with no problem.  I also installed MySQL with which seemed like no problem.  I try to install phpBB2 but I get this error while trying to install:

```

Warning: mysql_error(): supplied argument is not a valid MySQL-Link resource in /var/www/phpBB2/db/mysql4.php on line 330

Warning: mysql_errno(): supplied argument is not a valid MySQL-Link resource in /var/www/phpBB2/db/mysql4.php on line 331
phpBB : Critical Error

Could not connect to the database

```

I don't know how to fix this.  I installed phpmyadmin, but I don't know what I'm supposed to do with it.  I also opened port 3306 tcp.  I'm not really sure what to do. Any help would be wonderful.

---

### Post by Horndog on 2006-01-31
It's been a while but If I remember you have to make a data base in MySql with phpmyadmin call it phpbbDB then you add this name and login info to phpbb setup. It will then add the tables. This does require a basic understanding of the programs involved.

---

### Post by TriggerHappyChewie on 2006-02-01
Gotcha, I'll try learning more about phpmyadmin.  I'll try this and see how it goes.

---

### Post by TriggerHappyChewie on 2006-02-01
Figured it out.  That was easy.

Thanks for the help!

---

