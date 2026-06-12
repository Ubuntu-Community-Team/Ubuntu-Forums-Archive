---
title: "Apache help"
date: 2010-08-01
forum: Server Platforms
---

### Post by frankups1 on 2010-08-01
i have had my Ubuntu web/file server up and running for about 18 months now. i do not remember messing with anything but i am not gonna put it past me. basically whats going on is when you go to my website [http://perfectpanorama.com](http://perfectpanorama.com) it asks if you would like to download a file instead of redirecting(?) to index.php. if i type in the whole web address perfectpanorama.com/index.php it works.  any help would be much appreciated.

---

### Post by ub-newbie on 2010-08-01
What files are in your /var/www directory?  Have you added a "Index.htm" file recently?

---

### Post by frankups1 on 2010-08-01
there are a bunch of files mostly .php but no .html files.

---

### Post by Ryan Dwyer on 2010-08-01
Going to index.html does the same thing. Are you sure there's no index.html file? Check your Apache config to see what DocumentRoot it's serving and check that location for index.html.

You've probably installed an update that changed the order of which files are read as the index.

---

### Post by frankups1 on 2010-08-01
here is whats in site-available/default

DocumentRoot /var/www
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

<Directory /var/www/>
Options -Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all

</Directory>

---

