---
title: "caught SIGTERM, shutting down"
date: 2010-02-11
forum: Server Platforms
---

### Post by hitmanist on 2010-02-11
well this is my first post.i had a well working server with apache2 until now.
today i stopped it ,did last upgrades 2-2-14-6 over webmin and then it couldnt start

webmin error:
Failed to start apache : 
 :
Starting web server: apache2


every time i give the start command this message dropps to error.log:
[Thu Feb 11 15:01:04 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 15:01:42 2010] [notice] caught SIGTERM, shutting down

maybe i failed apache before upgrade but it worked until i stoppped it.
last things i made install some modules like pyhton and secuirty but i cleaned all my apache packages with purge and do aptitude -y purge '~c' either make a clean install nothing changed.with default config it dont start.

whats the thing,prevent apache's start
Thanks;)

---

### Post by Sporkman on 2010-02-11
Try logging in via SSH & starting it manually:

sudo /etc/init.d/apache2 start

...see what it prints out.

---

### Post by Satoru-san on 2010-02-11
better yet please post your apache log...
/var/log/apache2/error_log

I am pretty sure I know the problem. You cant start apache if you do not have a valid host domain name, You cant just have it be bobspc or something like that. it can either be localhost or yourdomain.com

---

### Post by hitmanist on 2010-02-12
error.log
[Thu Feb 11 15:01:04 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 15:01:42 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 15:01:43 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 15:07:03 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 15:07:04 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 15:20:45 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 15:20:46 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 15:34:16 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 15:34:17 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 16:17:16 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 16:17:17 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 16:28:42 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 16:28:43 2010] [notice] Apache/2.2.14 (Debian) configured -- resuming normal operations
[Thu Feb 11 16:33:43 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 16:35:07 2010] [notice] Apache/2.2.14 (Debian) mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Thu Feb 11 16:35:49 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 16:35:51 2010] [notice] Apache/2.2.14 (Debian) mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Thu Feb 11 18:19:17 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 18:19:18 2010] [notice] Apache/2.2.14 (Debian) mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Thu Feb 11 18:28:34 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 18:35:25 2010] [notice] Apache/2.2.14 (Debian) mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Thu Feb 11 18:41:16 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 18:42:29 2010] [notice] Apache/2.2.14 (Debian) mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Thu Feb 11 18:43:29 2010] [notice] caught SIGTERM, shutting down
[Thu Feb 11 18:43:30 2010] [notice] Apache/2.2.14 (Debian) mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Thu Feb 11 18:43:48 2010] [error] [client 88.224.16.215] Invalid method in request \x16\x03\x01
[Thu Feb 11 18:43:49 2010] [error] [client 88.224.16.215] Invalid method in request \x16\x03
[Thu Feb 11 18:43:49 2010] [error] [client 88.224.16.215] Invalid method in request \x16\x03
[Thu Feb 11 18:43:50 2010] [error] [client 88.224.16.215] Invalid method in request \x16\x03
[Thu Feb 11 18:43:51 2010] [error] [client 88.224.16.215] Invalid method in request \x16\x03
[Thu Feb 11 18:43:51 2010] [error] [client 88.224.16.215] Invalid method in request \x16\x03
[Thu Feb 11 18:43:52 2010] [error] [client 88.224.16.215] Invalid method in request \x16\x03

commands:
> sudo /etc/init.d/apache2 start
Starting web server: apache2.
> sudo /etc/init.d/apache2 stop
Stopping web server: apache2 ... waiting .
> sudo /etc/init.d/apache2 start
Starting web server: apache2.
> sudo /etc/init.d/apache2 start
Starting web server: apache2httpd (pid 2722) already running


and Apache have default configs,i try to take "it works" message

---

### Post by Satoru-san on 2010-02-12
Those are just notices, I thought you were saying that apache didnt start?

So you can see the it works page. Then you just need to upload some pages.

/var/www/

---

### Post by hitmanist on 2010-02-12
it seems working but not,i have var/www/index.html and host config


NameVirtualHost my ip:80

<VirtualHost my ip:80>
DocumentRoot /var/www
</VirtualHost>

---

### Post by hitmanist on 2010-02-12
never trust webmin,
1-webmin-apache not working properly
2-my apache was working but hosts didnt ,added "listen 80" to host config and it seems OK ,

and for webmin apache module correction
 pid file, That's how Webmin knows whether Apache is running or not
in module config set Path to Apache PID file var/run/apache2.pid

SOLVED_________

---

