---
title: "permissions error for phpmyadmin after change to Fast CGI (mod fcgid)"
date: 2010-11-22
forum: Server Platforms
---

### Post by NathanScrivener on 2010-11-22
Hi,

I'm still getting my head around setting things up on my web server, so if anyone would be prepared to help I would be very grateful.

I've configured php to run off of Fast CGI, rather than mod_php, due to better memory consumption. 

I've managed to get my virtual hosts configured to work with fastcgi, ensuring the following options are set:

AddHandler fcgid-script .php
FCGIWrapper /usr/lib/cgi-bin/php5 .php
Options +ExecCGI FollowSymLinks

I tried adding those settings to /etc/phpmyadmin/apache.conf, but this doesn't seem to work. 

Whenever I go to [www.mydomain.com/phpmyadmin](www.mydomain.com/phpmyadmin) , I just get a 403 Forbidden Error. This used to work no problems on mod_php.

/etc/phpmyadmin/apache.conf must be loading, because the alias is set so that my virtual hosts can access it through /phpmyadmin. 

There is probably something basic I am missing here. Does anybody have any ideas that could help?

Thanks in advance :-)

---

### Post by NathanScrivener on 2010-11-25
friendly bump

---

