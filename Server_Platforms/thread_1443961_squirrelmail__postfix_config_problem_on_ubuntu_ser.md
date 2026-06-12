---
title: "squirrelmail / postfix config problem on ubuntu server 9.10"
date: 2010-03-31
forum: Server Platforms
---

### Post by penrodyn on 2010-03-31
Hi,

I have created a working mail server using postfix and squirrelmail by following the tutorial at [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/).

My problem is that I would prefer squirrelmail to be installed on my webserver (ubuntu-www) and connect to my mail server (ubuntu-mail) rather than have squirrelmail run from the mail server.  I can login, send and receive external emails using squirrelmail installed on the mail server so I installed squirrelmail on the web server, mirroring the configuration with the exception of the fact that I changed the server settings from local host to the IP address of the mail server.

When I attempt to login via squirrelmail on the webserver I get an error unknown user or password incorrect.

Hope this makes sense, any suggestions?

Thanks in advance!
Lee

---

### Post by KB1JWQ on 2010-04-01
Remove Squirrelmail from the equation.  Use Thunderbird or evolution, and point it at the mailserver.

I think you'll find it fails there, too.  If so, I'd like to see what the maillogs say for Dovecot (or whatever imap server you're using).

---

