---
title: "Problems with 6.06 and PHP on a LAMP install"
date: 2006-06-05
forum: The Cafe
---

### Post by sheadley on 2006-06-05
I hope someone can help me here. I am new to ubuntu but not to Linux. I have installed a LAMP server from the iso i dnl  from a mirror site. The installation worked fine, but when I try to run php from the command line the system can find PHP5. I did a search to find the PHP binary and can't seem to find it anywhere. Also apache works ok, but when I try to load up a .php file, apache gives me just text, so I know there is a problem with my php install. Any ideas??


Regards,


Steven H.

---

### Post by WildTangent on 2006-06-05
You need to edit your php.ini file.
```

sudo nano /etc/php5/apache2/php.ini

```

then find (ctrl+w) the line that says:
```

;extension=mysql.so

```
And remove the ; from the beginning of the line, save it, and then restart apache:
```

sudo /etc/init.d/apache2 force-reload

```

Edit: crap, I just realized this is just to allow PHP to work with MySQL, which you need anyway. No idea why PHP wouldnt't be working with apache though.

-Wild

---

### Post by ssam on 2006-06-05
did you see [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by Johnsie on 2006-06-05
That seems like a lot of work.... Have you tried [http://apachefriends.org](http://apachefriends.org)

Xampp can do it all for you in under 1 minute:

Here's the instructions I stole off another thread:
1- download xampp from: [http://www.apachefriends.org/](http://www.apachefriends.org/)
2 - extract the file with: sudo tar xvfz filenameo.tar.gz -C /opt
3 - run the server with: sudo /opt/lampp/lampp start

(full instructions are on the website except you need to use sudo)

---

### Post by ubuntu_demon on 2006-06-05
My impression was that this is the only thing to get everything installed and configured :
$sudo lamp

But I might be wrong as I haven't tried a server install. And maybe this is for PHP4 instead of PHP5.

---

### Post by dada1958 on 2006-06-06
[QUOTE=ubuntu_demon]My impression was that this is the only thing to get everything installed and configured :
$sudo lamp

But I might be wrong as I haven't tried a server install. And maybe this is for PHP4 instead of PHP5.[/QUOTE]

I even didn't have to do that, my webserver worked out of the box after assigning a password for my MySQL database.

---

### Post by adamkane on 2006-06-07
XAMPP is overkill and is also a PITA to maintain:

Install LAMP + phpmyadmin this way:

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

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by arix on 2006-07-12
For run php scripts at the command line you must have php cli installed.LAMP server uses apache2 module for run php scripts only in web pages.

---

### Post by MoreBikesFewerCars on 2006-07-12
Thanks, Arix. That's exactly what I was looking for after being utterly confused by the PHP Online Manual Chapter 43. (And I've been programming in PHP for five years.)

Anyway, this is an easy install via Synaptic.

---

