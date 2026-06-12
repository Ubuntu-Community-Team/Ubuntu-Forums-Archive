---
title: "Apache/WordPress help please"
date: 2011-12-08
forum: Server Platforms
---

### Post by AlanRogers on 2011-12-08
I'm configuring a WordPress installation on an Ubuntu server. I've correctly installed Apache2, MySQL, PHP and WordPress - I can see the web site at [http://90.155.89.153/](http://90.155.89.153/) but not at [http://www.counselling-in-surrey.co.uk/](http://www.counselling-in-surrey.co.uk/)

I've set up the site in /var/www, /etc/apach2/sites-available and enabled it. The error message is ```
Neither /etc/wordpress/config-www.counselling-in-surrey.co.uk.php nor /etc/wordpress/config-counselling-in-surrey.co.uk.php could be found. 
Ensure one of them exists, is readable by the webserver and contains the right password/username.
```

I fairly certain that I'm missing something fundamental but I can't see what it is. All help appreciated.

---

### Post by a2j on 2011-12-08
its looking for files in /etc/wordpress and not in /var/www/

can you show your virtual site config?

---

### Post by AlanRogers on 2011-12-08
Screenshot attached [IMG]http://dl.dropbox.com/u/13924519/VirtualHost.png[/IMG]

---

