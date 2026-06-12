---
title: "How to avoid php5-fpm causing 502 error after update"
date: 2016-10-14
forum: Server Platforms
---

### Post by sebastiaan5 on 2016-10-14
Hello,


Today (14/10/2016)  due the update of php5-fpm my webserver stopped compiling php files and showed a 502 bad gateway error at every php file. I just needed to restart php5-fpm service to make it work again, so no big fix needed.


Logs:


- update-log


```
Fri Oct 14 07:30:27 CEST 2016   php5-cgi php5-cli php5-common php5-curl php5-dev php5-fpm php5-gd
Fri Oct 14 07:30:29 CEST 2016 Get:16 http://mirrordirector.raspbian.org/raspbian/ jessie/main php5-fpm armhf 5.6.26+dfsg-0+deb8u1 [1914 kB]
Fri Oct 14 07:30:44 CEST 2016 Preparing to unpack .../php5-fpm_5.6.26+dfsg-0+deb8u1_armhf.deb ...
Fri Oct 14 07:30:45 CEST 2016 Unpacking php5-fpm (5.6.26+dfsg-0+deb8u1) over (5.6.24+dfsg-0+deb8u1) ...
Fri Oct 14 07:31:37 CEST 2016 Setting up php5-fpm (5.6.26+dfsg-0+deb8u1) ...

```


- php5fpm-log (automatic update is at 7:30)


```
[13-Oct-2016 20:40:45] WARNING: [pool www] server reached max_children setting (5), consider raising it
[14-Oct-2016 07:30:45] NOTICE: Terminating ...
[14-Oct-2016 07:30:45] NOTICE: exiting, bye-bye!
[14-Oct-2016 08:24:58] NOTICE: configuration file /etc/php5/fpm/php-fpm.conf test is successful


[14-Oct-2016 08:24:58] NOTICE: fpm is running, pid 32300
[14-Oct-2016 08:24:58] NOTICE: ready to handle connections
[14-Oct-2016 08:24:58] NOTICE: systemd monitor interval set to 10000ms
[14-Oct-2016 08:27:58] NOTICE: Terminating ...
[14-Oct-2016 08:27:58] NOTICE: exiting, bye-bye!
[14-Oct-2016 08:27:58] NOTICE: configuration file /etc/php5/fpm/php-fpm.conf test is successful


[14-Oct-2016 08:27:58] NOTICE: fpm is running, pid 32367
[14-Oct-2016 08:27:58] NOTICE: ready to handle connections
[14-Oct-2016 08:27:58] NOTICE: systemd monitor interval set to 10000ms
[14-Oct-2016 08:34:14] NOTICE: Terminating ...
[14-Oct-2016 08:34:14] NOTICE: exiting, bye-bye!
[14-Oct-2016 08:34:14] NOTICE: configuration file /etc/php5/fpm/php-fpm.conf test is successful


[14-Oct-2016 08:34:14] NOTICE: fpm is running, pid 32449
[14-Oct-2016 08:34:14] NOTICE: ready to handle connections
[14-Oct-2016 08:34:14] NOTICE: systemd monitor interval set to 10000ms
[14-Oct-2016 08:36:13] NOTICE: Terminating ...
[14-Oct-2016 08:36:13] NOTICE: exiting, bye-bye!
[14-Oct-2016 08:36:13] NOTICE: configuration file /etc/php5/fpm/php-fpm.conf test is successful


[14-Oct-2016 08:36:13] NOTICE: fpm is running, pid 32510
[14-Oct-2016 08:36:13] NOTICE: ready to handle connections
[14-Oct-2016 08:36:13] NOTICE: systemd monitor interval set to 10000ms

```


I have a cronjob that my server will automatically update, but of course I want to keep my webserver intact. Is there any fix for my problem (future problems like this) or some advice? Is making a script that will next to update the system reload all services and restart the most important services a good idea?


Greetings

---

### Post by cariboo on 2016-10-14
You'll probably get help here quicker.

---

