---
title: "apache2 directories, simple question"
date: 2008-09-12
forum: Server Platforms
---

### Post by [pl]ice on 2008-09-12
hi guys,
 i setup torrentflux through apache2, but i'm having hard time blocking other folders the example is:

/var/www/
/var/www/torrentflux/
var/www/otherstuff/

i have full indexing running.

I would like to allow full access from outside to /var/www/ and torrentflux
but deny /var/www/otherstuff/
i tried that way:

<Directory /var/www/>
Order Deny,Allow
Deny from all
</Directory> 
  will block whole site, good. So

<Directory /var/www/>
Order Allow,Deny
Allow from all
</Directory>

<Directory /var/www/otherstuff/>
Order Deny,Allow
Deny from all
</Directory> 
    This will still allow access to otherstuff. I know that the right of /var/www/ is working for the subdirectories. But i don't know what to do.

 Please advise. Its early hours right now :) I guess when i wake up, i'll manage more, and bout to time to take the apache book into hands!!!

thank you so much!!!

Polish

---

### Post by inphektion on 2008-09-12
swap them

<Directory /var/www/otherstuff/>
Order Deny,Allow
Deny from all
</Directory>

<Directory /var/www/>
Order Allow,Deny
Allow from all
</Directory>

---

