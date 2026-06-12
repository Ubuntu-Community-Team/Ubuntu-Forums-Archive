---
title: "PHP extension won't work"
date: 2011-03-27
forum: Server Platforms
---

### Post by Tuumke on 2011-03-27
Hi there,

I'm going in a nerd rage over here, since i've been trying to get a LAMP server up and running.

**The problem**
When trying to open a php page, it want's to save a file.
After some tweaking to apache, i got it to "show", but it was only plain tekst.

**What i've tried**
*- Searching google for different solutions.*
What i can remember of the solutions:

[LIST]
[*]Adding php to the mimetypes
[*]using apt-get install apache2 php5
[*]reinstalling apache2 and php5
[*]removing mysql, apache2, php5 and using tasksel to install LAMP
[*]chanching mimetype extension from php to .php (makes it as a txt page instead of the file wanting to save)
[/LIST]
None of these solutions seem to get it to work.
Im all out of ideas. You got any?

---

### Post by BkkBonanza on 2011-03-27
You need to make sure the correct AddHandler config lien is present so Apache knows it needs to "handle" the file and not send it. "Handle" meaning it should give it to php interpreter.

AddHandler application/x-httpd-php .php

But this usually already set by default IIRC. 

You may also want below if you have a default that is php.

DirectoryIndex index.php

grep your config files and make sure these lines are in suitable place and not overridden somewhere.

You don't want it set as a mime-type since php files are not supposed to ever get sent to the client.

---

### Post by Tuumke on 2011-05-31
How do i grep the config files?

---

### Post by cpt_power on 2011-05-31
grep <text> <file>

So, in this case you'd write something to the effect of:

```
grep DirectoryIndex /etc/apache2/mods-available/dir.conf
```

or, to check everything under a folder just go with:

```
grep -R DirectoryIndex /etc/apache2/
```

---

### Post by SeijiSensei on 2011-05-31
> **BkkBonanza said:**
> But this usually already set by default IIRC.

This question gets asked so regularly lately that it has made me wonder whether it actually is being set up correctly by default.

As someone who runs CentOS for servers, I can't speak to Ubuntu here, but I've never had this issue when setting up a server using RedHat or CentOS.  Any ideas why this has become problematic on Ubuntu?

Surely if I install PHP5 and Apache I should expect the AddHandler directive to be set correctly without any further effort on my part.  From the questions posed here lately that doesn't seem to be the case.

---

### Post by Tuumke on 2011-06-13
> **cpt_power said:**
> grep <text> <file>

So, in this case you'd write something to the effect of:

```
grep DirectoryIndex /etc/apache2/mods-available/dir.conf
```or, to check everything under a folder just go with:

```
grep -R DirectoryIndex /etc/apache2/
```

```
tijmen@quwquw:/etc/apache2$ sudo grep -R DirectoryIndex /etc/apache2
/etc/apache2/mods-enabled/dir.conf:          DirectoryIndex index.html index.cgi                                                                                                                                index.pl index.php index.xhtml index.htm
/etc/apache2/mods-enabled/userdir.conf:         DirectoryIndex index.html index.                                                                                                                               php
/etc/apache2/mods-available/dir.conf:          DirectoryIndex index.html index.c                                                                                                                               gi index.pl index.php index.xhtml index.htm
/etc/apache2/mods-available/userdir.conf:               DirectoryIndex index.htm                                                                                                                               l index.php
tijmen@quwquw:/etc/apache2$ sudo grep -R .php /etc/apache2
/etc/apache2/sites-available/default-ssl:       <FilesMatch "\.(cgi|shtml|phtml|php)$">
/etc/apache2/mods-enabled/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
/etc/apache2/mods-enabled/userdir.conf:         DirectoryIndex index.html index.php
/etc/apache2/mods-available/dir.conf:          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
/etc/apache2/mods-available/userdir.conf:               DirectoryIndex index.html index.php
tijmen@quwquw:/etc/apache2$

```

---

### Post by BkkBonanza on 2011-06-13
It appears you have no AddHandler present. Try greping for that in particular.
If there is no AddHandler for php then as far as I recall it doesn't get handled so you would want to add that. 

The DirectoryIndex is a bit different. It tells apache that if a directory is requested without a file then use this name as the "default". So if you have index.html then it looks for that but if you have a default file index.php then you will want that file, not index.html, to be the default.

You can put these lines in a site conf file but I'd say it's better in a conf file that gets picked up by all sites, since generally speaking these actions are not usually site specific. 

As far as whether these are getting set by the default install - I don't know. I usually do manual Nginx installs nowadays so I'm no longer familiar with the repo based Apache/PHP install process. I'd have to agree that a lot of people keep asking these same questions so it is a bit odd.

---

### Post by Tuumke on 2011-06-24
wth....
when i do:
/etc/init.d/apache2 stop
it says stopping...
Then i do:
sudo apt-get remove apache2
press the J
and it says removed....
but when i do /etc/init.d/apache2 start, it starts again? :O

---

### Post by SeijiSensei on 2011-06-25
> **SeijiSensei said:**
> This question gets asked so regularly lately that it has made me wonder whether it actually is being set up correctly by default.

I set up a new Ubuntu Server 10.04.2 installation last night and had no problem with PHP files being interpreted rather than downloaded, so I'm at a loss to understand why so many people are having this problem.

---

### Post by mandza on 2011-06-27
i have a same problem.
i had redirect my server from var/www to home/user/public_html
but now i can't run .php it is downloading it. but html work fine.

---

### Post by mandza on 2011-06-28
my problem was solved here: [http://ubuntuforums.org/showthread.php?t=1778684]("http://ubuntuforums.org/showthread.php?t=1778684")

if not work control if php5 and libapache2-mod-php5 is installed.
for instalation sudo apt-get install php5 libapache2-mod-php5
and for mysql connection install php5-mysql.

---

### Post by HideoV on 2011-07-26
Same problem here. Solved (I hope) adding
```
AddHandler application/x-httpd-php .php
```
(which works also with .php3) to
```
/etc/apache2/mods-enabled/mime.conf
```

---

### Post by SeijiSensei on 2011-07-27
I'm guessing that people trying to set this up after installation fail to install libapache2-mod-php5 thinking they need only the apache2 and php5 packages.  libapache2-mod-php5 contains /etc/apache2/mods-available/php5.conf which includes the relevant SetHandler directive that tells Apache to use the PHP module to interpret .php files.

---

