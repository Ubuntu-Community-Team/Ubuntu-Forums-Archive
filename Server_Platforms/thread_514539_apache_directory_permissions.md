---
title: "apache directory permissions"
date: 2007-07-31
forum: Server Platforms
---

### Post by jman623 on 2007-07-31
I am trying to install phpmyadmin, but after untarring the file, I try to access it via the browser to install it, but apache says it;s forbidden, I have rw for all, the user apache and group apache own it, am I missing something?

---

### Post by Maxtorm on 2007-08-01
You can install phpmyadmin via apt-get and the permissions should be set correctly automatically:
```
sudo apt-get install phpmyadmin
```
On my install, it set these to root:root, which may not be ideal.  If you have a specific reason for installing from the tar file, perhaps changing the owner to www-data would work?  I believe it is the apache user.  

Lastly, where did you untar it?  Under a default install, it should be under /var/www/

---

