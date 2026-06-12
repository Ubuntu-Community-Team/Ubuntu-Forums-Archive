---
title: "Apache userdir permissions in Ubuntu 9.10 X64"
date: 2010-03-07
forum: Server Platforms
---

### Post by runes on 2010-03-07
By default the  install of apache sets the user to www-data for /var/www which is fine when you chown all the files  to www-data, reads and writes from a php portal such as Joomla will work without requiring ftp server to upload files.   

I've enabled .htaccess and tested basic authentication so I know at least .htaccess files will work in the users public_html folders.

The problem is, when I  create a user, it is copying the default install files from /etc/skel/ to the users home folder (default permissions are 755) but after configuring the portal (regardless of whether it is Joomla, Drupal or E107) the user has only read acces to their files and folders through the portal.  If I change the owner to www-data:www-data then they have full access...not the perfect solution by far.

I thought maybe chown user:www-data might work but I didn't want to make any more changes without seeing what the recommended procedure is.

Without changing the user:group in each users public_html folder, how can I give them the rights to modify their files?

---

