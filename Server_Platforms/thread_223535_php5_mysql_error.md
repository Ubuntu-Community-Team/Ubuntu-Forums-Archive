---
title: "php5 mysql error"
date: 2006-07-26
forum: Server Platforms
---

### Post by sixspeed on 2006-07-26
Hi, 

I am a little new at this so sorry if alot of information is misunderstood.

i have setup a ubuntu, apache2, mysql, and php5 on a server, i have been trying to simply connect to the server with a php file. it is giving me :

"Fatal error: Call to undefined function mysql_connect() in /var/www/InventoryDatabase/index.php on line 18"

i have read up on this error and i found somethings that relate to it, 

i was told to create a php.info file and see if mysql is listed, but it isn't.
and with the php.ini file uncomment the extention=mysql.so which i have and still no fixes.

any help would be awesome 

Thank you

---

### Post by sixspeed on 2006-07-26
Hi,

i have found a fix to my error. i had to run a command that fix missing extentions

this thread helped me:
[http://ubuntuforums.org/showthread.php?t=221818&highlight=php5+mysql+problem](http://ubuntuforums.org/showthread.php?t=221818&highlight=php5+mysql+problem)

---

