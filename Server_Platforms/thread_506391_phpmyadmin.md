---
title: "phpmyadmin"
date: 2007-07-21
forum: Server Platforms
---

### Post by lugos on 2007-07-21
Hello,

I've installed phpmyadmin on my Ubuntu 7.04 LAMP server, but when I try to access it using localhost/phpmyadmin, I get a 404.  I have set my default directory as /var/www/mydomain.com, so when I look at the error log I see the following: 'File does not exist: /var/www/mydomain.com/phpmyadmin'.  When I actually look at my directory structure, mydomain.com and phpmyadmin are on the same level, they are at /var/www/.  I had the directory structure set up this way on my last Ubuntu LAMP server and it worked, but I can't seem to remember how I configured it.

Any help would be greatly appreciated.

---

### Post by sunset_studies on 2007-07-22
sudo  ln -s /usr/share/phpmyadmin/ /var/www/mydomain.com/phpmyadmin 

might work...

---

### Post by lugos on 2007-07-22
Thanks for the response.  My fear is exposing it to others.  On my old machine phpmyadmin was one directory level up from the default directory so I could only get to it from localhost.  Because I did it before, it must be something with the configuration files.  I couldn't find anything when I searched the forum before, but I'll try again.

---

### Post by astralsin on 2007-07-24
if you cant figure out the problem, just try reinstalling it.  you may have missed some information important to the operation of it during the install.

---

