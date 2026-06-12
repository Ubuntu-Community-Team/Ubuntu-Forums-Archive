---
title: "Cacti graphs dont show"
date: 2010-01-06
forum: Server Platforms
---

### Post by rado3105 on 2010-01-06
I installed cacti and set snmp using this manual:
[http://samiux.wordpress.com/2009/06/26/howto-cacti-on-ubuntu-9-04-server/](http://samiux.wordpress.com/2009/06/26/howto-cacti-on-ubuntu-9-04-server/)
after installation and restart, the graphs dont show:
[img]http://i47.tinypic.com/2yw9x5z.jpg[/img]
this is my cacti general  settings:
[img]http://i46.tinypic.com/8wb9lz.[/img]

---

### Post by iponeverything on 2010-01-06
Take a peek in the apache access log and error log.

Post what you find.

---

### Post by rado3105 on 2010-01-06
output of /var/log/apache2/error.log:
> r-c@ubuntu-server:~$ cat /var/log/apache2/error.log
[Tue Jan 05 00:43:42 2010] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Tue Jan 05 02:39:19 2010] [notice] caught SIGTERM, shutting down
[Tue Jan 05 02:39:59 2010] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Tue Jan 05 02:44:27 2010] [notice] caught SIGTERM, shutting down
[Tue Jan 05 02:45:07 2010] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Tue Jan  5 03:37:54 2010] smokeping.cgi: RRDs::info /var/lib/smokeping/Internet/Yahoo-com.rrd: ERROR: '/var/lib/smokeping/Internet/Yahoo-com.rrd' is not an RRD file at /usr/share/perl5/smokeping/Smokeping/RRDtools.pm line 113.
[Tue Jan 05 03:37:57 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:00 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:06 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:12 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:18 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:27 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:33 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:44 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:47 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:50 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:41:54 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:42:03 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:42:07 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 03:42:26 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:45:33 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:47:30 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:47:35 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:47:41 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:48:58 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:49:14 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:49:21 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:54:22 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 12:55:53 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:06 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:12 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:17 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:23 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:26 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:30 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:35 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:44 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:50 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 17:43:55 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 20:44:43 2010] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Tue Jan 05 20:45:00 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 20:45:02 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 20:45:08 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 20:45:15 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 20:45:22 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 23:58:22 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Tue Jan 05 23:58:22 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:35:27 2010] [notice] caught SIGTERM, shutting down
[Wed Jan 06 00:37:01 2010] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Wed Jan 06 00:37:06 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 10.10.10.10 for ServerName
[Wed Jan 06 00:37:06 2010] [notice] Apache/2.2.11 (Ubuntu) configured -- resuming normal operations
[Wed Jan 06 00:38:00 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 10.10.10.10 for ServerName
[Wed Jan 06 00:38:03 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.4 with Suhosin-Patch configured -- resuming normal operations
[Wed Jan 06 00:42:47 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:42:53 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:42:58 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:43:58 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:44:05 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:44:17 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:44:21 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:44:26 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:44:44 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:44:48 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:44:57 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:45:02 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:45:35 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
ERROR: I don't understand ':45:57 To 2010/01/06 00:45:57\c' in command: 'COMMENT:From 2010/01/05 00:45:57 To 2010/01/06 00:45:57\c'.
ERROR: I don't understand ':45:57 To 2010/01/06 00:45:57\c' in command: 'COMMENT:From 2010/01/05 00:45:57 To 2010/01/06 00:45:57\c'.
ERROR: I don't understand ':45:57 To 2010/01/06 00:45:57\c' in command: 'COMMENT:From 2010/01/05 00:45:57 To 2010/01/06 00:45:57\c'.
ERROR: I don't understand ':45:57 To 2010/01/06 00:45:57\c' in command: 'COMMENT:From 2010/01/05 00:45:57 To 2010/01/06 00:45:57\c'.
ERROR: I don't understand ':46:15 To 2010/01/06 00:46:15\c' in command: 'COMMENT:From 2010/01/05 00:46:15 To 2010/01/06 00:46:15\c'.
ERROR: I don't understand ':46:15 To 2010/01/06 00:46:15\c' in command: 'COMMENT:From 2010/01/05 00:46:15 To 2010/01/06 00:46:15\c'.
ERROR: I don't understand ':46:15 To 2010/01/06 00:46:15\c' in command: 'COMMENT:From 2010/01/05 00:46:15 To 2010/01/06 00:46:15\c'.
ERROR: I don't understand ':46:15 To 2010/01/06 00:46:15\c' in command: 'COMMENT:From 2010/01/05 00:46:15 To 2010/01/06 00:46:15\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: I don't understand ':46:46 To 2010/01/06 00:46:46\c' in command: 'COMMENT:From 2010/01/05 00:46:46 To 2010/01/06 00:46:46\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':47:01 To 2010/01/06 00:47:01\c' in command: 'COMMENT:From 2010/01/05 00:47:01 To 2010/01/06 00:47:01\c'.
ERROR: I don't understand ':47:01 To 2010/01/06 00:47:01\c' in command: 'COMMENT:From 2010/01/05 00:47:01 To 2010/01/06 00:47:01\c'.
ERROR: I don't understand ':47:01 To 2010/01/06 00:47:01\c' in command: 'COMMENT:From 2010/01/05 00:47:01 To 2010/01/06 00:47:01\c'.
ERROR: I don't understand ':47:01 To 2010/01/06 00:47:01\c' in command: 'COMMENT:From 2010/01/05 00:47:01 To 2010/01/06 00:47:01\c'.
ERROR: I don't understand ':47:01 To 2010/01/06 00:47:01\c' in command: 'COMMENT:From 2010/01/05 00:47:01 To 2010/01/06 00:47:01\c'.
ERROR: I don't understand ':47:06 To 2010/01/06 00:47:06\c' in command: 'COMMENT:From 2010/01/05 00:47:06 To 2010/01/06 00:47:06\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':47:06 To 2010/01/06 00:47:06\c' in command: 'COMMENT:From 2010/01/05 00:47:06 To 2010/01/06 00:47:06\c'.
ERROR: I don't understand ':47:06 To 2010/01/06 00:47:06\c' in command: 'COMMENT:From 2010/01/05 00:47:06 To 2010/01/06 00:47:06\c'.
ERROR: I don't understand ':47:06 To 2010/01/06 00:47:06\c' in command: 'COMMENT:From 2010/01/05 00:47:06 To 2010/01/06 00:47:06\c'.
ERROR: I don't understand ':47:06 To 2010/01/06 00:47:06\c' in command: 'COMMENT:From 2010/01/05 00:47:06 To 2010/01/06 00:47:06\c'.
ERROR: I don't understand ':47:07 To 2010/01/06 00:47:07\c' in command: 'COMMENT:From 2010/01/05 00:47:07 To 2010/01/06 00:47:07\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':47:07 To 2010/01/06 00:47:07\c' in command: 'COMMENT:From 2010/01/05 00:47:07 To 2010/01/06 00:47:07\c'.
ERROR: I don't understand ':47:07 To 2010/01/06 00:47:07\c' in command: 'COMMENT:From 2010/01/05 00:47:07 To 2010/01/06 00:47:07\c'.
ERROR: I don't understand ':47:07 To 2010/01/06 00:47:07\c' in command: 'COMMENT:From 2010/01/05 00:47:07 To 2010/01/06 00:47:07\c'.
ERROR: I don't understand ':47:07 To 2010/01/06 00:47:07\c' in command: 'COMMENT:From 2010/01/05 00:47:07 To 2010/01/06 00:47:07\c'.
ERROR: I don't understand ':47:30 To 2010/01/06 00:47:30\c' in command: 'COMMENT:From 2010/01/05 00:47:30 To 2010/01/06 00:47:30\c'.
ERROR: I don't understand ':47:30 To 2010/01/06 00:47:30\c' in command: 'COMMENT:From 2010/01/05 00:47:30 To 2010/01/06 00:47:30\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':47:30 To 2010/01/06 00:47:30\c' in command: 'COMMENT:From 2010/01/05 00:47:30 To 2010/01/06 00:47:30\c'.
ERROR: I don't understand ':47:30 To 2010/01/06 00:47:30\c' in command: 'COMMENT:From 2010/01/05 00:47:30 To 2010/01/06 00:47:30\c'.
ERROR: I don't understand ':47:30 To 2010/01/06 00:47:30\c' in command: 'COMMENT:From 2010/01/05 00:47:30 To 2010/01/06 00:47:30\c'.
[Wed Jan 06 00:49:22 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 00:49:25 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_load_1min_8.rrd': No such file or directory
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: I don't understand ':49:31 To 2010/01/06 00:49:31\c' in command: 'COMMENT:From 2010/01/05 00:49:31 To 2010/01/06 00:49:31\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':52:26 To 2010/01/06 00:52:26\c' in command: 'COMMENT:From 2010/01/05 00:52:26 To 2010/01/06 00:52:26\c'.
ERROR: I don't understand ':52:26 To 2010/01/06 00:52:26\c' in command: 'COMMENT:From 2010/01/05 00:52:26 To 2010/01/06 00:52:26\c'.
ERROR: I don't understand ':52:26 To 2010/01/06 00:52:26\c' in command: 'COMMENT:From 2010/01/05 00:52:26 To 2010/01/06 00:52:26\c'.
ERROR: I don't understand ':52:26 To 2010/01/06 00:52:26\c' in command: 'COMMENT:From 2010/01/05 00:52:26 To 2010/01/06 00:52:26\c'.
ERROR: I don't understand ':52:26 To 2010/01/06 00:52:26\c' in command: 'COMMENT:From 2010/01/05 00:52:26 To 2010/01/06 00:52:26\c'.
ERROR: I don't understand ':52:26 To 2010/01/06 00:52:26\c' in command: 'COMMENT:From 2010/01/05 00:52:26 To 2010/01/06 00:52:26\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: I don't understand ':22:34 To 2010/01/06 00:52:34\c' in command: 'COMMENT:From 2010/01/06 00:22:34 To 2010/01/06 00:52:34\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':22:49 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:22:49 To 2010/01/06 00:52:49\c'.
ERROR: I don't understand ':22:49 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:22:49 To 2010/01/06 00:52:49\c'.
ERROR: I don't understand ':22:49 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:22:49 To 2010/01/06 00:52:49\c'.
ERROR: I don't understand ':22:49 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:22:49 To 2010/01/06 00:52:49\c'.
ERROR: I don't understand ':22:49 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:22:49 To 2010/01/06 00:52:49\c'.
ERROR: I don't understand ':22:49 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:22:49 To 2010/01/06 00:52:49\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':22:49 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:22:49 To 2010/01/06 00:52:49\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':37:26 To 2010/01/06 00:52:49\c' in command: 'COMMENT:From 2010/01/06 00:37:26 To 2010/01/06 00:52:49\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':24:03 To 2010/01/06 00:54:03\c' in command: 'COMMENT:From 2010/01/06 00:24:03 To 2010/01/06 00:54:03\c'.
ERROR: I don't understand ':24:03 To 2010/01/06 00:54:03\c' in command: 'COMMENT:From 2010/01/06 00:24:03 To 2010/01/06 00:54:03\c'.
ERROR: I don't understand ':24:03 To 2010/01/06 00:54:03\c' in command: 'COMMENT:From 2010/01/06 00:24:03 To 2010/01/06 00:54:03\c'.
ERROR: I don't understand ':24:03 To 2010/01/06 00:54:03\c' in command: 'COMMENT:From 2010/01/06 00:24:03 To 2010/01/06 00:54:03\c'.
ERROR: I don't understand ':24:03 To 2010/01/06 00:54:03\c' in command: 'COMMENT:From 2010/01/06 00:24:03 To 2010/01/06 00:54:03\c'.
ERROR: I don't understand ':24:03 To 2010/01/06 00:54:03\c' in command: 'COMMENT:From 2010/01/06 00:24:03 To 2010/01/06 00:54:03\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':27:59 To 2010/01/05 00:54:23\c' in command: 'COMMENT:From 2008/12/19 11:27:59 To 2010/01/05 00:54:23\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':24:33 To 2010/01/06 00:54:33\c' in command: 'COMMENT:From 2010/01/06 00:24:33 To 2010/01/06 00:54:33\c'.
ERROR: I don't understand ':24:33 To 2010/01/06 00:54:33\c' in command: 'COMMENT:From 2010/01/06 00:24:33 To 2010/01/06 00:54:33\c'.
ERROR: I don't understand ':24:33 To 2010/01/06 00:54:33\c' in command: 'COMMENT:From 2010/01/06 00:24:33 To 2010/01/06 00:54:33\c'.
ERROR: I don't understand ':24:33 To 2010/01/06 00:54:33\c' in command: 'COMMENT:From 2010/01/06 00:24:33 To 2010/01/06 00:54:33\c'.
ERROR: I don't understand ':24:33 To 2010/01/06 00:54:33\c' in command: 'COMMENT:From 2010/01/06 00:24:33 To 2010/01/06 00:54:33\c'.
ERROR: I don't understand ':24:33 To 2010/01/06 00:54:33\c' in command: 'COMMENT:From 2010/01/06 00:24:33 To 2010/01/06 00:54:33\c'.
ERROR: I don't understand ':54:52 To 2010/01/06 00:49:52\c' in command: 'COMMENT:From 2010/01/05 00:54:52 To 2010/01/06 00:49:52\c'.
ERROR: I don't understand ':45:57 To 2010/01/06 00:49:52\c' in command: 'COMMENT:From 2010/01/05 17:45:57 To 2010/01/06 00:49:52\c'.
ERROR: I don't understand ':55:05 To 2010/01/06 00:50:05\c' in command: 'COMMENT:From 2010/01/05 00:55:05 To 2010/01/06 00:50:05\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':25:15 To 2010/01/06 00:55:15\c' in command: 'COMMENT:From 2010/01/06 00:25:15 To 2010/01/06 00:55:15\c'.
ERROR: I don't understand ':25:15 To 2010/01/06 00:55:15\c' in command: 'COMMENT:From 2010/01/06 00:25:15 To 2010/01/06 00:55:15\c'.
ERROR: I don't understand ':25:15 To 2010/01/06 00:55:15\c' in command: 'COMMENT:From 2010/01/06 00:25:15 To 2010/01/06 00:55:15\c'.
ERROR: I don't understand ':25:15 To 2010/01/06 00:55:15\c' in command: 'COMMENT:From 2010/01/06 00:25:15 To 2010/01/06 00:55:15\c'.
ERROR: I don't understand ':25:15 To 2010/01/06 00:55:15\c' in command: 'COMMENT:From 2010/01/06 00:25:15 To 2010/01/06 00:55:15\c'.
ERROR: I don't understand ':25:15 To 2010/01/06 00:55:15\c' in command: 'COMMENT:From 2010/01/06 00:25:15 To 2010/01/06 00:55:15\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':28:48 To 2010/01/06 00:58:48\c' in command: 'COMMENT:From 2010/01/06 00:28:48 To 2010/01/06 00:58:48\c'.
ERROR: I don't understand ':28:48 To 2010/01/06 00:58:48\c' in command: 'COMMENT:From 2010/01/06 00:28:48 To 2010/01/06 00:58:48\c'.
ERROR: I don't understand ':28:48 To 2010/01/06 00:58:48\c' in command: 'COMMENT:From 2010/01/06 00:28:48 To 2010/01/06 00:58:48\c'.
ERROR: I don't understand ':28:48 To 2010/01/06 00:58:48\c' in command: 'COMMENT:From 2010/01/06 00:28:48 To 2010/01/06 00:58:48\c'.
ERROR: I don't understand ':28:48 To 2010/01/06 00:58:48\c' in command: 'COMMENT:From 2010/01/06 00:28:48 To 2010/01/06 00:58:48\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':04:10 To 2010/01/06 00:59:10\c' in command: 'COMMENT:From 2010/01/05 01:04:10 To 2010/01/06 00:59:10\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':34:45 To 2010/01/05 16:17:52\c' in command: 'COMMENT:From 2010/01/05 14:34:45 To 2010/01/05 16:17:52\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':39:10 To 2010/01/05 16:17:52\c' in command: 'COMMENT:From 2010/01/05 15:39:10 To 2010/01/05 16:17:52\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':40:03 To 2010/01/06 01:10:03\c' in command: 'COMMENT:From 2010/01/06 00:40:03 To 2010/01/06 01:10:03\c'.
ERROR: I don't understand ':40:03 To 2010/01/06 01:10:03\c' in command: 'COMMENT:From 2010/01/06 00:40:03 To 2010/01/06 01:10:03\c'.
ERROR: I don't understand ':40:03 To 2010/01/06 01:10:03\c' in command: 'COMMENT:From 2010/01/06 00:40:03 To 2010/01/06 01:10:03\c'.
ERROR: I don't understand ':40:03 To 2010/01/06 01:10:03\c' in command: 'COMMENT:From 2010/01/06 00:40:03 To 2010/01/06 01:10:03\c'.
ERROR: I don't understand ':40:03 To 2010/01/06 01:10:03\c' in command: 'COMMENT:From 2010/01/06 00:40:03 To 2010/01/06 01:10:03\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':42:30 To 2010/01/06 01:12:30\c' in command: 'COMMENT:From 2010/01/06 00:42:30 To 2010/01/06 01:12:30\c'.
ERROR: I don't understand ':42:30 To 2010/01/06 01:12:30\c' in command: 'COMMENT:From 2010/01/06 00:42:30 To 2010/01/06 01:12:30\c'.
ERROR: I don't understand ':42:30 To 2010/01/06 01:12:30\c' in command: 'COMMENT:From 2010/01/06 00:42:30 To 2010/01/06 01:12:30\c'.
ERROR: I don't understand ':42:30 To 2010/01/06 01:12:30\c' in command: 'COMMENT:From 2010/01/06 00:42:30 To 2010/01/06 01:12:30\c'.
ERROR: I don't understand ':42:30 To 2010/01/06 01:12:30\c' in command: 'COMMENT:From 2010/01/06 00:42:30 To 2010/01/06 01:12:30\c'.
[Wed Jan 06 11:13:35 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':13:43 To 2010/01/06 11:13:43\c' in command: 'COMMENT:From 2010/01/05 11:13:43 To 2010/01/06 11:13:43\c'.
ERROR: I don't understand ':13:43 To 2010/01/06 11:13:43\c' in command: 'COMMENT:From 2010/01/05 11:13:43 To 2010/01/06 11:13:43\c'.
ERROR: I don't understand ':13:43 To 2010/01/06 11:13:43\c' in command: 'COMMENT:From 2010/01/05 11:13:43 To 2010/01/06 11:13:43\c'.
ERROR: I don't understand ':13:43 To 2010/01/06 11:13:43\c' in command: 'COMMENT:From 2010/01/05 11:13:43 To 2010/01/06 11:13:43\c'.
ERROR: I don't understand ':13:43 To 2010/01/06 11:13:43\c' in command: 'COMMENT:From 2010/01/05 11:13:43 To 2010/01/06 11:13:43\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':13:43 To 2010/01/06 11:13:43\c' in command: 'COMMENT:From 2010/01/05 11:13:43 To 2010/01/06 11:13:43\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':14:07 To 2010/01/06 11:14:07\c' in command: 'COMMENT:From 2010/01/05 11:14:07 To 2010/01/06 11:14:07\c'.
ERROR: I don't understand ':14:07 To 2010/01/06 11:14:07\c' in command: 'COMMENT:From 2010/01/05 11:14:07 To 2010/01/06 11:14:07\c'.
ERROR: I don't understand ':14:07 To 2010/01/06 11:14:07\c' in command: 'COMMENT:From 2010/01/05 11:14:07 To 2010/01/06 11:14:07\c'.
ERROR: I don't understand ':14:07 To 2010/01/06 11:14:07\c' in command: 'COMMENT:From 2010/01/05 11:14:07 To 2010/01/06 11:14:07\c'.
ERROR: I don't understand ':14:07 To 2010/01/06 11:14:07\c' in command: 'COMMENT:From 2010/01/05 11:14:07 To 2010/01/06 11:14:07\c'.
[Wed Jan 06 11:18:48 2010] [notice] caught SIGTERM, shutting down
[Wed Jan 06 11:19:58 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.4 with Suhosin-Patch configured -- resuming normal operations
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':32:12 To 2010/01/06 11:32:12\c' in command: 'COMMENT:From 2010/01/05 11:32:12 To 2010/01/06 11:32:12\c'.
ERROR: I don't understand ':32:12 To 2010/01/06 11:32:12\c' in command: 'COMMENT:From 2010/01/05 11:32:12 To 2010/01/06 11:32:12\c'.
ERROR: I don't understand ':32:12 To 2010/01/06 11:32:12\c' in command: 'COMMENT:From 2010/01/05 11:32:12 To 2010/01/06 11:32:12\c'.
ERROR: I don't understand ':32:12 To 2010/01/06 11:32:12\c' in command: 'COMMENT:From 2010/01/05 11:32:12 To 2010/01/06 11:32:12\c'.
ERROR: I don't understand ':32:12 To 2010/01/06 11:32:12\c' in command: 'COMMENT:From 2010/01/05 11:32:12 To 2010/01/06 11:32:12\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':32:17 To 2010/01/06 11:32:17\c' in command: 'COMMENT:From 2010/01/05 11:32:17 To 2010/01/06 11:32:17\c'.
ERROR: I don't understand ':32:17 To 2010/01/06 11:32:17\c' in command: 'COMMENT:From 2010/01/05 11:32:17 To 2010/01/06 11:32:17\c'.
ERROR: I don't understand ':32:17 To 2010/01/06 11:32:17\c' in command: 'COMMENT:From 2010/01/05 11:32:17 To 2010/01/06 11:32:17\c'.
ERROR: I don't understand ':32:17 To 2010/01/06 11:32:17\c' in command: 'COMMENT:From 2010/01/05 11:32:17 To 2010/01/06 11:32:17\c'.
ERROR: I don't understand ':32:17 To 2010/01/06 11:32:17\c' in command: 'COMMENT:From 2010/01/05 11:32:17 To 2010/01/06 11:32:17\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':34:21 To 2010/01/06 11:34:21\c' in command: 'COMMENT:From 2010/01/05 11:34:21 To 2010/01/06 11:34:21\c'.
ERROR: I don't understand ':34:21 To 2010/01/06 11:34:21\c' in command: 'COMMENT:From 2010/01/05 11:34:21 To 2010/01/06 11:34:21\c'.
ERROR: I don't understand ':34:21 To 2010/01/06 11:34:21\c' in command: 'COMMENT:From 2010/01/05 11:34:21 To 2010/01/06 11:34:21\c'.
ERROR: I don't understand ':34:21 To 2010/01/06 11:34:21\c' in command: 'COMMENT:From 2010/01/05 11:34:21 To 2010/01/06 11:34:21\c'.
ERROR: I don't understand ':34:21 To 2010/01/06 11:34:21\c' in command: 'COMMENT:From 2010/01/05 11:34:21 To 2010/01/06 11:34:21\c'.
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':39:22 To 2010/01/06 11:39:22\c' in command: 'COMMENT:From 2010/01/05 11:39:22 To 2010/01/06 11:39:22\c'.
ERROR: I don't understand ':39:22 To 2010/01/06 11:39:22\c' in command: 'COMMENT:From 2010/01/05 11:39:22 To 2010/01/06 11:39:22\c'.
ERROR: I don't understand ':39:22 To 2010/01/06 11:39:22\c' in command: 'COMMENT:From 2010/01/05 11:39:22 To 2010/01/06 11:39:22\c'.
ERROR: I don't understand ':39:22 To 2010/01/06 11:39:22\c' in command: 'COMMENT:From 2010/01/05 11:39:22 To 2010/01/06 11:39:22\c'.
ERROR: I don't understand ':39:22 To 2010/01/06 11:39:22\c' in command: 'COMMENT:From 2010/01/05 11:39:22 To 2010/01/06 11:39:22\c'.
[Wed Jan 06 11:41:27 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
[Wed Jan 06 11:42:24 2010] [error] [client 10.10.10.9] File does not exist: /var/www/favicon.ico
ERROR: opening '/var/lib/cacti/rra/localhost_5min_cpu_9.rrd': No such file or directory
ERROR: I don't understand ':45:18 To 2010/01/06 11:45:18\c' in command: 'COMMENT:From 2010/01/05 11:45:18 To 2010/01/06 11:45:18\c'.
ERROR: I don't understand ':45:18 To 2010/01/06 11:45:18\c' in command: 'COMMENT:From 2010/01/05 11:45:18 To 2010/01/06 11:45:18\c'.
ERROR: I don't understand ':45:18 To 2010/01/06 11:45:18\c' in command: 'COMMENT:From 2010/01/05 11:45:18 To 2010/01/06 11:45:18\c'.
ERROR: I don't understand ':45:18 To 2010/01/06 11:45:18\c' in command: 'COMMENT:From 2010/01/05 11:45:18 To 2010/01/06 11:45:18\c'.
ERROR: I don't understand ':45:18 To 2010/01/06 11:45:18\c' in command: 'COMMENT:From 2010/01/05 11:45:18 To 2010/01/06 11:45:18\c'.


---

### Post by iponeverything on 2010-01-06
Ok, next step:

What is in:
/var/lib/cacti/rra/


I take it does not contain the rrd files..

Anyway.. lets try to find where they actually are..

```
find / -type f -name "*.rrd" -ls 

```

---

### Post by iponeverything on 2010-01-06
Cacti should kicking off cronjob every 5 minutes.

su to user that cacti is using and try running the command by hand so that you can catch any output.

do you have a /var/log/cacti

?

---

### Post by iponeverything on 2010-01-06
found your problem:

[http://forums.cacti.net/about28537.html&highlight=](http://forums.cacti.net/about28537.html&highlight=)

---

### Post by rado3105 on 2010-01-06
works, thanks a lot.

---

### Post by iponeverything on 2010-01-06
glad you figured it out.

---

### Post by Nander on 2010-12-02
Hello Guys!

I´ve the same problem!

I was using CMD.php and switched by the SPINE and my graphics were not presented. I read that this could be a problem because he is not running in Cron the pooler.php.

Ran the pooler.php and returned to default Settings in Settings page to CMD.

went back to work!

Att

Nander

---

