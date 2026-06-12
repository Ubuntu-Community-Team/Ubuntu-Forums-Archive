---
title: "apache2/php5 - can't get php log_errors to work"
date: 2006-08-12
forum: Server Platforms
---

### Post by axolotl on 2006-08-12
Hi all.  I'm usually a Mac or OpenBSD'er, and I've never had this problem before, so I wonder if anyone on Ubuntu or similar Linux has seen this before and has any suggestions.

Installed apache2/php5 on Dapper Drake.  Actually, I started with the Desktop install, but it's ending up as a server - I just took that path because I wanted to get more familiar with the system in a friendly sort of way.

Anyway, no matter what I tweak, I can't get php's error log to output anything.  In /etc/php5/apache2/php.ini, I've set...

error_reporting  =  E_ALL & ~E_NOTICE
log_errors = On
error_log = /var/log/apache2/phperr.log

...and I've done something similar in a VirtualHost to output its own logs.  All settings are correctly reflected by phpinfo().  All other aspects of apache2 logging (e.g. piping to cronolog) are working perfectly, but php just won't output anything to its log file.

In the past, I've had to 'touch phperr.log' and chown it to the webserver user to get it to work, and I've done that here, but still no luck.

Any thoughts much appreciated...

---

