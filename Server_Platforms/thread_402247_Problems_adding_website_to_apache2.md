---
title: "Problems adding website to apache2"
date: 2007-04-05
forum: Server Platforms
---

### Post by vmikalinis on 2007-04-05
Hi I hope someone can help me,

I am trying to add a website to an installation of apache2.  There are already several websites that are functioning correctly on that server.

They are listed in the /var/www/virtuals directory.  The website has been physically added to this directory, I then added it to /etc/apache2/sites-available and ran a2ensite which added a link in the /etc/apache2/sites-enabled directory.  All of the files in all of these directories are almost identical to the sites that are currently working except for their names and the website names.

I restarted apache2 and the new site is still not accessible by [www.name.com](www.name.com).  I can type in the IP of the server and the virtual folder name on apache2 and get to it.

I thought it might have something to do with the name being unable to be found so I continued on to edit the bind files such as /etc/bind/named.conf.local and /etc/bind/zones/nameofsite.com

I restarted bind and the site is still not accessible.  

I have never used a apache2 server with virtual folders like this before.  I hope someone could please lend me some assistance.   :confused:

---

### Post by vmikalinis on 2007-04-09
After much research and testing I realized that I had a couple of typos in my /etc/bind/named.config.local file.

Make sure your brackets are {}   not () and you'll be fine :?

---

