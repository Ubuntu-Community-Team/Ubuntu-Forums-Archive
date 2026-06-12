---
title: "PHP, MySql And PHPMyadmin"
date: 2005-08-15
forum: Server Platforms
---

### Post by noob_Lance on 2005-08-15
Hey, im trying to install phpMyAdmin, but then i go to localhost/phpmyadmin

i get this error

 MySQL said: Documentation
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

i had this problem when setting up the webserver for my town when i was in co-op, but failed, the guy i co-oped for (IT manager) was the one who figured it out... so i dont know the solution... plz help me.

Thanks
~Lance

---

### Post by noob_Lance on 2005-08-16
anyone?

---

### Post by az on 2005-08-17
apt-get install mysql-server?

---

### Post by deuce868 on 2005-08-17
It sounds like it can't connect to phpmyadmin. 

run:
ps aux | grep mysqld 

Make sure you have instances of the daemon running. If you do check that you didn't move the port off of 3306. Also make sure the phpmyadmin config file is looking on port 3306 & localhost to contact the mysql server.

---

### Post by az on 2005-08-17
Would you get that error if you did not create a root user password, as described in
/usr/share/doc/mysql*/readme.debian?


mysqladmin -u root password "insertithere"

---

### Post by deuce868 on 2005-08-17
[QUOTE=azz]Would you get that error if you did not create a root user password, as described in
/usr/share/doc/mysql*/readme.debian?


mysqladmin -u root password "insertithere"[/QUOTE]

I think you would get a phpadmin error stating "Invalid login using password YES" or something like that since the password would still be ""

---

### Post by Velox Letum on 2005-08-19
I had this problem earlier...its a simple matter of finding the MySQL socket and updating php.ini.

Open up a terminal and type *mysql -p*, then enter your MySQL root password. Once this is open you should have a prompt like so:

mysql>

Now type in *status*. Scroll around and you should find the socket in the middle somewhere. Now type *exit*.

Open up php.ini in your favorite editor, find the **mysql.default_socket** value and change it to the socket path you received from the MySQL status. Reload/reboot the webserver in question, and it should be fixed.

---

### Post by davro on 2005-08-21
Php version ?
MySql version ?

Really need some information, as backward compat is really an issue now with Php5*.
[http://www.zend.com/php5/articles/php5-mysqli.php](http://www.zend.com/php5/articles/php5-mysqli.php)

---

### Post by nattster on 2005-09-04
[QUOTE=Velox Letum]I had this problem earlier...its a simple matter of finding the MySQL socket and updating php.ini.

Open up a terminal and type *mysql -p*, then enter your MySQL root password. Once this is open you should have a prompt like so:

mysql>

Now type in *status*. Scroll around and you should find the socket in the middle somewhere. Now type *exit*.

Open up php.ini in your favorite editor, find the **mysql.default_socket** value and change it to the socket path you received from the MySQL status. Reload/reboot the webserver in question, and it should be fixed.[/QUOTE]
 Thanks

It really work!

---

