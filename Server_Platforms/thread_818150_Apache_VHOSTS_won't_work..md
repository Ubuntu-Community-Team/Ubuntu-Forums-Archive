---
title: "Apache VHOSTS won't work."
date: 2008-06-04
forum: Server Platforms
---

### Post by Ignite_nz on 2008-06-04
So, I followed the perfect guide for a server on HowtoForge for Ubuntu 8.04, and installed ISPConfig. Everything on my server works, EXCEPT, Whenever I go to any of my websites, all I see is

"It work's!"

Apache has vHosts etc setup, but for some reason they aren't registering. Here's all my Apache configs:

[http://pastebin.org/40542](http://pastebin.org/40542)
[http://pastebin.org/40544](http://pastebin.org/40544)

I'm aware I'm being very vauge here, but with the massive amount of information I could be providing, it's best probably to provide what is asked. I've provided the above to start off with, and will give more if needed.

---

### Post by eak on 2008-06-04
do you make dns option ?? on ispconfig

---

### Post by Ignite_nz on 2008-06-04
Yes. I've made the DNS on ISPConfig, and it shows up in Bind, and I can see all the records fine. This is some description of Apache problem. It's not parsing the header for some stupid reason.:confused::confused:

---

### Post by spiderbatdad on 2008-06-04
I have always used virtual hosts in the virtual hosts directory: /etc/apache2/sites-available/my_site.  "It works!" is the default file from /var/www as specified by /etc/apache2/sites-available/default.

Create /sites-available/your_site. Copy /default to /your_site, then edit appropriately. 

```
sudo a2dissite /etc/apache2/sites-available/default
sudo a2ensite /etc/apache2/sites-available/your_site
```

/sites-available/* is symlinked to /sites-enabled when a2ensite is run.

---

### Post by Ignite_nz on 2008-06-06
I found the problem.

I was binding to a public IP, but I was behind a router -_-;;

---

