---
title: "Problem to launch my PHP files in Firefox."
date: 2011-05-06
forum: Server Platforms
---

### Post by Limada on 2011-05-06
Hi everybody.

Happy to bother you again. :)

My problem is that I can' t launch my PHP files in Firefox to see them local.

I have Apache, PHP and MySQL installed.

I also moved my web folder to /var/www but still can't see them.

I can see the default html file: "It works!" but not my files.

Firefox is still asking what it should do with the file, if it should open or save it. But I can't see them.

Hope some web developer or a shell genius can tell me what to do :)

THanks in advance.

---

### Post by memilanuk on 2011-05-20
Dunno if you got this worked out or not...  I had the same problem with a fresh install of 11.04, though I didn't remember any such problem with 10.04.  Apparently one of the updates to 10.04 implemented this nasty little change somewhat silently...

[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-virtual-hosts-php-config.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-virtual-hosts-php-config.file)

[https://wiki.ubuntu.com/UserDirectoryPHP](https://wiki.ubuntu.com/UserDirectoryPHP)

HTH,

Monte

---

### Post by nsnidanko on 2011-05-20
Hi Limanda,
 
Looks like you didn't install php or it is not properly configured (such as didn't restart apache2 service after intallation). Follow this guide to install it:
 
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
 
and than create a test.php in the /var/www directory with the following content:
 
<? phpinfo(); ?>
 
Hope it helps,
Naz

---

### Post by memilanuk on 2011-05-20
Naz,

You must not have read the links I posted...

There is not necessarily *anything* wrong with the install Limanda has... there was nothing wrong with the install *I* had.  Starting sometime in 10.04, there are specific lines added in /etc/apache2/mods-enabled/php5.conf that *disable* php in files located in /home/*/public_html.  Unless you go in and intentionally comment out/ delete those lines, apache will not run php files in user home directories.

Now... if Limanda is still having problem viewing them in /var/www... that might be an install problem.  I had it working 'right' and then had to re-install the system (for other reasons) and for whatever reason tasksel installed apache2, mysql-server, libapache2-mod-whatever, phpmysql, etc. but *not* php5...?  Took me a bit to get that figured out, but once I got everything installed (and per-user php re-enabled), it worked just fine.

Monte

---

