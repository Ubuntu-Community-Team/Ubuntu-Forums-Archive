---
title: "[desktop] PHP scripts don't run, but get downloaded."
date: 2010-08-04
forum: Server Platforms
---

### Post by compiz addict on 2010-08-04
I can't get PHP  to work properly with my apache2 server.

I've tried adding this to the empty httpd.conf file:
```

AddType application/x-httpd-php .php3 .php
AddType application/x-httpd-php-source .phps

```

but that didn't work. Also, there are no apparent php related files in /etc/apache2/mods-enabled

Any ideas?

---

### Post by einstein on 2010-08-04
I had this problem a short while ago.  I never figured out precisely what the problem was but it had to do with web sites served from a user's home directory, e.g., /home/user/public_html/.  I put the files under /var/www and the problem went away.

- Dennis

---

### Post by Vegan on 2010-08-05
Did you install the fill LAMP stack?

```
sudo tasksel
```

and select LAMP

---

### Post by cdenley on 2010-08-05
Remove anything you added to httpd.conf, then make sure apache's php5 module is installed and enabled.
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by cdenley on 2010-08-05
Sorry, the site gave me a proxy error, so I didn't think my post went through.

---

### Post by compiz addict on 2010-08-05
Dennis:
My files are already under /var/www so that wont work.

Vagen:
I tried that, but it still doesn't work.

cdenly:
"libapache2-mod-php5 is already the newest version." is what I get when install it, and then at the same time:

```

eric@eric-desktop:~$ sudo a2enmod php5
ERROR: Module php5 does not exist!

```

So at this point I don't know what to do. I'll try reinstalling "libapache2-mod-php5".

---

### Post by cdenley on 2010-08-06
```

ls -l /etc/apache2/mods-available/php5.*
dpkg-query -S php5.*

```

---

