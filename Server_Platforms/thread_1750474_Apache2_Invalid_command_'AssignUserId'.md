---
title: "Apache2: Invalid command 'AssignUserId'"
date: 2011-05-05
forum: Server Platforms
---

### Post by megabuffen on 2011-05-05
I just reinstalled my server with Ubuntu 11.04 and I am now trying to put my websites back in place. The problem is that the configuration directive AssignUserId is no longer working. I simply get this:
```
root@silvertejp:/etc/apache2/sites-available# service apache2 start
 * Starting web server apache2                                                                                                                                Syntax error on line 12 of /etc/apache2/sites-enabled/finn:
Invalid command 'AssignUserId', perhaps misspelled or defined by a module not included in the server configuration
```This worked fine on Ubuntu 10.04. Should I install some module? How? 
Any help would be much appreciated:D

---

### Post by megabuffen on 2011-05-17
It's solved now. All I needed to do was to install the package "apache2-mpm-itk".

---

