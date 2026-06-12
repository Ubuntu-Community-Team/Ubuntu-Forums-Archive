---
title: "Website no longer works after phpmyadmin install"
date: 2016-09-24
forum: Virtualisation
---

### Post by sstrate on 2016-09-24
The website on the server does not display, it is located in var/www as a /website sub directory.

 The website stopped displaying, once I installed phpmyadmin.   /phpmyadmin would NOT load. (phpmyadmin conf was symlinked correctly,  etc)


  As a test, I renamed /phpmyadmin to /website and voila.. works  perfectly.  The trouble began once I renamed /website back to its  original directory.  It no longer displays. I uninstalled phpmyadmin, still no luck.  I reset all of the apache2  config files - no luck.


  I've checked all the virtualhost config files, all are pointing to var/www as DocumentRoot.


  Because /website/phpinfo.php loads, as does other .txt files, I'm  wondering how to narrow down the discrepancy.  I've edited php.ini to  log errors, yet none appear - the page is simply white.  If I rename  /website to something else and attempt to load the website, only "File  not found." appears.  
  The directory and files ownership belongs to www-data[33].

---

