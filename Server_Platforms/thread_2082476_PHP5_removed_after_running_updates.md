---
title: "PHP5 removed after running updates"
date: 2012-11-09
forum: Server Platforms
---

### Post by Loggy on 2012-11-09
This has just happened to my 10.04 LTS server.  Everything running smoothly, nginx as a reverse proxy and apache handling all php via mod_php5.  

The packages updated overnight were:

An update to apache2 from 2.2.14-5ubuntu8.9 to 2.2.14-5ubuntu8.10 is needed.
This update has been successfully installed.

An update to apache2-mpm-prefork from 2.2.14-5ubuntu8.9 to 2.2.14-5ubuntu8.10 is needed.
This update has been successfully installed.

An update to apache2-utils from 2.2.14-5ubuntu8.9 to 2.2.14-5ubuntu8.10 is needed.
This update has been successfully installed.

An update to linux-libc-dev from 2.6.32-44.98 to 2.6.32-45.99 is needed.
This update has been successfully installed.

The symptom was that the visitor was asked to download something, clearly apache wasn't handling php!

After some moments of panic after restarting apache and seeing a permissions comment, so looking for a permissions problem, I tried a2enmod php5 and was told the module didn't exist.  Funny so I reinstalled it and it started working again.

Removing php on a working server is pretty dire!

Is this a glitch in the update system?

---

### Post by svandragt on 2012-11-15
This just happened to me via weekly updates on my LTS server. (Ubuntu 10.04.4 LTS)

fix:
```
apt-get install php5 php-pear
apache2ctl restart
```

The following packages that were updated I had in common with Loggy's list:
> An update to apache2 from 2.2.14-5ubuntu8.9 to 2.2.14-5ubuntu8.10 is needed.
This update has been successfully installed.

An update to apache2-mpm-prefork from 2.2.14-5ubuntu8.9 to 2.2.14-5ubuntu8.10 is needed.
This update has been successfully installed.

An update to apache2-utils from 2.2.14-5ubuntu8.9 to 2.2.14-5ubuntu8.10 is needed.
This update has been successfully installed.

An update to linux-libc-dev from 2.6.32-44.98 to 2.6.32-45.99 is needed.
This update has been successfully installed.



---

