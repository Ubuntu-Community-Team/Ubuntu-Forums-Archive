---
title: "Questions a/b 'ServerName' and Wordpress"
date: 2007-04-16
forum: Server Platforms
---

### Post by Xarok on 2007-04-16
Ubuntu Server 6.06 with default LAMP server installation.

I'm confused as to how I can change the 'ServerName'. Within Apache's config files I've found no line called 'ServerName' despite many tutorials saying that it exists. 
I've attempted many times to add it throughout Apache's various config files and restarting the server, but it always complains about not being able to find the server name and changes it to the server's LAN IP (192.168.1.111).

When I go to my domain name outside my server's LAN I can see the index page of my site, but when I attempt to access the WordPress section it doesn't get past initial loading of the html file(css files do not load).  I've noticed that if I access WordPress on another computer on my LAN, WordPress works just fine, though the domain name changes to my server's LAN IP.

Example:
**[http://mydomain.com/](http://mydomain.com/)  **
changes to
**[http://192.168.1.111/wp/](http://192.168.1.111/wp/)**
when I access the the wp directory (wordpress directory).

Being new to servers, I don't know what this means.  Will setting Apache's 'ServerName' to 'mydomain.com' fix this?

Thank you so much for any help you can give me.

---

