---
title: "Fatal error: Allowed memory size exhausted"
date: 2009-05-04
forum: Server Platforms
---

### Post by mjfroggy on 2009-05-04
OK,

 I have a php script which works on my other server but now when I try to run it on this new server I just setup with a basic LAMP setup I get a message that says 

 Fatal error: Allowed memory size of 262144 bytes exhausted (tried to allocate 311296 bytes) in /usr/share/phpmyadmin/libraries/common.inc.php on line 794

So my phpmyadmih does not even work so I can setup a data base
even when I try to go to a php script page I get
Fatal error: Allowed memory size of 262144 bytes exhausted (tried to allocate 19456 bytes) in /var/www/myhome/configuation.inc.php on line 30

 I tried editing my php.ini file I have it set to 16MB which is the max php can run and still get this error??
 I tried even uninstalling php and re-installing via apt-get remove and then apt-get install ... and still have same issues.

So I need a point in the right direction

thanks

---

### Post by nquinnathome1 on 2009-05-05
I've had a similar issue moving a MediaWiki installation from 8.10 to 9.04; I fixed it in the interim by allocating more memory to the script that was complaining (actually editing the memory allowed in the script file itself); changing the global PHP memory allocation (right up to 512MB) made no difference to the error. It must be a bug though; the wiki installation was an exact copy; files, database et al.

---

