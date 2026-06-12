---
title: "Try to build lamp server but got &quot;403 Forbidden&quot;"
date: 2009-07-26
forum: Server Platforms
---

### Post by Olnex on 2009-07-26
I tried to build a LAMP server on Ubuntu 9.04 Desktop edition, followed the link:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Everything is fine but when I access [http://localhost](http://localhost) it said "403 Forbidden" and "You don't have permission to access / on this server."

Everything is setup according to the above link, and here is the error.log:

> [Mon Jul 27 11:49:45 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Mon Jul 27 11:50:03 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Jul 27 11:50:06 2009] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Jul 27 11:51:02 2009] [notice] caught SIGTERM, shutting down
[Mon Jul 27 11:51:08 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Mon Jul 27 11:51:10 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Jul 27 11:51:10 2009] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Mon Jul 27 11:56:02 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Mon Jul 27 11:56:02 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 27 11:59:09 2009] [notice] caught SIGTERM, shutting down
[Mon Jul 27 11:59:11 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 27 11:59:29 2009] [error] [client 127.0.0.1] File does not exist: /var/www/phpAdmin
[Mon Jul 27 11:59:33 2009] [error] [client 127.0.0.1] File does not exist: /var/www/phpMyAdmin
[Mon Jul 27 12:04:06 2009] [notice] caught SIGTERM, shutting down
[Mon Jul 27 12:04:07 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Jul 27 12:04:34 2009] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
[Mon Jul 27 12:08:31 2009] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
[Mon Jul 27 12:10:42 2009] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
[Mon Jul 27 12:10:52 2009] [error] [client 127.0.0.1] (13)Permission denied: access to / denied

and access.log:
> 
127.0.0.1 - - [27/Jul/2009:11:50:03 +1000] "GET / HTTP/1.1" 200 56 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:11:50:03 +1000] "GET /favicon.ico HTTP/1.1" 404 236 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:11:50:06 +1000] "GET /favicon.ico HTTP/1.1" 404 236 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:11:51:10 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:51:10 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:51:10 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:51:10 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:51:10 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:56:02 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:56:02 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:56:02 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:56:02 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:56:02 +1000] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.11 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [27/Jul/2009:11:59:25 +1000] "GET / HTTP/1.1" 200 56 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:11:59:29 +1000] "GET /phpAdmin HTTP/1.1" 404 259 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:11:59:33 +1000] "GET /phpMyAdmin HTTP/1.1" 404 261 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:12:04:34 +1000] "GET / HTTP/1.1" 403 256 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:12:08:31 +1000] "GET / HTTP/1.1" 403 256 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:12:10:42 +1000] "GET / HTTP/1.1" 403 256 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"
127.0.0.1 - - [27/Jul/2009:12:10:52 +1000] "GET / HTTP/1.1" 403 256 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.12) Gecko/2009070811 Ubuntu/9.04 (jaunty) Firefox/3.0.12"

I tried to chmod 777 index.html also tried to rename it to index.htm, but none of them works, can anyone helps me out or point me to the right direction?

Thanks!

---

### Post by cosine352 on 2009-07-26
what is the out put of 

> ls -l /var/ | grep www

I got this and works fine

> drwxr-xr-x  4 root root   4096 2009-05-08 20:51 www


probably you need to change the permission for the directory 'www'

---

### Post by Olnex on 2009-07-27
Thanks for your reply. I have the same output, I even tried to make www belong to "users" group, but it does not work. Furthermore, I've set the directory to /home/username/public_html.

---

### Post by baboeska on 2009-08-12
Hi,
I'm getting the same problem since July 30th, constant 403 access denied errors.

My error log has the following line repeated many times over:

[Wed Aug 12 23:07:05 2009] [crit] [client 192.168.1.1] (13)Permission denied: /home/mingus/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

And my site appears with the following text:

Forbidden

You don't have permission to access / on this server.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at localhost Port 80


My main public_html directory has the following permissions set:
drwxr-xr-x  3 www-data homeuser    4096 2009-08-12 22:56 public_html

The files within have the following permissions set:
-rwxrwxr-x 1 www-data mingus  2002 2009-07-28 10:19 index.html

As it is I get 403 errors when I try to go to localhost, I'm happy to paste/get more data, but I am new to running LAMP servers, so please give me lots of information.
The server was up for about two days, I think the suhosin patch might have done something based on other reading I've done, but I'm not sure what to do next and help resolving this would be great :)

Thank you

---

### Post by cirobr on 2009-09-23
Same error for me on a fully updated Ubuntu Hardy server, which was working smoothly till 1-2 months ago:

* All attempts for purging apache and all config files before reinstalling;

* Changing permission of /home/user/www to 777.

Any feedback is appreciated.

Thanks.

---

### Post by cirobr on 2009-09-23
Have also noticed that, whenever Apache is restarted, the following message is shown:

> 
* Restarting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


---

### Post by cirobr on 2009-10-06
> **cirobr said:**
> Same error for me on a fully updated Ubuntu Hardy server, which was working smoothly till 1-2 months ago:

* All attempts for purging apache and all config files before reinstalling;

* Changing permission of /home/user/www to 777.

Any feedback is appreciated.

Thanks.

By setting permissions as follows has solved my issue:
/home/user to 711
/home/user/www to 751

---

### Post by crypto2600 on 2009-11-04
Thank you

711 & 751 permissions solved my problem.

thank you very much

---

### Post by another_sam on 2012-05-02
I had to put 711 & 755.

Thank you very much anyways. I usually trip over this problem for each LAMP installation.

---

