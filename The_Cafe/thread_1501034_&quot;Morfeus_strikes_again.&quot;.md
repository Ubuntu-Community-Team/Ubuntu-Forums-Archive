---
title: "&quot;Morfeus strikes again.&quot;"
date: 2010-06-03
forum: The Cafe
---

### Post by spezticle on 2010-06-03
anyone familiar with "morfeus strikes again." as a user agent?
it's looking for readme files for roundcube webmail and other readme files, as showing in the following log line entries:


92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /roundcubemail/README HTTP/1.1" 404 474 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /rc/README HTTP/1.1" 404 467 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /webmail/README HTTP/1.1" 404 471 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /roundcube/README HTTP/1.1" 404 471 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:39 -0500] "GET /mail/README HTTP/1.1" 404 468 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:39 -0500] "GET /README HTTP/1.1" 404 465 "-" "Morfeus strikes again."

---

### Post by sydbat on 2010-06-03
Where did you find this, exactly?

---

### Post by FuturePilot on 2010-06-03
> **spezticle said:**
> anyone familiar with "morfeus strikes again." as a user agent?
it's looking for readme files for roundcube webmail and other readme files, as showing in the following log line entries:


92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /roundcubemail/README HTTP/1.1" 404 474 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /rc/README HTTP/1.1" 404 467 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /webmail/README HTTP/1.1" 404 471 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:38 -0500] "GET /roundcube/README HTTP/1.1" 404 471 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:39 -0500] "GET /mail/README HTTP/1.1" 404 468 "-" "Morfeus strikes again."
92.243.17.132 - - [03/Jun/2010:18:33:39 -0500] "GET /README HTTP/1.1" 404 465 "-" "Morfeus strikes again."

It's a bot scanner.

> **sydbat said:**
> Where did you find this, exactly?

Apache logs.

---

### Post by spezticle on 2010-06-03
> **sydbat said:**
> Where did you find this, exactly?

yeah, its my apache log, there's also relevant error log entries, too

[Thu Jun 03 18:33:38 2010] [error] [client 92.243.17.132] File does not exist: /var/www/roundcubemail
[Thu Jun 03 18:33:38 2010] [error] [client 92.243.17.132] File does not exist: /var/www/rc
[Thu Jun 03 18:33:38 2010] [error] [client 92.243.17.132] File does not exist: /var/www/webmail
[Thu Jun 03 18:33:38 2010] [error] [client 92.243.17.132] File does not exist: /var/www/roundcube
[Thu Jun 03 18:33:39 2010] [error] [client 92.243.17.132] File does not exist: /var/www/mail
[Thu Jun 03 18:33:39 2010] [error] [client 92.243.17.132] File does not exist: /var/www/README

yeah, i figured it was a scanner of sorts. i'm running lamp to learn the whole system pretty well, i'm being confronted now with security concerns lol. the IP traces back to a french webhost.

---

### Post by blackheartxxx on 2010-07-21
"morfeus strikes again" is also called "morfeus ****ing scanner."
It is an agent spider that searches your server to find any breaks so that it may shut down your Phpmyadmin and anyother php agents you may have.
 
In addition to the access log you will also find it's foot prints in the error.log.
 
Some say it is not so bad, but I lost SQL and Php-myadmin from it.
Thats about all I know of it.
 
The IP that I traced back was a Mexican Host.

---

### Post by RiceMonster on 2010-07-21
The user agent is just a simple part of the http headers. It's trivial to change it to whatever you want. Check out the firefox extension "live http headers". I know someone who saw "long live russia" and other things in their logs as well.

---

