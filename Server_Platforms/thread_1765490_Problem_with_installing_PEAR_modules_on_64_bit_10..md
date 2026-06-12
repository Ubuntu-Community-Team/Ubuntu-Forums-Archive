---
title: "Problem with installing PEAR modules on 64 bit 10.04.2"
date: 2011-05-23
forum: Server Platforms
---

### Post by mormops on 2011-05-23
Hi All,

I'm running Ubuntu x86_64 10.04.2  Server on a quad core Xeon and am having problems installing the php PEAR modules required to run EGroupware.

If I try to install PEAR modules using "pear install <module-name> it fails with the following error:

 
pear install XML_Feed_Parser                                                                                                               

Notice: Array to string conversion in PEAR/REST/13.php on line 80
PHP Notice:  Array to string conversion in /usr/share/php/PEAR/REST/13.php on line 80

Warning: Invalid argument supplied for foreach() in PEAR/REST/13.php on line 84
PHP Warning:  Invalid argument supplied for foreach() in /usr/share/php/PEAR/REST/13.php on line 84
PHP Fatal error:  Cannot use string offset as an array in /usr/share/php/PEAR/REST/10.php on line 263

Originally, it also had a line warning about using # to mark comments  in imap.ini being deprecated but a ; at the beginning of the commented line cured that.

Any PHP/Pear gurus out there that have fixed  the same problem?

Cheers,

Jools

---

### Post by mormops on 2011-05-23
Turns out Ubuntu's pear installation doesn't get its proxy settings from the system wide $http_proxy variable. 

Instead, set the proxy settings using the command:

pear config-set http_proxy http://<proxy_ipaddress>:<proxy_port>

---

