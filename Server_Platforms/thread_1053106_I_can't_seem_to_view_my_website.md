---
title: "I can't seem to view my website"
date: 2009-01-28
forum: Server Platforms
---

### Post by Fertech on 2009-01-28
I'm running ubuntu 8.10 apache, and i restart the apache. is there something im missing. i did had my website running a few days ago, but don't know what happen.

```
fertech@fertech-desktop:~$ sudo /etc/init.d/apache2 restart
[sudo] password for fertech: 
 * Restarting web server apache2                                                 ... waiting ..                                                          [ OK ]
fertech@fertech-desktop:~$ 
sudo a2ensite default
Site default already enabled
fertech@fertech-desktop:~$ 




```


for get it. i sloved the problem, i had the wire plug into the wrong nic card.

---

