---
title: "trouble configuring home server/apache semi unique situations"
date: 2010-12-02
forum: Server Platforms
---

### Post by tower19 on 2010-12-02
greetings ubuntu community, i recently set up a home server that will be serving up webpages, ftp, vpn and the like. 

I have an ubuntu 10.10 lamp server installed and have run into a bit of a speed bump.

The problem lies with viewing any web pages (webpage,torrentflux,myphpadmin...) from outside of my network regardless of addressing scheme i use (will elaborate in a moment)
I believe the problem lies with apache because all other protocols work fine. ftp, webmin, ssh


At the moment i have a domainname registered with godaddy and one provided by dyndns so when my ip is re-leased with isp no interruption of service. 

atm i have my .info domain fwding to the dyndns domain
when i ftp or ssh or login to webmin through  mydomain.dyndns-blog.com or through my actual external IP all works fine.

when i externally use the dyndns domain or external ip for http it times out.

when i internally access any of the webpages regardless of method  all resolves fine.

And finally i get the error when starting apache could not determine fqdn.
I have already tried numerous numerous configuration options none to which have solved problem. 

My question lies in pretty much where am i going wrong in regards to my apache configuration.
Sorry if that was bit confusing any help appreciated. If anymore info is need let me know.

heres apache error log if that helps (blocked out my external IP for security reasons.)

server is behind basic home router in dmz. (host ip 192.168.1.19)

```
[Wed Dec 01 02:59:08 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9 with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 01 03:00:53 2010] [notice] caught SIGTERM, shutting down
[Wed Dec 01 12:35:04 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9 with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 01 12:44:12 2010] [notice] caught SIGTERM, shutting down
[Wed Dec 01 12:45:57 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 01 12:45:59 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Dec 01 12:45:59 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 01 12:53:32 2010] [notice] caught SIGTERM, shutting down
[Wed Dec 01 13:00:24 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Dec 01 17:16:19 2010] [notice] caught SIGTERM, shutting down
[Wed Dec 01 17:16:20 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 02:51:07 2010] [error] [client 192.168.1.4] File does not exist: /var/www/10000
[Thu Dec 02 02:51:08 2010] [error] [client 192.168.1.4] File does not exist: /var/www/favicon.ico
[Thu Dec 02 02:51:51 2010] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/favicon.ico
[Thu Dec 02 02:59:33 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 02 02:59:33 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 02:59:35 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 02:59:36 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:04:29 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 02 03:04:29 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:12:29 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 02 03:12:29 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:12:31 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysql.so' - /usr/lib/php5/20090626+lfs/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysqli.so' - /usr/lib/php5/20090626+lfs/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/pdo_mysql.so' - /usr/lib/php5/20090626+lfs/pdo_mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Thu Dec 02 03:12:31 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:18:25 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 02 03:18:25 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:18:27 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Dec 02 03:18:27 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:20:37 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 03:20:38 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:38:13 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 03:40:12 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:45:27 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 03:45:27 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 03:45:51 2010] [error] [client 192.168.1.4] File does not exist: /var/www/favicon.ico
ls: cannot access '/home/ftp/video/new file': No such file or directory
ls: cannot access '/home/ftp/video/new file (copy)': No such file or directory
ls: cannot access '/home/ftp/video/new file': No such file or directory
ls: cannot access '/home/ftp/video/new file (copy)': No such file or directory
[Thu Dec 02 03:58:40 2010] [error] [client 192.168.1.4] File does not exist: /var/www/favicon.ico
[Thu Dec 02 03:59:06 2010] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/favicon.ico
[Thu Dec 02 03:59:36 2010] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/favicon.ico
[Thu Dec 02 04:03:20 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 04:04:20 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 04:10:51 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 04:10:52 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 13:45:37 2010] [notice] Graceful restart requested, doing restart
[Thu Dec 02 13:45:38 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 13:46:21 2010] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/ampache
[Thu Dec 02 13:46:21 2010] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/favicon.ico
[Thu Dec 02 13:47:02 2010] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/8080
[Thu Dec 02 13:47:02 2010] [error] [client xxx.xxx.xxx.xxx] File does not exist: /var/www/favicon.ico
[Thu Dec 02 14:24:37 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 14:24:38 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 14:25:10 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 14:26:15 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 18:16:43 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 18:16:44 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations
[Thu Dec 02 18:18:08 2010] [notice] caught SIGTERM, shutting down
[Thu Dec 02 18:18:09 2010] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.1 with Suhosin-Patch configured -- resuming normal operations

```

---

### Post by tower19 on 2010-12-05
Bump....

---

