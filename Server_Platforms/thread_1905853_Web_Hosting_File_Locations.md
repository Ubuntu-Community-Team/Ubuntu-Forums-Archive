---
title: "Web Hosting File Locations"
date: 2012-01-07
forum: Server Platforms
---

### Post by lenwood on 2012-01-07
Hi All, I just signed up for a VPS and followed their [published instructions]("http://library.linode.com/lamp-guides/ubuntu-10.04-lucid") to get a LAMP stack configured. So far so good, everything seems to be working. I just realized that the server is sending some visitors to the "website" in /var/www. Can someone help sort this out?

[http://website.com](http://website.com) goes to /srv/www/website.com/public_html (this is what I want)

[http://www.website.com](http://www.website.com) goes to /var/www (this is incorrect)

Calling the site by IP address also goes to /var/www (this is incorrect)

Can someone help me sort this out? Seems like it should be simple, but I've read the documentation again, as well as the [howto]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") on the Ubuntu site, and this is eluding me.

---

### Post by Dangertux on 2012-01-07
Did you follow the step in the documentation they published entitled "Configure Name-Based Virtual Host"

That should solve your problem.

---

### Post by lenwood on 2012-01-07
Thanks for prompt reply. I had followed their steps, but as I was going through the steps again realized that I hadn't set the 'default' file within sites-available. I've updated that file, and now no matter how you access the site you end up in /srv (which is what I want). Thanks again.

---

### Post by Dangertux on 2012-01-07
> **lenwood said:**
> Thanks for prompt reply. I had followed their steps, but as I was going through the steps again realized that I hadn't set the 'default' file within sites-available. I've updated that file, and now no matter how you access the site you end up in /srv (which is what I want). Thanks again.

No problem , glad it all worked out for you :-)

---

