---
title: "Problems with LAMP install"
date: 2007-10-26
forum: Server Platforms
---

### Post by soopafly on 2007-10-26
Hello all,
I'm a n00b, so go easy on me :-) I've installed 7.10 desktop and was intending to have a living room internet station/server.

I've installed Apache2, and want to install PHP, MySQL, and phpMyAdmin along with it.  I've set the DocumentRoot of Apache to live on a secondary blank drive, rather than the default /var/www.  I then tried installing PHP, MySQL, and phpMyAdmin with apt-get, but I cannot get this to work. Going to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) gets me a 404 error.

I believe that setting a new DocumentRoot in Apache is the culprit.

Can someone help? Thanks!

---

### Post by pkarjala on 2007-10-26
Try setting your DocumentRoot back to the default /var/www and see if this fixes the issue.  If it does, you have something to start from.  :)

---

### Post by adza on 2007-10-26
try creating a symbolic link from your webroot /var/www --> /path to blank drive...

```

sudo ln -s /path/to/blank /var/www

```

hehe, try googling the symbolic link creation first though to ensure syntax is correct (i'm still a rookie myself).. This got my eclipse workspace working sweetly away from my webroot folder....

---

### Post by robert_pectol on 2007-10-26
Forget about symlinking the specified document root to /var/www.  That step is un-necessary.  As long as apache can reach the specified document root (drive is mounted, permissions are appropriate, etc.), Apache is happy.  Now, on to the phpmyadmin issue...

phpmyadmin installs to /usr/share/phpmyadmin (at least mine did) so you'll need to symlink to that location.
```

sudo ln -s /usr/share/phpmyadmin /mountpoint/path/to/document_root

```
Where mountpoint is the mount point of the drive which contains the document root for Apache.  Once you've done that, you should be able to go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and get the login page served up to you.  Good luck.

---

### Post by u_kraze on 2007-10-28
i have the exact same problem and well i tried the symlink cuz other palces said to try it and well when i try to access phpmyadmin from localhost it says i am trying to download a phtml file ???i du nno what that is.

---

### Post by u_kraze on 2007-10-28
I found a way to make it work just follow this guide for now..
> 
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

---

