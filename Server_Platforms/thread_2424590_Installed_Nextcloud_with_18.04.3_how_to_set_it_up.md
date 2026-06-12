---
title: "Installed Nextcloud with 18.04.3 how to set it up?"
date: 2019-08-11
forum: Server Platforms
---

### Post by mw4jet on 2019-08-11
I have ran Ubuntu server for years, I usually install a basic server and manually install nextcloud, this time I chose to have Nextcloud installed as I was installing the basic OS. 

Now what? All my searches are explaining the install, I need to access the process of setting it up, any help?

I find the Nextcloud folder under /var/snap/nextcloud, is it accessed by html? If so I would need the url


Any help will be greatly appreciated.

---

### Post by LHammonds on 2019-08-11
I have not used Snaps.  I'm not interested in them and cannot tell you how they are setup other than they are intended as a fully-contained system with all required software together.

I run many server and do not want "silo" systems like this (multiple database servers, multiple web servers, etc.)

NextCloud is mainly just a PHP web application that uses a database backend like MariaDB.

You can access and use it entirely via the web interface.  You can also install the sync client for the platform you are on and it will keep your PC/Laptop connected to the server and keep a local folder in sync with what you have on the server.

I have documented how I install a [NextCloud server here](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=254).  But just because you see how the URL works on my install does not guarantee the same URL path will work with the snap install.  You will need to look at the web server configuration to see what port is is listening on (probably 80 but if using SSL, then 443) and what path it is in the URL such as "/" (root) or "/nextcloud" (sub-folder).

LHammonds

---

