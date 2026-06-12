---
title: "Apache virtual hosts"
date: 2006-04-04
forum: Server Platforms
---

### Post by Swab on 2006-04-04
I'm trying to configure a sub-domain in apache.  Following the wiki I created a file called /etc/apache2/sites-available/development  then added the following:

<VirtualHost *>
        DocumentRoot /data/development/
        ServerName development.localhost

        <Directory /data/development/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

Then I issued a sudo a2ensite . Sym link was created in sites-enabled.  

However when I try to access the site by doing something like wget [http://development.localhost/index.html](http://development.localhost/index.html)   I get a 404: Not Found error.  

Examining the error.log shows that apache was looking for the index.html file in the wrong place:

[Tue Apr 04 20:39:46 2006] [error] [client 192.168.1.5] File does not exist: /var/www/index.html

Any idea where I'm going wrong here?

---

### Post by Swab on 2006-04-04
OK, panic over.. it was just a permissions issue! doh!

---

### Post by alkalined on 2006-05-06
[QUOTE=Swab]OK, panic over.. it was just a permissions issue! doh![/QUOTE]

I have the exact same problem!
Would you care to share what was the permissions issue about?

---

### Post by Swab on 2006-05-06
Basically I had the wrong permissions for my /data/development/ directory... can't remember exactly what it was now, sorry!

---

### Post by alkalined on 2006-05-09
Anyway, I used the a2ensite script this time and all was fine. I guess it has setup the right permissions.

---

