---
title: "just me having problems with cacti ?"
date: 2006-03-12
forum: Server Platforms
---

### Post by rich on 2006-03-12
I followed the howto in the wiki, but (after a series of events routed in my incompetence) I kept getting an error on the webpage [http://localhost/cacti](http://localhost/cacti)

Permission denied in /usr/share/cacti/site/include/config.php on line 29

This is the line
require('/etc/cacti/debian.php');


 ls -l /etc/cacti
total 8
-rw-r--r--  1 root root     539 2006-03-12 14:18 apache.conf
-rw-r-----  1 root www-data 132 2006-03-12 14:18 debian.php


So, I 

sudo chmod a+r /etc/cacti/debian.php


It then showed me the install screen and all seems well. However, I'm left slightly confused by the whole thing. Has anyone else had similar problems ?

cheers,


Rich

---

