---
title: "Rights on /var/www folder so Joomla may function right"
date: 2008-06-03
forum: Server Platforms
---

### Post by cellv14 on 2008-06-03
Hey!
I got the classic /var/www problem.
Joomla cant write or anything in it it seems. Cant install new modules or plugins. So what can i do about this?

Been searching around the forums but no answers came up..:(

Running ubuntu 8.0.4 server with lamp setup.

---

### Post by adamos on 2008-06-03
If you are installing Joomla 1.5 you will run into problems..
Install proftpd and create a user.
then add this user in your joomla installation.

look at [www.adamos.us](www.adamos.us) and read How to setup FTP layer for Joomla 1.5

---

### Post by iLoVe.cF- on 2008-09-15
sudo chmod 777 or something on the /var/www/ folder worked for me, i suspect its not the correct way... i'm working on it, you can install by doing the chmod.

Tip

Chmod -R 777 or 775 or whatEVER it was, howto chmod on google does it for ya.

just sudo chmod -R xxx /var/www/

---

### Post by cariboo on 2008-09-15
Have a look at his chart of directory permissions:

[http://www.netadmintools.com/art560.html](http://www.netadmintools.com/art560.html)

Jim

---

### Post by yaddoshi on 2011-04-13
I've been fighting with Joomla 1.6 and I appreciate your links.  However, instead of chgrp apache, I had to chgrp www-data to get it all working.  I also had to chmod g+w the entire directory and disable the FTP layer in the site configuration.  It's all groovy now.

Thanks again!

---

