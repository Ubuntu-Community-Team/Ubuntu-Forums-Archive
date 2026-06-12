---
title: "http://localhost is downloading the index.php files as PHTML"
date: 2006-05-29
forum: Server Platforms
---

### Post by Isoss on 2006-05-29
I have  apache2, php4, mysql-client, mysql-server, libapache2-mod-php4, libapache2-mod-auth-mysql, php4-mysql, phpmyadmin installed.

They used to work fine, but suddenly - after downloading some stuff with synaptic - mysql stopped working ... I removed all these ackages and reinstalled the:
```
 sudo apt-get install apache2 php4 mysql-client mysql-server libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin
```

Now when I go to [http://localhost](http://localhost) and choose a site folder, if it's index.html it works, otherwise, if it's PHP it downloads the file as a PHTML file!!!

I can't display any of the PHP websites!!!

Please help!

---

### Post by oly on 2006-05-30
open up the apache2.conf file and search for .php you will most likely find a line commented out uncomment it and stop and restart the apache service.

hopefully will sort your problem

---

### Post by Isoss on 2006-05-30
Ok, I purged  everything related to php and apache and then reinstalled the whole thing. Now it's working except that it can't read the database! it's giving this error:
```
Fatal error: Call to undefined function: mysql_connect() in /var/www/Under Construction/Nourelalam.org/includes/header.inc.php on line 19
```

I went to header,inc.pho and commented the config scripts:
```
//MYSQL_CONNECT($server, $user, $pass);

//MYSQL_SELECT_DB($db);
```
Now the page works fine expect that the data are not shown of course.

What have I missed?
I have the following mysql-related packages installed:
libapace2-mod-auth-mysql 
libmysqlclient12
libmysqlclient14
mysql-client
mysql-common
mysql-server
php4-mysql
and Phpmyadmin ofcourse which works fine and is showing all the data

there are some related packages installed as well but not for webservers, like python and perl and other stuff.

I dounbt these packages: libmysqlclient12 and libmysqlclient14 but I can't remove them cuz they are dependencies for kubuntu-desktop and some other needed packages.

So please help!

---

### Post by Isoss on 2006-05-30
I think it's a php package problem! although I have php4-mysql installed!!

Any clue?

---

### Post by linuxone on 2006-05-30
Hi,

[QUOTE=Isoss]```
Fatal error: ... [color=red]/var/www/Under Construction/Nourelalam.org/includes/header.inc.php[/color] on line 19
```[/QUOTE]

first rule for a UNIX web server: **No spaces** in folder or file names! (to complete this rule: and all names were case sensitive)

> and Phpmyadmin ofcourse which works fine and is showing all the data

if the PHP scripts from phpMyAdmin really works fine and you can access the MySQL database via phpMyAdmin without problems, your problems were neither PHP nor MySQL related.

It may depend on the illegal folder name (no space!!) or maybe on a config problem into apache OR the related PHP application (Nourelalam.org)?

> I dounbt these packages: libmysqlclient12 and libmysqlclient14 but I can't remove them cuz they are dependencies for kubuntu-desktop and some other needed packages.

it causes no problems to keep both libraries.

Thomas

---

### Post by Isoss on 2006-05-30
Thanks Thomas, but concerning the space in the folder it was working fine before on linux! I've been developing that site for almost a month on ubuntu so I don't think that's the problem

yes Phpmyadmin works fine as PHP and MYsql but in my site php works only if I comment all mysql scripts like mysql_connect, mysql_query, mysql_fetch_assoc and all of these stuff ...

could be an apache problem!? looks like this web application is not able to interpret or compile php and mysql?

---

### Post by Isoss on 2006-05-31
Alright, this is too much! I reinstalled ubuntu and then ran this command:
```
 sudo apt-get install apache2 php5 mysql-client mysql-server libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql phpmyadmin
```
Now it's the same mysql problem!!!

I opened PHPMYADMIN and it works fine exept that creating a new database is not permitted! in other words it's telling me No privileges!!!
check it out:
[IMG]http://nourelalam.com/Isos/phpmyadmin.gif[/IMG]

---

### Post by uglysmurf on 2006-06-04
I'm having similar problems with apache2 and php5 (no mysql), and posted to another thread if you're interested: [http://www.ubuntuforums.org/showthread.php?t=188017&highlight=phtml](http://www.ubuntuforums.org/showthread.php?t=188017&highlight=phtml)

I'm still not sure what's causing the behavior I'm seeing...

[EDIT] Cleared my browser's cache on my client browser and the php is displaying as expected...hope this helps.

---

### Post by Isoss on 2006-06-04
Actually, after I've had this problem, I just went working with my other stuff and then I opened the phpmyadmin again and the problem was gone ( is my laptop demon-possesed or something? ) I dunno what happened it just didn't appear again and I've been able to create databases and develop my websites ever since!

Anyway, maybe I've done something by chance that fixed the problem, I don't remember if I cleared the chache or not but anyway the problem is gone. I wish I'd known the problem and the cause to avoid it in the future, but thank God I am no longer ancountering any problem.

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=Isoss]Now it's the same mysql problem!!!

I opened PHPMYADMIN and it works fine exept that creating a new database is not permitted! in other words it's telling me No privileges!!!
check it out:[/QUOTE]

this is no "problem" but **only a security and configuration issue**. Please read the phpMyAdmin install manual and configure phpMyAdmin correctly. See the red colored hint at the screen dump bottom.

Thomas

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=Isoss]Thanks Thomas, but concerning the space in the folder it was working fine before on linux! I've been developing that site for almost a month on ubuntu so I don't think that's the problem[/QUOTE]

into the UNIX world a space is a separator and not a legal char for names. Space is NOT becoming a legal file/folder name char because a big software company does use it in that kind. Anyway, this does happen in a completly other world of operating system but not in the UNIX world.

Comparing OS features you can use spaces anywhere and char's were NOT case sensitive into the flying glases system. Into the real UNIX world a space keeps a separator and char's are case sensitive.

Thomas

---

### Post by mitticus on 2006-07-06
Just had same problem.

The issue arose because of a dependency installing php4.

I reinstalled php5 but it doesnt create the symlinks in /etc/apache2/mods-enabled. You must do it manually.

you must create them and restart:

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/php5* .
sudo rm php4*



hope this helps someone : took me ages to find.

---

### Post by az on 2006-07-06
[QUOTE=mitticus]Just had same problem.

The issue arose because of a dependency installing php4.

I reinstalled php5 but it doesnt create the symlinks in /etc/apache2/mods-enabled. You must do it manually.

you must create them and restart:

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/php5* .
sudo rm php4*



hope this helps someone : took me ages to find.[/QUOTE]

Don't create the symlinks, use a2enmod:

sudo a2enmod php5

The php4 link should no longer be there!

The mod is enabled by default as you install the package.  It gets removed if you downgrade to php4.

---

### Post by c_lbnc on 2006-10-04
> **uglysmurf said:**
> I'm having similar problems with apache2 and php5 (no mysql), and posted to another thread if you're interested: [http://www.ubuntuforums.org/showthread.php?t=188017&highlight=phtml](http://www.ubuntuforums.org/showthread.php?t=188017&highlight=phtml)

I'm still not sure what's causing the behavior I'm seeing...

[EDIT] Cleared my browser's cache on my client browser and the php is displaying as expected...hope this helps.

Thank you for this! I was having the same problem and losing my mind. I cleared my browser cache and all is fine now. :D

---

