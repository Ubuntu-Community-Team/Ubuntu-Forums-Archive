---
title: "&quot;Your apache2 configuration is broken...&quot;"
date: 2011-01-27
forum: Server Platforms
---

### Post by memilanuk on 2011-01-27
So... relatively fresh (last night) install of Ubuntu 10.04 LTS, fully updated.  Used tasksel during install to select LAMP server, Postgresql server, file server, ssh server as this is a general purpose 'training' box for my own education, nothing more.

Installed phpmyadmin, and checked that I can get to [http://local.ip.address](http://local.ip.address) on the land, as well as [http://local.ip.address/phpmyadmin](http://local.ip.address/phpmyadmin) and log in.  Yay.

Then I went to install phppgadmin, and at the end of the installation I get the following error:

```

monte@oobun2:~$ sudo apt-get install phppgadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  php5-pgsql
Suggested packages:
  slony1-bin
The following NEW packages will be installed:
  php5-pgsql phppgadmin
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 946kB of archives.
After this operation, 5,485kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main php5-pgsql 5.3.2-1ubuntu4.7 [52.0kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/universe phppgadmin 4.2.2-1ubuntu1 [894kB]
Fetched 946kB in 4s (225kB/s)     
Selecting previously deselected package php5-pgsql.
(Reading database ... 47579 files and directories currently installed.)
Unpacking php5-pgsql (from .../php5-pgsql_5.3.2-1ubuntu4.7_i386.deb) ...
Selecting previously deselected package phppgadmin.
Unpacking phppgadmin (from .../phppgadmin_4.2.2-1ubuntu1_all.deb) ...
Processing triggers for libapache2-mod-php5 ...
[COLOR="Red"]Your apache2 configuration is broken, so we're not restarting it for you.[/COLOR]
Setting up php5-pgsql (5.3.2-1ubuntu4.7) ...
Setting up phppgadmin (4.2.2-1ubuntu1) ...
 * Reloading web server config apache2                                   [ OK ] 

monte@oobun2:~$ 


```


And no access to phppgadmin @ [http://local.ip.address/phppgadmin](http://local.ip.address/phppgadmin)

Any ideas?

---

### Post by weedeater64 on 2011-01-27
Check 

```
cat etc/apache2/apache2.conf
```

and look for 

Include /etc/phpmyadmin/apache.conf

I'm running Debian, and just last week figured out that I needed to add that line to that file.

---

### Post by wongo888 on 2011-01-27
You might try:

```
$ apache2ctl configtest
```

And try to work out where the error is occurring.

---

### Post by memilanuk on 2011-01-27
```

monte@oobun2:~$ sudo apache2ctl configtest
[sudo] password for monte: 
Syntax OK
monte@oobun2:~$ 

```

---

### Post by wongo888 on 2011-01-27
Ok, I installed this on a spare VM and it reported the same error. Strangely, once I tweaked the config file it worked:

```
/etc/apache2/conf.d$ cat phppgadmin 
Alias /phppgadmin /usr/share/phppgadmin/

<Directory /usr/share/phppgadmin/>

DirectoryIndex index.php

Options +FollowSymLinks
AllowOverride None

order deny,allow
#deny from all
#allow from 127.0.0.0/255.0.0.0 ::1/128
allow from all

<IfModule mod_php5.c>
  php_flag magic_quotes_gpc Off
  php_flag track_vars On
  php_value include_path .
</IfModule>

</Directory>

```

By default, it only allows connections from localhost. Change the order directives and it loads the login page. I didn't bother to set up the users or anything, but at least it gets that far.

---

### Post by shyamjoshi on 2011-10-17
It  will have worked in Jan recently i had a new problem . 

The real problem is that current version of PGSQL server is 8.4 and phppgadmin is not realeased for this server version on top , there is no new php release which supports the php-pgsql plugin yet so one has to downgrade the php version.

That is what happened with you and hence you ended up breaking your php install .

i blogged about it you can read it here 

[http://shyam-techblog.blogspot.com/2011/08/installing-phppgadmin.html](http://shyam-techblog.blogspot.com/2011/08/installing-phppgadmin.html)

best of luck :popcorn:

---

