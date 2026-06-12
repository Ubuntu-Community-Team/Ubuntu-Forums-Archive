---
title: "MySQL and PHP4 install woes"
date: 2005-05-21
forum: Server Platforms
---

### Post by wildscribe on 2005-05-21
Hi Folks, 

Got two questions that I was hoping you could help me out with. I am a complete newbie to Debian and Ubuntu.

I am having problems getting MySQL to work with PHP4. I keep getting the error message:

*Fatal error: Call to undefined function: mysql_connect() in /var/www/mysql_up.php on line 12*

(Note that mysql_up.php is a script that I am using to test the connection between PHP and MySQL.) 

I did some research and found that I needed to have php4-mysql installed for it to work, but when I ran “sudo apt-get install php4-mysql” I kept getting the package not found message.

Has the php4-mysql package been renamed? Or is there another way that I can get MySQL to work with PHP? I am thinking about uninstalling and reinstalling PHP, but I am sure there is a better way.

My second question is how do I upgrade programs. I would like to upgrade to PHP5 from PHP4 and I would also like to upgrade to MySQL 4.1 from MySQL 4.0

Any and all help is appreciated. 

- - - - Wild

---

### Post by jdonnell on 2005-05-22
Are you using hoary or warty? 

You can find packages with the 'apt-cache search' command as follows.

```
apt-cache search mysql
```

I see the following in the output of that command
```

mysql-client-4.1 - mysql database client binaries
mysql-common-4.1 - mysql database common files (e.g. /etc/mysql/my.cnf)
mysql-navigator - GUI client program for MySQL database server
mysql-query-browser - Official GUI tool to query MySQL database
mysql-query-browser-common - Architecture independent files for MySQL Query Browser
mysql-server-4.1 - mysql database server binaries

```

Once you find the package you want you can use
```
sudo apt-get install mysql-server-4.1
```

There isn't a php5 package for ubuntu yet, but installing from source is painless. You can find some ubuntu specific instructions at
[http://www.ubuntulinux.org/wiki/PHP5FromSource](http://www.ubuntulinux.org/wiki/PHP5FromSource)
and
[http://www.ubuntulinux.org/wiki/PHP5Installation](http://www.ubuntulinux.org/wiki/PHP5Installation)

If you want to stick with php4 you'll need to install the php4-mysql package to use mysql
```
sudo apt-get install php4-mysql
```

---

### Post by LordHunter317 on 2005-05-22
The php4-mysql package is in universe, if you don't have that repository uncommented, you will not see those packages.

---

### Post by unruly on 2005-06-08
[QUOTE=LordHunter317]The php4-mysql package is in universe, if you don't have that repository uncommented, you will not see those packages.[/QUOTE]Oh thank god.  Thank you for pointing this out.  I've been spinning my wheels trying to figure out why php didn't have mysql support compiled into it.

---

