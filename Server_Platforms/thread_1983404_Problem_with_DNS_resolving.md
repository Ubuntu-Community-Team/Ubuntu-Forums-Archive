---
title: "Problem with DNS resolving"
date: 2012-05-20
forum: Server Platforms
---

### Post by gsinekliev on 2012-05-20
Hello

I've created and installed site with the apache2 server on Ubuntu 11.04. I host multiple sites and made the settings so that the different sites to be known by their name not address(the address is the same for all sites:)). However i want to change the name  that the site is accessed with so i changed the ServerName in  the relevant <VirtualHost> tag in /etc/apache2/..
I also changed the old name in the hosts file. /etc/hosts
I restarted the machine.
However now the site is accessible with both the new and old name from my browser.  I want to remove the old name because there is a conflict with actual website on the Internet i need;

Thanks:)

---

### Post by gsinekliev on 2012-05-20
Actually the problem was that the browser cache wasn't flushed. Sorry for bothering:D

---

### Post by LHammonds on 2012-05-20
Ya, I've noticed that some browser's "refresh" does not actually do a true refresh.  In Firefox, you have to hit CTRL+F5 to force it to re-download assets (such as updating an image file without changing the path)

---

