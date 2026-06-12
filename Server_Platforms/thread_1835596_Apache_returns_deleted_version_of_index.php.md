---
title: "Apache returns deleted version of index.php"
date: 2011-08-29
forum: Server Platforms
---

### Post by bobnw on 2011-08-29
(using Ubuntu 11 with data and web root on an NTFS partition)

I set up a virtual host directory in sites-avaliable/test  using the following Documentroot statement

        DocumentRoot /unb/bob/Dropbox/wdv/test


I changed the an echo statement in  ../test/index.php and saved the file.  Apache is returning the previous version of ../test/index.php.

The following steps did not help:
restart Apache
reload the site in Firefox
access the site using Chrome and Konqueror
reboot

I did a search on contains “index.ph” to make look for other ../test/index.php files on the system.  Onthe changed file showed up. 

The "show hidden files" in the Gnome file manager  exposed a backup copy which I deleted,  but this did not fix the problem.

Any idea on where is the old copy of the index.php is hiding and on how to get rid of it?

Thanks,
Bob N

---

### Post by bobnw on 2011-08-30
My Bad!

I had overwritten the default /var/www/index file.

---

