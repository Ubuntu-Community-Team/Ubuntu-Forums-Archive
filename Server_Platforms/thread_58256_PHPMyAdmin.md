---
title: "PHPMyAdmin"
date: 2005-08-19
forum: Server Platforms
---

### Post by JamesBond on 2005-08-19
when i try to access phpmyadmin i get this message, and i need help to fix it, thanks

[Quote=error message]
cannot load mysql extension;
please check PHP configuration
Documentation
[/quote]

thanks for the help

---

### Post by Velox Letum on 2005-08-19
Did you install from apt or compile from source? If you installed by apt, you'll want to install php4-mysql.

---

### Post by lee_connell on 2005-08-19
dpkg --purge phpmyadmin

apt-get install php4-mysql

if it's already installed try dpkg-reconfigure php4-mysql

apt-get install phpmyadmin


I just had this same problem the other night and i believe that's what fixed it, it wasn't setup properly in php.  Make sure when you load a web site with "phpinfo();" in the body that mysql plugin is listed there.

---

### Post by JamesBond on 2005-08-20
i just did those steps you listed, and i still get the same message

---

### Post by JamesBond on 2005-08-20
bump...anyone?

---

### Post by Velox Letum on 2005-08-20
Is the MySQL block in phpinfo();?

---

### Post by JamesBond on 2005-08-20
no....and now i cant get php working again, when i try to access phpinfo.php from my home dir i get a download file window, same thing when i try to view a index.php

EDIT:  ok, mysql appears in phpinfo for php5, but i can only view index.php all other php asks for me to download, and when  i try to change my mysql password i get this lovely message:

```

root@Gateway:/php-5.0.4 # /usr/bin/mysqladmin -u root password testpassword
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
root@Gateway:/php-5.0.4 #

```

i can connect to mysql db from phpmyadmin i just dont have any privliges, please help me

Andrew

---

### Post by Velox Letum on 2005-08-21
Open up a terminal/command line and enter:

```
mysql -u root mysql
```

Now you'll have a mysql> prompt, enter the line as I have below and replace <password> with your desired MySQL root passwed.

```
mysql> SET PASSWORD FOR root@localhost=PASSWORD('<password>');
```

---

### Post by LordHunter317 on 2005-08-21
That won't work, as you're missing a SQL statement, and he already has a password set, whihc is the issue.

What did you set your root DB password to?  You have to enter it to change it: add a -p to your mysqladmin line, and enter the old password at the prompt.

As for your other issue, it sounds like Apache doesn't have PHP support loaded and/or configured properly, but it's hard to tell.

---

### Post by davro on 2005-08-21
PHP 5+
MySQL is not enabled by default, nor is the MySQL library bundled.

The mysqli extension allows you to access the functionality provided by MySQL 4.1 and above.
[http://www.zend.com/php5/articles/php5-mysqli.php](http://www.zend.com/php5/articles/php5-mysqli.php)

In A Nutshell Php5 breaks PhpMyAdmin.

---

