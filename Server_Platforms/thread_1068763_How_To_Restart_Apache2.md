---
title: "How To Restart Apache2"
date: 2009-02-13
forum: Server Platforms
---

### Post by mistypotato on 2009-02-13
Can someone tell me how to restart the Apache server on Ubuntu 8.10?

I've tried sudo /etc/init.d/apache2ctl restart

and

I've tried sudo /etc/init.d/apache2 restart


This is the result........

Goddess@MWServer:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
 * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!

 ... waiting Syntax error on line 4 of /etc/apache2/sites-enabled/Myfirtsite:
Invalid command 'Server', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

thx

---

### Post by cdenley on 2009-02-13
The second command is correct. You just need to fix your site configuration file "/etc/apache2/sites-enabled/Myfirtsite".

---

### Post by mistypotato on 2009-02-13
thx!

that did it :)

---

