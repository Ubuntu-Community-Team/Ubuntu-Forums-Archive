---
title: "[Ubuntu 5.10 Breezy]: problem with the apache2 home page."
date: 2006-05-28
forum: Server Platforms
---

### Post by chlag on 2006-05-28
Hello, 
 I have installed the Ubuntu 5.10 "Breezy Badger", without problem and then, I installed the trio, apache2, php5 and mysql and it was, also, without problem. 
 
 I have done: 
 
```
#sudo /etc/init.d/apache2/ start
```

(to start apache2) 
 
 and then: 
 
```
#lynx http://localhost
```

 I get the home page of apache2. 
 
 also, I obtain the phpinfo page by doing: 
 
 ```
#lynx http://localhost/test.php
```

> //test.php 
 <?php 
 phpinfo 
 ?>
I swiched off my computer, and.............when I have swiched on the computer(here begun the problem): 
 I do(starting apache2): 
 
```
#sudo /etc/init.d/apache2 start
```
 no problem, the apache2 starts 
 
 But, when I do:(in the window of mozilla) 
 
 [http://localhost](http://localhost) 
 
 I get the following message(but not the apache2 home page as normal): 
 
 the message is:(after waiting for a long time) 
 
 > The operation time out when attempting to contact localhost

 My question is : 
 what is the "things" that don't allow the apache2 home page to start? 
 and, then, what must I do to have this page? 
 Thanks in advence for the help.

---

### Post by jgoguen on 2006-05-28
There should be something in your access logs and/or error logs.  By default, Apache puts them in /var/log/apache2/.  Run
```
sudo tail /var/log/apache2/access.log
``` and
```
sudo tail /var/log/apache2/error.log
``` and post the output.

---

### Post by chlag on 2006-05-28
```
sudo tail /var/log/apache2/error.log
```

gives:
> [Sat May 27 07:44:52 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico 
 [Sat May 27 07:47:22 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico 
 [Sat May 27 07:59:26 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico 
 [Sat May 27 07:59:29 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico 
 [Sat May 27 08:18:38 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico 
 [Sat May 27 08:18:42 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico 
 [Sat May 27 08:19:12 2006] [notice] caught SIGTERM, shutting down 
 [Sat May 27 09:05:34 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations 
 [Sat May 27 09:07:21 2006] [notice] caught SIGTERM, shutting down 
 [Sat May 27 09:07:22 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
and, by doing:
```
$cat /var/log/apache2/access.log
```
I get:

>  

127.0.0.1 - - [27/May/2006:07:38:05 +0200] "GET / HTTP/1.0" 200 557 "-" "Lynx/2.8.5rel.1 libwww-FM/2.14 SSL-MM/1.4.1 GNUTLS/1.0.16"
 127.0.0.1 - - [27/May/2006:07:41:53 +0200] "GET /test.php HTTP/1.1" 200 37289 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:41:53 +0200] "GET /test.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 4644 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:41:53 +0200] "GET /test.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2146 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:41:53 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:16 +0200] "GET /test.php HTTP/1.1" 200 37289 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:16 +0200] "GET /test.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 4644 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:16 +0200] "GET /test.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2146 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:16 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:52 +0200] "GET /test.php HTTP/1.1" 200 38197 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:52 +0200] "GET /test.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 4644 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:52 +0200] "GET /test.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2146 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:44:52 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:47:21 +0200] "GET /gd.php HTTP/1.1" 200 364 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:47:22 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:59:26 +0200] "GET /gd.php HTTP/1.1" 200 364 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:59:26 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:59:28 +0200] "GET /test.php HTTP/1.1" 200 38201 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:59:28 +0200] "GET /test.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 4644 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:59:28 +0200] "GET /test.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2146 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:07:59:29 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:08:18:38 +0200] "GET /gd.php HTTP/1.1" 200 364 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:08:18:38 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:08:18:42 +0200] "GET /test.php HTTP/1.1" 200 38201 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:08:18:42 +0200] "GET /test.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 4644 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:08:18:42 +0200] "GET /test.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42 HTTP/1.1" 200 2146 "http://localhost/test.php" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
 127.0.0.1 - - [27/May/2006:08:18:42 +0200] "GET /favicon.ico HTTP/1.1" 404 305 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)"
cio.

---

### Post by jgoguen on 2006-05-28
So it doesn't look like Apache started receiving requests after you rebooted.  The error log tells me that it went down and came back up, but there's no recorded page requests after the first shutdown (which I assume is when you rebooted).  My first thought, since you say Apache came up fine, is that it's not listening on localhost.  Restart Apache
```
sudo /etc/init.d/apache2 restart
```
and let's see what you get with
```
netstat -tan | grep :80 | grep LISTEN
```
This will return a list (hopefully) of addresses Apache is listening for connections on.

---

### Post by chlag on 2006-05-28
Good morning,
When I do:(After restart apache2)
```
netstat -tan | grep :80 | grep LISTEN
```
I get:

> tcp6       0      0 :::80                   :::*                    LISTEN

---

### Post by chlag on 2006-05-28
```
sudo tail /var/log/apache2/access.log
```

Gives NOTHING.

Whereas, while doing:
```
sudo tail /var/log/apache2/error.log
```
I get:
> 
[Mon May 29 04:39:15 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon May 29 04:44:37 2006] [notice] caught SIGTERM, shutting down
[Mon May 29 04:44:41 2006] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations
[Mon May 29 04:44:42 2006] [notice] caught SIGTERM, shutting down
[Mon May 29 04:44:43 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 29 04:45:59 2006] [notice] Graceful restart requested, doing restart
[Mon May 29 04:45:59 2006] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Mon May 29 04:45:59 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations
[Mon May 29 04:46:09 2006] [notice] caught SIGTERM, shutting down
[Mon May 29 04:46:10 2006] [notice] Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 configured -- resuming normal operations

---

### Post by jgoguen on 2006-05-29
Check to see if Apache is set to run at boot.  Open System -> Administration -> Services and look for the "Webserver" entry.  It's probably the last item in the list.  If the checkbox is checked, then Apache should start on boot.  If it is, reboot and don't give Apache a start command, just open a browser and try to access localhost.

If this doesn't work, or if Apache is not set to start on boot (the checkbox is unchecked), can you provide me with a tarball containing the following files:
[list]
[*]/var/log/apache2/access.log*
[*]/var/log/apache2/error.log*
[*]/var/log/messages*
[/list]
The command 
```
tar zcvf ~/logs.tgz /var/log/apache2/access.log* /var/log/apache2/error.log* /var/log/messages*
```
should put a tarball in your home directory that you can attach to a post here.  Try restarting Apache and try to access a page right before you make the tarball.

The star (*) at the end of each filename ensures that if the logs got rotated I'll get the previous logs as well (i.e. access.log.0 or access.log.0.gz).

---

### Post by chlag on 2006-05-30
Thanks, the solution of the problem was found by doing as this:
```
ifconfig -a
```
and then, we can see, clearly the problem where is it .
ok!

---

### Post by jgoguen on 2006-05-30
Heh, nice to hear it was a simple fix.  What was the problem?

---

