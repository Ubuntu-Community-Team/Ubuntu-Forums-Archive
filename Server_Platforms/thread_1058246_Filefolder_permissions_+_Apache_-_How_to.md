---
title: "File/folder permissions + Apache - How to?"
date: 2009-02-02
forum: Server Platforms
---

### Post by Poleh on 2009-02-02
Hi Folks

been running ubuntu/apache for some time now, and have finally decided to fix a long outstanding "issue". Issue in that it's me who doesn't know how to do something rather than Ubuntu being broken.

Consider the scenario:

1. Apache with websites residing in
/var/www/www.domain.com/public_html
/var/www/www.domain.com/logs
etc.

Rinse and repeat for all vhosts.

With the default install of Apache/PHP on Ubuntu the apache web server runs as www-data, however the permissions on /var/www are for root:root.

To get around this I have made the following ownership changes on folders:
/var/www/www.domain.com/public_html (user:www-data)
/var/www/www.domain.com/logs (user:www-data)

This allows the www-data user access and hence apache to display the site as well as write the logs. It also allows the user who owns the site to access it via ftp.

My question is, I want to apply these permissions at the /var/www/ folder level, make it so that all sub-folders inherit these ownerships but also (and most importantly) set it so that the ownership cannot be changed.

I looked into "sticky bits" but to be honest can't work out what the hell it's on about and whether it's the right thing for me.

All I want to do is:

chown user:www-data /var/www/somewebsite.com* and make it so the user can't change that ownership ... anyone know how I can do this?

Muchos gracias in advance amigos...

---

### Post by Poleh on 2009-02-03
bumpity bump, surely there must be a chmod/chown guru out there with nothing to do ... ? :)

---

