---
title: "Kolab SSL Issues"
date: 2010-08-08
forum: Server Platforms
---

### Post by Stewart9643 on 2010-08-08
Hi

I'm not sure if it should be here or newbies but here I go.

I've done a basic install of Lucid Server.
I created my own certs as per the ubuntu server guide and then installed Kolab. 
I appear to have an issue with the SSL configuration for Kolab preventing a HTTPs access.
 
nc: connect to 127.0.0.1 port 443 (tcp) failed: Connection refused
operations@ZUES:~$ sudo a2enmod ssl
[sudo] password for operations:
Module ssl already enabled
operations@ZUES:~$ sudo a2ensite default-ssl
Enabling site default-ssl.
Run '/etc/init.d/apache2 reload' to activate new configuration!
operations@ZUES:~$ sudo /etc/init.d/apache2 reload
Syntax error on line 17 of /etc/apache2/sites-enabled/kolab:
SSLCertificateFile: file '/etc/kolab/cert.pem' does not exist or is empty
   ...fail!
operations@ZUES:~$ sudo service apache2 restart
 * Restarting web server apache2                                                Syntax error on line 17 of /etc/apache2/sites-enabled/kolab:
SSLCertificateFile: file '/etc/kolab/cert.pem' does not exist or is empty
                                                                         [fail]

Any suggestions.
Thanks
Stewart

---

### Post by carolinason on 2011-09-29
me too

---

