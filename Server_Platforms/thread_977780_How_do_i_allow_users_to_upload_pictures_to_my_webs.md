---
title: "How do i allow users to upload pictures to my website"
date: 2008-11-10
forum: Server Platforms
---

### Post by Fertech on 2008-11-10
do i need /cgi-bin dir cause i don't see it, or what do i need.

---

### Post by rustutzman on 2008-11-10
There are lots of PHP based solutions. Also you might want to look into a CMS like Joomla. CGI-BIN will work but if you're already running Linux why not go with what you already have.

I'm using LinPHA on a couple of my sites.

Russ

---

### Post by Coreigh on 2008-11-10
Are you hosting the site or do you have the site hosted somewhere in the internet? If you have someone hosting for you they may have tools or applets available for you to use, or they may not allow uploads. If they don't offer the tools or you are hosting one your own server you will need to use some thing of your own liking. As rustutzman suggested it is easiest to use something pre-built and customize it to your liking. For web sites Joomla is very popular and widely supported with community help and lots of books and online documentation.

---

### Post by cariboo on 2008-11-10
FYI cgi-bin is located in /usr/lib/cgi-bin

Jim

---

### Post by Fertech on 2008-11-10
ok rustutzman and cariboo907 i will look into that. so in the form i have to type <form method=post action="/usr/lib/cgi-bin/what about this part the .pl do i created a perl script  or do i just put something like upload.pl, i don't really get that part.

or do i type in "/cgi-bin/upload.pl"

---

### Post by Fertech on 2008-11-10
where and how do i download Linpha, in what dir do i save it in?

---

### Post by Fertech on 2008-11-10
i download this file on my desktop is this the right file zip linpha-1.3.4.tar.gz can some one help uncompress it to the right dir

---

### Post by volkswagner on 2008-11-10
This just caught my eye.  Looks cool.

I followed these directions

[http://linpha.sourceforge.net/wiki/index.php/Installation]("http://linpha.sourceforge.net/wiki/index.php/Installation")

I first created another virtual hosts.  I am using named based virtual hosts.  Depending how you have apache setup, will depend where you want to extract the install.  Some use the default /var/www.

The extract command is given in the directions.

Make sure you change the file permissions as in the directions.  Also make sure you chmod the group to www-data.

For me I did as follows.

```
tar xvfz /home/user/myhostdirectory/linpha-1.3.4.tar.gz
```

I am no expert on security so I will not give advice and setting the group permissions. 

Hope this helps get you started

---

### Post by rustutzman on 2008-11-10
Sorry fertech, been away from the computer for a while. Did you get this setup following the directions listed? 

Russ

---

### Post by Fertech on 2008-11-10
ok Linpha is install and i try to what is said. but fail, the links said to point my browser to [http://hostname/linpha](http://hostname/linpha) and follow the instruction there, but i get an error. page no found. Is there something im missing. also how do i know it's up and running.

---

### Post by Philio on 2008-11-11
Did you go to [http://hostname/linpha](http://hostname/linpha) or did you change it to your domain name, eg: [http://www.somedomain.com/linpha](http://www.somedomain.com/linpha)

---

### Post by rustutzman on 2008-11-11
When you extracted linpha to your www directory did you rename the directory to just linpha or is named linpha-1.3.4?

Russ

---

### Post by Fertech on 2008-11-11
i type [http://fertech.ath.cx/linpha](http://fertech.ath.cx/linpha) i never rename the dir, all i did was this code in the terminal tar xvfz /home/user/myhostdirectory/linpha-1.3.4.tar.g  and a folder after i did that, there was a folder in my desktop

---

### Post by Fertech on 2008-11-11
ok i change the dir and it work. I never hear if this Linpha. i don't know if this is what im looking for, i want my user to uploap pic to my server. you know like myspace. i upload pic to tom's server. let me know is this linpha is what im looking for and if you can get me the html code form.

---

### Post by Fertech on 2008-11-11
INSTALLATION ABORTED !!! magick and gd missing where and how do i download them. and where should i save them. if i need to rename a dir let me know too.

---

### Post by cpetercarter on 2008-11-11
gd is, I guess, the gd php extension which is needed for image manipulation, and magick is a programme called imagemagick which is used to manipulate image formats. They are both in the repositories.

> sudo apt-get install php5-gd 

sudo apt-get install imagemagick

---

### Post by Fertech on 2008-11-11
ok i install them but i got this error now.
Trying to connect Database Server-->
Warning: mysql_connect() [function.mysql-connect]: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) in /var/www/linpha/install/forth_stage_install.php on line 104
Error while trying to connect Database Server, using:
localhost
3306
root
linpha

---

### Post by rustutzman on 2008-11-12
Probably a password issue. Make sure you have the right password for root in MySQL and try it again. If you have phpMyAdmin try getting in MySQL with it. Should be the same password you need for this.

Russ

---

### Post by Fertech on 2008-11-12
i dont think i ever setup mysql with a password how can i view the password or reset it. also how can i access mysql.

---

### Post by rustutzman on 2008-11-12
You can try calling it from the command line. you'll have to do a --help or man to see the commands as I don't have access to my server right now.

You probably should install phpmyadmin from sourceforge.net if your going to be using mysql.

Russ

---

### Post by Fertech on 2008-11-21
ok i download phpmyadmin and extracted to my desktop, what dir do i put it in.

---

### Post by Fertech on 2009-01-04
i got this error how do i increase the memory_limit in php.ini

Hmmh, your PHP memory limit is <=16MB. If you encounter problems with missing thumbnails, try to increase the memory_limit in php.ini or resize your pictures to a lower resolution and try again.

---

### Post by Fertech on 2009-01-04
new error i got, what does this means.

Trying to connect Database Server-->
Fatal error: Call to undefined function sqlite_open() in /var/www/linpha/install/forth_stage_install.php on line 135

---

### Post by spiderbatdad on 2009-01-04
I use a very simple program called filethingie which consists of a simple php program file placed in the directories where I would like file uploading to be possible. It depends on php.ini file for configuration.

[http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)

---

### Post by Fertech on 2009-01-04
im not looking for  different software. if i keep on switching software i will never get this done. just looking to correct this error.

---

