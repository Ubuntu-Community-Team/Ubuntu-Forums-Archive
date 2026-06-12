---
title: "Subdomain for phpmyadmin to set up PHPBB"
date: 2009-04-12
forum: Server Platforms
---

### Post by mjdiaz89 on 2009-04-12
Hello,

I am trying to install phpbb on my server (8.10 Intrepid), but I keep getting a MySQL server error ("Could not connect to the database, see error message below. Unknown MySQL server host 'domain.com/phpmyadmin/"). I think this is cause by phpmyadmin not being accessed from a subdomain.  I only have SSH connection to my server and much Googling has yielded articles that need graphical access to my server (which again, I don't have). I made a subdomain, mysql.domain.com that points to /usr/shar/phpmydomain, but when I access it, it only shows the "it works!!" page from APACHE.

This is what I added to httpd.conf:
```

NameVirtualHost *
<VirtualHost *>
ServerName mysql.domain.com
DocumentRoot /usr/share/phpmyadmin/
</VirtualHost>

```

That's all my httpd.confg file contains.

Umm... I also made an A record of mysql.domain.com using my server IP address.

domain.com/phpmyadmin/ works perfectly fine, meaning the mySQL server is up 'n runnin'

all php5, apache, phpmyadmin, MySQL-server libraries have been installed via apt-get install

So how else do I get my subdomain to work right so PHPBB can acknowledge my MySQL server?


Thank you for your time

---

### Post by apel_2804 on 2009-04-12
Setup the virtual host in /etc/apache2/sites-available/default. Reload apache.

---

### Post by BkkBonanza on 2009-04-12
Two things to note here. If the virtual host directives above are not being found by apache (due to being misplaced) then you will get the default server directory for any subdomains. So that is likely why you get the it works page. And once it gets to the correct directory for your subdomain make sure that the config.inc file for phpmyadmin has the correct absolute url set so that it will know it's location. If not then it will keep trying to redirect to the incorrect url, probably the one on your main domain.

---

