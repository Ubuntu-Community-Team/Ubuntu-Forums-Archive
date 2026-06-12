---
title: "server troubles... php5 not working"
date: 2006-08-01
forum: Server Platforms
---

### Post by msg on 2006-08-01
I installed _apache2_ _mysql_ _php5_ and _libapache2-mod-php5_

but still when I try opening a php file (http:/localhost/testphp.php) it asks me to download it instead of running it like a good server should

I even tried the _sudo a2enmod php5_ thing and then restarted apache2

it still asks to download the testphp.php file :(

how do I get php to work?

---

### Post by adamkane on 2006-08-01
Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start apache and mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by msg on 2006-08-01
thank you soo much you're a lifesaver

it works now :)

---

### Post by adamkane on 2006-08-01
Woo hoo!

---

### Post by dolson on 2006-08-03
$ sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql
Reading package lists... Done
Building dependency tree... Done
apache2 is already the newest version.
php5 is already the newest version.
mysql-client-5.0 is already the newest version.
mysql-server-5.0 is already the newest version.
phpmyadmin is already the newest version.
libapache2-mod-php5 is already the newest version.
libapache2-mod-auth-mysql is already the newest version.
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


It still tries to download the file.. I don't know what to do.. I don't have this problem on my Debian system.

---

### Post by harisund on 2006-08-03
```
$ sudo aptitude -y purge apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql apache2-common
$ sudo aptitude -y install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql apache2-common
```

---

### Post by adamkane on 2006-08-04
This is a foolproof method to install LAMP, but I still haven't figured out how to uninstall/re-install LAMP, when LAMP stops working.

Unfortunately the best you can do is try to troubleshoot (very difficult) or backup your database, and do a complete re-install.

Let us know if the above suggestion using aptitude works.

---

### Post by standleydj on 2008-04-07
I found out how to fix this well it worked 4 me 

run the follow commands in the terminal 

sudo mv /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/

sudo mv /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/

sudo /etc/init.d/apache2 restart

\\:D/

---

### Post by mesaynaysayer on 2008-05-12
**I LOVE YOU!!!!**
:KS 
I WAS DRIVING MYSELF NUTS TRYING TO SOLVE THIS AND YOU HELPED ME FIX IT!
IF THERES ANY WAY I CAN THANK YOU, PLEASE DONT HESITATE! :D 
[www.sudoshelby.com/blog](www.sudoshelby.com/blog) (im me :D )

---

