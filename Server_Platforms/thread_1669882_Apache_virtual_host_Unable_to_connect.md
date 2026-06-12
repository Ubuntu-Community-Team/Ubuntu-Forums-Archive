---
title: "Apache virtual host Unable to connect"
date: 2011-01-18
forum: Server Platforms
---

### Post by Ageris on 2011-01-18
Hi

I've set up a server running Ubuntu 10.10 (desktop) with apache. Problem is: When I try to configure multiple virtual hosts I can only access the first one. I'm sure that I'm missing something basic in my setup, but I cannot seem to figure out what.

What I want is simply two virtual hosts, one only available on the LAN where I can test my php files and one "live" available from the outside.

Heres what I've done:
Installed Apache2.2
Copy /etc/apache2/sites-available/default -> /etc/apache2/sites-available/dev
Modified "dev" config DocumentRoot and Document to point to /var/www/dev
Modified "dev" config VirtualHost to <VirtualHost *:1337> (port change right?)
Modified "default" config DocumentRoot and Document to point to /var/www/live
a2dissite dev
a2dissite default
a2ensite dev
a2ensite default
service apache2 restart

Live works fine, but dev cannot connect (as if there is no server there).

Any help would be greatly appreciated!

---

### Post by RobbanC on 2011-01-18
I belive you have to tell Apache to listen also to your other port (1337), so it can be directed to your new virtual server.

That's done in /etc/apache2/ports.conf

---

### Post by Ageris on 2011-01-18
Of course it was something simple.

That did the trick. Thanks a million!

---

