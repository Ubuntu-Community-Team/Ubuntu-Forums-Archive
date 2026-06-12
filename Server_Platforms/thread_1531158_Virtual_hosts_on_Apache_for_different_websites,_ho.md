---
title: "Virtual hosts on Apache for different websites, howto?"
date: 2010-07-14
forum: Server Platforms
---

### Post by klaasvg on 2010-07-14
Hello,
I am pretty newbie with Apache Webserver under Ubuntu 10.04, I had already some content live but only knew how to put some files in de /var/www directory to set it live.
Now I want some more and have embarked in a tutorial. I have my own domain, drsklaus.nl, and have forward this to the IP address of my provider.
Now I want to make some different sites with their own subdomain like:
site1.drsklaus.nl
site2.drsklaus.nl
intranet.drsklaus.nl

For each of them, I made a copy of the sites-available/default configfile and edited it for each subdomain. For the intranet site, I want to restrict the access to my own private subdomain (192.168.)
I can access the sites using the URL's above, but ALSO via the url drsklaus.nl/site1
This is because the base domain drsklaus.nl maps to the /var/www directory and the other websites reside in subdirectories of /var/www, like /var/www/site1
Am I doing it the right way? What can I do to prevent access to the subdomain sites via the base domain followed by the subdirectory? Can I exclude the subdirectories from access in the default VirtualHost?
TIA, Klaas

---

### Post by Ryan Dwyer on 2010-07-14
Don't put the subdirectories inside the DocumentRoot of the default site. A common method is to use a directory structure like this:

/var/www/sitea.com/public_html
/var/www/sitea.com/subdomains/sub/public_html (sub.sitea.com)
/var/www/siteb.com/public_html

---

### Post by klaasvg on 2010-07-14
Thanx this sounds pretty logical! I will try it. 
Grtz Klaas

---

