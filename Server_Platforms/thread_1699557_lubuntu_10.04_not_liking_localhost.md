---
title: "lubuntu 10.04 not liking localhost"
date: 2011-03-03
forum: Server Platforms
---

### Post by JKH Designs on 2011-03-03
Hello,

I am still a newbie at Linux, but have managed to get about 6 different Kubuntu systems up and all running a localhost test web server.  I always start out with a server .iso and after installing I add a kubuntu desktop GUI.  I have an old laptop that was running 8.04 server w/xubuntu desktop gui and it was running my test web pages through localhost.  I got a wild hair and thought it was about time to upgrade to 10.04 server.  I always do a complete install and this time I tried lubuntu desktop GUI.  I really like lubuntu but for some reason can not get localhost to run. I get a  402 forbidden error.  same error with 127.0.0.1

Here is what I get when I run this command

james@jkhlubuntu:~$ ls -l /etc/apache2/conf.d/
total 12
-rw-r--r-- 1 root root  269 2010-04-13 15:27 charset
lrwxrwxrwx 1 root root   45 2011-02-13 09:02 javascript-common.conf -> /etc/javascript-common/javascript-common.conf
-rw-r--r-- 1 root root 3296 2010-04-13 15:27 localized-error-pages
lrwxrwxrwx 1 root root   28 2011-02-13 09:04 phpmyadmin.conf -> ../../phpmyadmin/apache.conf
-rw-r--r-- 1 root root 1481 2010-04-13 15:27 security

Can someone please help this is driving me nutty and I haven´t got far to go.

Thanks in advance.

James

---

### Post by wongo888 on 2011-03-04
What is in your Apache error log?

---

### Post by JKH Designs on 2011-03-05
Hello wonga 888
Thanks for the reply. BTW my error code I am getting is 403 forbidden not 402 as I stated in first post.

Here is my Error Log

PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Sat Mar 05 21:21:19 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.7 with Suhosin-Patch configured -- resuming normal operations
[Sat Mar 05 22:02:51 2011] [crit] [client 127.0.0.1] (13)Permission denied: /home/james/adweb/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Sat Mar 05 22:02:52 2011] [crit] [client 127.0.0.1] (13)Permission denied: /home/james/adweb/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Sat Mar 05 22:02:55 2011] [crit] [client 127.0.0.1] (13)Permission denied: /home/james/adweb/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

I see  where (13) Permission denied is on the .htaccess pcfg openfile
but I am not sure how to change this or ensure it is readable.

I have checked my other systems and none of the error logs have this message.  I have checked all the setting for the htaccess file in Webmin
and compared them to my other systems but can´t seem to fix the problem..

Anyone have any ideas?

---

### Post by wongo888 on 2011-03-06
You need to ensure that the .htaccess file in this folder (/home/james/adweb/) is readable by Apache:

```
$ sudo chmod 644 /home/james/adweb/.htaccess
$ sudo chmod 755 /home/james/adweb
```

Otherwise, since it can't read the htaccess file, Apache fails safe by restricting access to the folder. This is just in case there are restrictions in the htaccess file that Apache doesn't know about because it can't read them. 

See:

[http://wiki.apache.org/httpd/PcfgOpenfile?highlight=(pcfg\_openfile](http://wiki.apache.org/httpd/PcfgOpenfile?highlight=(pcfg\_openfile))

[http://wiki.apache.org/httpd/13PermissionDenied](http://wiki.apache.org/httpd/13PermissionDenied)

---

### Post by JKH Designs on 2011-03-08
Hey Wonga888,

thanks so much for your help you were dead on.  It was a permission error something that I had not run into on setup of the several Kubuntu systems before.  Its funny how lubuntu handled the setup of the web server differently.

---

