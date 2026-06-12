---
title: "Apache2 empty error.log"
date: 2015-01-26
forum: Server Platforms
---

### Post by CrewDK on 2015-01-26
OK. I decided to start new topic for this question. 

Well. What i have: 

```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

```
 apache2 -v
Server version: Apache/2.4.7 (Ubuntu)
Server built:   Jul 22 2014 14:36:38
```


All are fresh installed. Apache is without any modification so i have only default virtual host with default settings and log files. 

cat /etc/apache2/sites-available/000-default.conf

```
<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName www.example.com

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

The problem is that in my error.log I see **only** server restart messages. Like: 

```
cat ./error.log
[Mon Jan 26 23:36:25.010217 2015] [mpm_event:notice] [pid 1611:tid 139708328335232] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Mon Jan 26 23:36:25.010365 2015] [core:notice] [pid 1611:tid 139708328335232] AH00094: Command line: '/usr/sbin/apache2'
```

In the same time in access.log a see all GET requests to my server: normal requests, bad requests, spammers e.t.c.

```
cat ./access.log 
93.185.181.155 - - [26/Jan/2015:23:36:31 +0300] "GET /favicon.ico HTTP/1.0" 404 516 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
93.185.181.155 - - [26/Jan/2015:23:36:34 +0300] "GET / HTTP/1.0" 200 11820 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
93.185.181.155 - - [26/Jan/2015:23:36:34 +0300] "GET /icons/ubuntu-logo.png HTTP/1.0" 200 3688 "http://school371.ru/" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
93.185.181.155 - - [26/Jan/2015:23:36:54 +0300] "GET /skfnsjkfbb/ HTTP/1.0" 404 502 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
93.185.181.155 - - [26/Jan/2015:23:37:13 +0300] "GET /favicon.ico HTTP/1.0" 404 516 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
93.185.181.155 - - [26/Jan/2015:23:37:26 +0300] "GET /favicon.ico HTTP/1.0" 404 516 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
93.185.181.155 - - [26/Jan/2015:23:37:37 +0300] "GET /favicon.ico HTTP/1.0" 404 516 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
93.185.181.155 - - [26/Jan/2015:23:37:39 +0300] "GET /favicon.ico HTTP/1.0" 404 515 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
```

I tried to add "LogLevel" setting to my virtual host, but this didnt helped me. 

So my question is - where is working error.log or why I doesn't see any errors in it?

---

### Post by SeijiSensei on 2015-01-26
A 404 response code is not an "error" to Apache, so it is listed in access.log.  "Errors" consist of problems loading the program, errors thrown by modules like PHP, or operating system errors like attempting to access a non-existent directory.

---

### Post by Doug S on 2015-01-26
> **SeijiSensei said:**
> A 404 response code is not an "error" to Apache, so it is listed in access.log.  "Errors" consist of problems loading the program, errors thrown by modules like PHP, or operating system errors like attempting to access a non-existent directory.That seems to be a difference between a 12.04 server and a 14.04 server. A 12.04 server does log such 404 errors in the error.log file, but yes (and I am surprised) the same is not true on a 14.04 server.

---

### Post by CrewDK on 2015-01-27
Exactly! But im affraid that this is difference not U. servers, but Apache servers.

Apache2 v. 2.2.2

access.log

```
95.167.186.8 - - [27/Jan/2015:10:37:08 +0300] "GET / HTTP/1.0" 200 479 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
95.167.186.8 - - [27/Jan/2015:10:37:24 +0300] "GET /kjgndkjfgnkdjn HTTP/1.0" 404 436 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
95.167.186.8 - - [27/Jan/2015:10:37:34 +0300] "GET /kjgndkjfgnkdjn.php HTTP/1.0" 404 440 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
```

error.log

```
[Tue Jan 27 10:37:24 2015] [error] [client 95.167.186.8] File does not exist: /var/www/cms/www/kjgndkjfgnkdjn
[Tue Jan 27 10:37:34 2015] [error] [client 95.167.186.8] script '/var/www/cms/www/kjgndkjfgnkdjn.php' not found or unable to stat
```

Apache2 2.4.7

access.log

```
95.167.186.13 - - [27/Jan/2015:10:41:56 +0300] "GET / HTTP/1.0" 200 11820 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
95.167.186.13 - - [27/Jan/2015:10:42:01 +0300] "GET /dfgdfgdfg HTTP/1.0" 404 500 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
95.167.186.13 - - [27/Jan/2015:10:42:06 +0300] "GET /dfgdfgdfg.php HTTP/1.0" 404 503 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:35.0) Gecko/20100101 Firefox/35.0"
```

error.log

```
[Mon Jan 26 23:36:25.010217 2015] [mpm_event:notice] [pid 1611:tid 139708328335232] AH00489: Apache/2.4.7 (Ubuntu) configured -- resuming normal operations
[Mon Jan 26 23:36:25.010365 2015] [core:notice] [pid 1611:tid 139708328335232] AH00094: Command line: '/usr/sbin/apache2'
```

In both cases there are same 3 requests: normal, request non-existing folder and non-existing file. So why **404 ERRORS** aren't errors anymore for apache?! And is there any way I can turn it back to "normal" work?

---

### Post by Doug S on 2015-01-27
> **CrewDK said:**
> In both cases there are same 3 requests: normal, request non-existing folder and non-existing file. So why **404 ERRORS** aren't errors anymore for apache?! And is there any way I can turn it back to "normal" work?Well, it seems that the log level for the "File does not exist" error has moved from the "error" level to the "info" level. And so those entries can be turned on again by increasing either the overall log level or the specific log level in /etc/apache2/apcahe2.conf. The example below is specific:```
#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn [COLOR=#ff0000]core:info[/COLOR]
```and gives this:```
[Tue Jan 27 08:16:15.815255 2015] [mpm_prefork:notice] [pid 9239] AH00169: caught SIGTERM, shutting down
[Tue Jan 27 08:16:16.927209 2015] [mpm_prefork:notice] [pid 9563] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 OpenSSL/1.0.1f configured -- resuming normal operations
[Tue Jan 27 08:16:16.927259 2015] [core:notice] [pid 9563] AH00094: Command line: '/usr/sbin/apache2'
[Tue Jan 27 08:16:31.613340 2015] [COLOR=#ff0000][core:info] [pid 9567] [client 192.168.111.101:53055] AH00128: File does not exist: /var/www/html/djgheht.html[/COLOR]
```I do not know what other stuff, that perhaps I don't want, will be spewed to the log.

Myself, I am going back to the default settings.

---

