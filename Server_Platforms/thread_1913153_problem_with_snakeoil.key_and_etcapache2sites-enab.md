---
title: "problem with snakeoil.key and /etc/apache2/sites-enabled/default-ssl"
date: 2012-01-22
forum: Server Platforms
---

### Post by jonny.milano on 2012-01-22
Why does this not work...

user@user:~$ /etc/init.d/apache2 restart
 * Restarting web server apache2
 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
kill: 226: Operation not permitted

Syntax error on line 52 of /etc/apache2/sites-enabled/default-ssl:
SSLCertificateKeyFile: file '/etc/ssl/private/ssl-cert-snakeoil.key' does not exist or is empty
   ...fail!

and this does work??


user@user:~$ sudo service apache2 restart
 * Restarting web server apache2
 ... waiting    ...done.


I have googled this, but i couldn't find anything that would solve this. The server restarts with the second command just fine, but I would like to know what's up here.

---

### Post by agillator on 2012-01-22
Your attempt to start from init.d needs to be sudo (sudo /etc/init.d/apache2 start). If that doesn't work, we'll try again.

---

### Post by jonny.milano on 2012-01-22
wow, and.. i feel like an idiot! i can't believe it.

---

