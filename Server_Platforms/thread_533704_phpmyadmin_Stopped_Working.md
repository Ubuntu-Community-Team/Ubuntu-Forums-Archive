---
title: "phpmyadmin Stopped Working"
date: 2007-08-24
forum: Server Platforms
---

### Post by jlacroix on 2007-08-24
phpmyadmin was working, now it's not. When I try to visit my installation, I get this message:
"Wrong permissions on configuration file, should not be world writable!"

That leads me to believe that it is a permissions issue, but the error doesn't tell me what file(s) I need to change the permissions on, and what the permissions should be changed to.

I tried doing:
```

sudo apt-get remove --purge phpmyadmin

```
And then I tried installing it again, but I got the same message.

This is probably easy for you guys but its got me stumped.

---

### Post by GigaVolt on 2007-08-24
chmod 644 /usr/share/phpmyadmin/config.inc.php

---

### Post by jlacroix on 2007-08-24
Thanks, I ran that command, and I am still getting that error. :(

---

### Post by trtech on 2007-08-24
Where is config.inc.php?

Try:

```
sudo updatedb
locate config.inc.php
```

and post output.

---

### Post by jlacroix on 2007-08-24
Here is the output that I get.
```

/var/lib/phpmyadmin/config.inc.php
/var/lib/ucf/cache/:etc:phpmyadmin:config.inc.php
/var/www/deltawo/phpmyadmin/config.inc.php
/var/www/ironwo/phpmyadmin/config.inc.php
/usr/share/phpmyadmin/config/config.inc.php
/usr/share/phpmyadmin/config.inc.php
/usr/share/ucf/phpmyadmin/etc/phpmyadmin/config.inc.php
/etc/phpmyadmin/config.inc.php

```

---

### Post by trtech on 2007-08-24
lol -- well, we need to figure out which of those is being used.

Do you know where your site's document root is? Like where do you put php and html files for your site?

If you don't know, you can try checking your apache config. Are you using virtual hosts (i.e. more than one site) on the server?

-Chris

---

### Post by jlacroix on 2007-08-24
From looking at my own output as seen above, I removed phpmyadmin from the directories /var/www/ironwo and /var/www/deltawo, it was not supposed to be there. Now it doesn't work at all, my IP address for my server is 10.1.2.85 and I use 10.1.2.85/phpmyadmin to get to phpmyadmin, but the page can't be found.

I guess I need to know how to point phpmyadmin to my server now. :(

---

### Post by trtech on 2007-08-24
10.1.2.85 looks like a LAN IP address to me, but not necessarily the same computer you're on. Do you know where 10.1.2.85 is? Is it your local machine?

---

### Post by jlacroix on 2007-08-24
10.1.2.85 is the local lan address of the webserver. The webserver will only be responsible for an intranet page that would not be viewable by others outside the network.

---

### Post by GigaVolt on 2007-08-25
chmod 777 -R /usr/share/phpmyadmin/config

---

### Post by jlacroix on 2007-08-27
Now I'm getting a new error:
"The requested URL /phpmyadmin was not found on this server."

I reinstalled phpmyadmin several times and this error won't go away.

---

### Post by jlacroix on 2007-08-28
It works now. For some reason I had to install and configure phpmyadmin manually with a howto I found on Google. Thank you for your help.

---

### Post by mandeep kaur on 2007-08-29
Hi,

We have phpldapadmin in our office. By mistake I had deleted admin account, Could you please help me to create it again. Due to this we are not able update the addresses. Please help me.

Thanks & Regards

Mandeep Kaur

---

