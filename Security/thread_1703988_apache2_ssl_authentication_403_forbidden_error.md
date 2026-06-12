---
title: "apache2 ssl authentication 403 forbidden error"
date: 2011-03-10
forum: Security
---

### Post by satya1225 on 2011-03-10
Hi to all.
I am satya.
I configured apache2 and openssl in my ubuntu 10.04.
I configured two virtualhosts.
One is lsn.lsnsoft.com;
 [http://pastebin.com/9GpmvZQF](http://pastebin.com/9GpmvZQF)
Another is ubuntu.lsnsoft.internal
[http://pastebin.com/w3rz0DdW](http://pastebin.com/w3rz0DdW)

after configuration openssl, i tried to access the sites from my client web browser using https,
it says 403 forbidden error. you dont have to access / on this server.
Permissions for /etc/apache2/ssl = 777
Permissions fro /var/www/ = 755  owner= username:www-data
Permissions /var/www/reviewboard/htdocs/media= 777
Thank you and regards

-satya.

---

### Post by robsoles on 2011-03-10
Hi, welcome to UF.

You don't need those explicitly 'open' permissions on those directories to make SSL work. No doubt regulars of Apache specific forums would be all over this with a rash of things for you to check.

I've done a fair bit with Apache and had a little experience of Apache2 but I haven't bothered with SSL before and I have to say right now that it is just the 'nature' of webservice requirements for directory permissions that I very much doubt that service in SSL requires 'foolish' permissions on files.

Have you read all the way though [http://onlamp.com/pub/a/onlamp/2008/03/04/step-by-step-configuring-ssl-under-apache.html](http://onlamp.com/pub/a/onlamp/2008/03/04/step-by-step-configuring-ssl-under-apache.html) ???

To be honest, I didn't but I expect they don't tell you chmod 777 anything.

Please read it and challenge me to help you make their stuff work rather than responding without making sure you've applied the steps they say are required to make SSL work with Apache 2.0

---

