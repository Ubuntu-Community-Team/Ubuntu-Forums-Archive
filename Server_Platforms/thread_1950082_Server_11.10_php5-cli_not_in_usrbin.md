---
title: "Server 11.10 php5-cli not in /usr/bin/"
date: 2012-03-31
forum: Server Platforms
---

### Post by kadeous on 2012-03-31
I've setup my server using 11.10, did a fresh installation and setup LAMP manually installing each package and configuring apache. The issue that I'm having is php5-cli is installed and current but not located in /usr/bin/php or php5, the directory isn't created. I removed and re-installed php5-cli but still no luck.

Any ideal why this is happening?

---

### Post by dharmavir on 2012-04-03
I think you should try going to root folder and then do a search by typing:
 $ sudo find | grep php-cli 
or something similar, I hope that should help.

---

### Post by SeijiSensei on 2012-04-03
On my machine /usr/bin/php is a symlink pointing to /etc/alternatives/php which points to /usr/bin/php5.

I'm not sure why you think a directory needs to be created.  /usr/bin/php5 is a binary file; the other two objects are symbolic links.

What do you see when you run "php -v" from the command line?  You should get a banner with versioning information.

---

### Post by kadeous on 2012-04-03
Thank you both the grep returns nothing, but php -v shows that php is installed with CLI support and it should work.

---

