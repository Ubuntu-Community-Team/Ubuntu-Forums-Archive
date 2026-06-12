---
title: "MySQL Wordpress website on localhost - no content"
date: 2012-08-30
forum: Server Platforms
---

### Post by aryangor on 2012-08-30
Hello!

I want to host my Wordpress site on my PC for sandbox editing. But the MySQL database seems to have errors when connecting localhost and the website database.

I have installed Apache and Wordpress, as was shown in this guide:
[http://www.wpwebhost.com/install-wordpress-in-ubuntu-12-04-lts-localhost-lampp-server/](http://www.wpwebhost.com/install-wordpress-in-ubuntu-12-04-lts-localhost-lampp-server/)

This guide shows how to create a new Wordpress site with a clean MySQL database. Everything works well up unlit here - the dummy website displays on [http://localhost/wordpress](http://localhost/wordpress).

When I try to import the .sql file downloaded from my website into MySql, it does not display any content. Perhaps I do not link the server and the database properly. Has anyone encountered a similar problem before?

Also I apologize if I have posted in a wrong section.

---

### Post by Habitual on 2012-08-30
> **aryangor said:**
> ...When I try to import the .sql file downloaded from my website into MySql, it does not display any content. Perhaps I do not link the server and the database properly. Has anyone encountered a similar problem before?...

Sorta remember WP likes hostname-based resolution, so, if the import.sql file came from domain.com and you want to import that into example.net, you may see an issue like this.

How was this import done exactly?

```
mysql -uroot -p <db> < /path/to/file.sql
```
check wp-config.php file on the server for MySQL username/password/db and substitute -uroot for the indicated user/pass/db in wp-config.php

Connect with those credentials using a terminal >
```
mysql -u<user> -p 
``` and then ```
show databases;
```
If your db does NOT show up, then you have a problem.

Let us know....

---

### Post by aryangor on 2012-08-31
Hey, thanks for your reply!

> **Habitual said:**
> 
How was this import done exactly?

```
mysql -uroot -p <db> < /path/to/file.sql
```


Yes, that's how I imported the .sql database file. If I log in as 
```
mysql -uroot -p
```
and view the list of databases, then the desired import.sql database is there on the list, along with the default wordpress.sql database.


> **Habitual said:**
> 
check wp-config.php file on the server for MySQL username/password/db and substitute -uroot for the indicated user/pass/db in wp-config.php



I have a feeling this is where the problem lies - here or with the database itself. 

Looking at wp-config.php, I find the following line:
```
define('DB_NAME', 'wordpress');

/** MySQL database username */
define('DB_USER', 'root');

/** MySQL database password */
define('DB_PASSWORD', 'password');

/** MySQL hostname */
define('DB_HOST', 'localhost');
```

The DB_NAME value is 'wordpress' - this is the default one of the dummy Wordpress website, which is also an existing MySql database. When DB_NAME value is 'wordpress', my browser shows the dummy website at 'localhost/wordpress' just fine. When I change DB_NAME to 'import', as it appears on the list of databases, it takes me to my website on the web, and there it gives a 404 error.

The name 'wordpress' in 'localhost/wordpress' is the name of the folder which apache2 reads, and it contains wp-config.php and other files that I downloaded from my website.

---

### Post by Habitual on 2012-08-31
> **aryangor said:**
> ...
```
define('DB_NAME', 'wordpress');

/** MySQL database username */
define('DB_USER', 'root');

/** MySQL database password */
define('DB_PASSWORD', 'password');

/** MySQL hostname */
define('DB_HOST', 'localhost');
```
This is MOST insecure and NOT [The Way]("http://codex.wordpress.org/Installing_WordPress").

The DB_NAME value is 'wordpress' - this is the default one of the dummy 

> **aryangor said:**
> ...When I change DB_NAME to 'import'...

why?

typically, I'd create a wpinstall_user or some such with
```
mysql > create database mywp; 
mysql > grant all privileges on mywp.* to wpinstaller@`localhost` identified by 'password'; 
flush privileges; 
exit; 
```then test it with 
```
mysql -uwpinstaller -p -e "show databases;"
```you should 'see' mywp

use these for wp-config.php
```
define('DB_NAME', 'mywp');

/** MySQL database username */
define('DB_USER', 'wpinstaller');

/** MySQL database password */
define('DB_PASSWORD', 'password');

/** MySQL hostname */
define('DB_HOST', 'localhost');
```

---

### Post by aryangor on 2012-08-31
> **Habitual said:**
> 
typically, I'd create a wpinstall_user or some such with
```
mysql > create database mywp; 
mysql > grant all privileges on mywp.* to wpinstaller@`localhost` identified by 'password'; 
flush privileges; 
exit; 
```then test it with 
```
mysql -uwpinstaller -p -e "show databases;"
```you should 'see' mywp

use these for wp-config.php
```
define('DB_NAME', 'mywp');

/** MySQL database username */
define('DB_USER', 'wpinstaller');

/** MySQL database password */
define('DB_PASSWORD', 'password');

/** MySQL hostname */
define('DB_HOST', 'localhost');
```

Awesome, thanks for the tip! I did this the way you suggested.

I have some progress now. localhost/mywp shows the website, but incompletely. Apparently, all plugins are there, but deactivated. And all pages, posts and widgets are not appearing.

---

### Post by aryangor on 2012-08-31
> **aryangor said:**
> When I change DB_NAME to 'import', as it appears on the list of databases, it takes me to my website on the web, and there it gives a 404 error.

I am back to this error. I don't understand why it takes me to [www.mywebsite.com](www.mywebsite.com) when I type localhost/database...

---

### Post by sandyd on 2012-08-31
/methinks your wordpress URL is wrong in MySQL.

Take a read of [http://codex.wordpress.org/Changing_The_Site_URL](http://codex.wordpress.org/Changing_The_Site_URL)

I personally like the MySQL method ([http://codex.wordpress.org/Changing_The_Site_URL#Changing_the_URL_directly_in_the_database](http://codex.wordpress.org/Changing_The_Site_URL#Changing_the_URL_directly_in_the_database)), but thats just me.

Change the url to [http://localhost/mywp](http://localhost/mywp)

---

### Post by Habitual on 2012-08-31
> **aryangor said:**
> I am back to this error. I don't understand why it takes me to [www.mywebsite.com]("http://www.mywebsite.com") when I type localhost/database...

as I said "if the import.sql file came from domain.com and you want to import that into example.net, you may see an issue like this."...

Thanks sandyd!

---

### Post by aryangor on 2012-09-05
> **sandyd said:**
> /methinks your wordpress URL is wrong in MySQL.

Take a read of [http://codex.wordpress.org/Changing_The_Site_URL](http://codex.wordpress.org/Changing_The_Site_URL)

I personally like the MySQL method ([http://codex.wordpress.org/Changing_The_Site_URL#Changing_the_URL_directly_in_the_database](http://codex.wordpress.org/Changing_The_Site_URL#Changing_the_URL_directly_in_the_database)), but thats just me.

Change the url to [http://localhost/mywp](http://localhost/mywp)

Sorry about the late reply! :(

Thanks, *sandyd* and *Habitual*! I have used the above-quoted link to change the URL and now everything works fine! Have a blesssed day!

---

### Post by Habitual on 2012-09-05
So glad you worked it out!

Have a Great Day also!

---

