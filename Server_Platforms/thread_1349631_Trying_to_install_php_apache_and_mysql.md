---
title: "Trying to install php apache and mysql"
date: 2009-12-08
forum: Server Platforms
---

### Post by g_lev on 2009-12-08
Hello, I used to work with WAMP on my windows platform (for testing web cms like wordpress) and I need somethings similar for Ubuntu. 

I tried to install php apache and mysql using
```

sudo apt-get install php5 mysql-server apache2 phpmyadmin

```but I get nothing when running "localhost" on my browser.  
when I try to restart I get the following errors :
```

Gpacko@Gpack-desktop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2 
apache2: Syntax error on line 235 of /etc/apache2/apache2.conf: Syntax error on line 6 of /etc/apache2/sites-enabled/index.html: Expected </title></title> but saw </html>
  [fail]
Gpacko@Gpack-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2 
apache2: Syntax error on line 235 of /etc/apache2/apache2.conf: Syntax error on line 6 of /etc/apache2/sites-enabled/index.html: Expected </title></title> but saw </html>
[fail]
Gpacko@Gpack-desktop:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld  [ OK ] 
 * Starting MySQL database server mysqld  [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
Gpacko@Gpack-desktop:~$ 

```

Thank you for your help.

---

### Post by munky99999 on 2009-12-08
So since I basically did this last night.

[LIST]
[*]sudo apt-get install apache2 
[*]sudo apt-get install mysql-server 
[*]sudo apt-get install php5 libapache2-mod-php5 php5-mysql

[*]mysql -u root
[/LIST]

mysql> use mysql;
mysql> update user set password=PASSWORD("[COLOR="SeaGreen"]mynewpassword[/COLOR]") where User='root';
[COLOR="SeaGreen"]only green part needs to change. Unless you like that for your password.[/COLOR]
mysql> flush privileges;
mysql> quit
munky@munkydesktop:~$ mysql -u root -p
mysql> create database wordpress;
mysql> flush privileges;
mysql> quit

Copy the wordpress files to /var/www/

sudo cp /var/www/wp-config-sample.php /var/www/wp-config.php
sudo nano /var/www/wp-config.php

**DB_NAME **
wordpress
**DB_USER** 
root
**DB_PASSWORD **
P@ssw0rd
**DB_HOST **
localhost

sudo chmod -R 777 /var/www/

[http://localhost/wp-admin/install.php](http://localhost/wp-admin/install.php)


[SIZE="6"]
[COLOR="Red"]Horrible security here. Dont expose this setup to the net.[/COLOR][/SIZE]

If anyone wants to pm me the steps to do this securely. Hey great. I'll edit this :) Or post in here where I'm a numpty.

---

### Post by apel_2804 on 2009-12-08
You copied the files into /etc/apache2/sites-available/! 
**That's wrong, it's only for config files!**

The www root is "/var/www".

---

### Post by g_lev on 2009-12-08
I reinstalled it by purge etc'
but it doesn't work
> 
/etc/init.d/apache2 start
 * Starting web server apache2                                                                                                                               apache2: Syntax error on line 235 of /etc/apache2/apache2.conf: Syntax error on line 6 of /etc/apache2/sites-enabled/index.html: Expected </title></title> but saw </html>



---

### Post by g_lev on 2009-12-08
> **apel_2804 said:**
> You copied the files into /etc/apache2/sites-available/! 
**That's wrong, it's only for config files!**

The www root is "/var/www".
I have 2 files in that folder:
/etc/apache2/sites-enabled/000-default
and
/etc/apache2/sites-enabled/index.html

---

### Post by cdenley on 2009-12-08
> **g_lev said:**
> I reinstalled it by purge etc'
but it doesn't work

As the error indicates, it failed to parse your apache configuration in the file "/etc/apache2/sites-enabled/index.html". That is probably because that file doesn't contain any apache configuration, but website content, which (as apel_2804 said) does not belong in that directory.

---

### Post by HighCommander540 on 2009-12-08
> **g_lev said:**
> I have 2 files in that folder:
/etc/apache2/sites-enabled/000-default
and
/etc/apache2/sites-enabled/index.html

Its true though. The only thing that goes in site-available is config files.

First, of all there are two major things wrong you did with the setup (munky99999):

1. Never allow the /var/www/ files to be 0777. At the very least do 0775, and even less if you can get away with it.

2. Never ever use your root account in MySQL to access your databases in applications. Make a new user for each app you want to use and a new database. Only allow that user to access the database.

But, other than that. Your setup is actually just fine. Ubuntu's LAMP is actually very secure by default. The thing is you made it less secure by the changes you made.

Also, /etc/apache2/sites-available/ is ONLY FOR CONFIG!!! IDK, how you got an index.html. But get rid of it. Post your apache2.conf and httpd.conf files so I can help you with the problem.

---

### Post by munky99999 on 2009-12-08
> First, of all there are two major things wrong you did with the setup (munky99999):

1. Never allow the /var/www/ files to be 0777. At the very least do 0775, and even less if you can get away with it.
Actually 777 is necessary for the original installation done by wordpress through the wp-admin/install one. Basically it's writing files with no user at all.

At least that's what I discovered when I did it. Might have been just quirky. Though it does the exact same thing for fedora 12; afaik.

> . Never ever use your root account in MySQL to access your databases in applications. Make a new user for each app you want to use and a new database. Only allow that user to access the database.
Ya. So true. 

There are a few other things that should be done. Just trying out thunderbird 3 though atm. So I'll leave you with that.

---

### Post by HighCommander540 on 2009-12-08
> **munky99999 said:**
> Actually 777 is necessary for the original installation done by wordpress through the wp-admin/install one. Basically it's writing files with no user at all.

At least that's what I discovered when I did it. Might have been just quirky. Though it does the exact same thing for fedora 12; afaik.


Then you are doing something wrong, because a webserver should never have anything more than read for everyone. And if you can get away with it, (like you are the only one that will ever use it) it shouldn't even allow read or write by anything but the owner (www-data).

If you actually go and read the good LAMP tutorials (like the one's Ubuntu set-up) they will all tell you this same thing.
> **munky99999 said:**
> 
Ya. So true. 

There are a few other things that should be done. Just trying out thunderbird 3 though atm. So I'll leave you with that.

Hell yes, on the MySQL. And if you think there are other things what are they? Because I have read most security tutorials and done some of my own security measures. And really there isn't much else you need to do. Unless you want to add SSL or basic authentication to certain directories.

---

### Post by apel_2804 on 2009-12-09
For wordpress you need to set the owner to apache in case you want to edit the wordpress files from the webinterface (as you need to when using build in installation script).

```
# sudo chown -R www-data:www-data /xxx/xxx/wordpress
```

What I did, I configured an extra "site" for wordpress:

```
# nano /etc/apache2/sites-available/wordpress

Alias /blog /usr/share/wordpress

<Directory /usr/share/wordpress>
  Options FollowSymLinks
  AllowOverride Limit
  <IfModule mod_dir.c>
    DirectoryIndex index.php
  </IfModule>
</Directory>
```

And located the files not in the www root /var/www but in an extra folder under /usr/share/wordpress as it would an extra application.

You then have to activate the "site" config file with:

```
# sudo a2ensite wordpress
# sudo /etc/init.d/apache2 restart
```

---

### Post by g_lev on 2009-12-09
Thank you all,
apache2 is working now and I've changed the relevant folders permissions.
the thing is that I don't know how to set a database without phpmyadmin.
in the package manager I have phpmyadmin but I don't know how to access it.

---

### Post by apel_2804 on 2009-12-09
If you want to install it:

```
sudo aptitude install phpmyadmin
```

If it's installed just open it:

[http://your.domain/phpmyadmin](http://your.domain/phpmyadmin)

It's configured in:

```
/etc/apache2/conf.d/phpmyadmin.conf
```

---

### Post by g_lev on 2009-12-09
> **apel_2804 said:**
> Hm, just open it:

[http://your.domain/phpmyadmin](http://your.domain/phpmyadmin)

It's configured under:

```
cat /etc/apache2/conf.d/phpmyadmin.conf 
```

I tried [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) but doesn't work.
I have no file named phpmyadmin.conf under that directory.

---

### Post by apel_2804 on 2009-12-09
Is it actually installed?

```
sudo aptitude install phpmyadmin
```

---

### Post by g_lev on 2009-12-09
> **apel_2804 said:**
> Is it actually installed?

```
sudo aptitude install phpmyadmin
```

yes

> 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


---

### Post by g_lev on 2009-12-09
OK this is what I did 
I searched my HD for the phpmyadmin folder which was located on usr > share > phpmyadmin and copied it into the www folder.
now everything is running ok.

Thank you all for all your help : )

---

### Post by apel_2804 on 2009-12-09
Yes this will work, but it isn't nice.

You can use a symlink instead of copying the files:

```
sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin
```

I don't get why it looks so different. What version of Ubuntu are you using?

It should run out of box. And there should be config file in /etc/apache2/conf.d/phpmyadmin.conf.

Actually in that config file is the information where phpmyadmin is located so that you don't need to copy or linking anything anywhere.

---

