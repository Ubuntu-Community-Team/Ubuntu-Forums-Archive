---
title: "php in Apache [warty]"
date: 2005-04-11
forum: Server Platforms
---

### Post by lizardking on 2005-04-11
I have tryed to install apache2 and the php module using this guide...
[guida php](http://ubuntuguide.org/4.10/index.html#installphpapache) 

but Apache 2 works perfectly **but not php module**.When I do [http://localhost/testphp.php](http://localhost/testphp.php) firefox try to open the file with gedit...I have tried to search in the forum and I find a similiar topic but the solution was not that of this problem...

some help?
 :roll:

---

### Post by HungSquirrel on 2005-04-11
I had php working fine on my server with minimal effort.  Check for php4.conf and php4.load symbolic links in /etc/apache2/mods-enabled/ .  They should point to files in /etc/apache2/mods-available/ .  Check to make sure the files they point to exist.

---

### Post by lizardking on 2005-04-11
[QUOTE=HungSquirrel]I had php working fine on my server with minimal effort.  Check for php4.conf and php4.load symbolic links in /etc/apache2/mods-enabled/ .  They should point to files in /etc/apache2/mods-available/ .  Check to make sure the files they point to exist.[/QUOTE]
I have no symbolic links in /etc/apache2/mods-enabled... about php

I added this links and then reload apache but nothing..

this is my problem [http://ubuntuforums.org/showthread.php?t=24738&highlight=php+apache](http://ubuntuforums.org/showthread.php?t=24738&highlight=php+apache)

---

