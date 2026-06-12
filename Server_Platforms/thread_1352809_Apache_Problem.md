---
title: "Apache Problem?"
date: 2009-12-12
forum: Server Platforms
---

### Post by njschwartz on 2009-12-12
I recently decided to build a new server to serve my personal web page. I had been doing the same with an older computer for over a year with no problems. The old server was running Ubuntu 8. After setting up and installing an Ubuntu 9.10 LAMP server, I am having a strange issue. 

Basically, if I attempt to access my site directly after the install I get the default apache page and everything works just fine both locally and over the internet. However when I attempt to put my old site back up, or even add code to the default index.html file it stops working.  I can still access the site from my local network with no problems, but if I try to access the site externally it times out. This very well may be a router issue, however it worked before and it works as long as the index.html page is relatively simple so I don't really understand. I even tried placing the server in the DMZ of the router to see if it would work and no dice. The site for those that may wish to help test things is [www.nateandstephie.com](www.nateandstephie.com). I am at a loss and would appreciate any assistance anyone can offer.  

Nate

---

### Post by FoXoF on 2009-12-12
If you haven't already, try reading through apache's error log, might show what's wrong.

/var/log/apache2/error.log

---

### Post by niklasn on 2009-12-12
Have the same problem since yesterday after upgrading to 9.10 (kernel 2.6.31.17) from 9.04.

The inner nic works fine, but the outer nic does not respond at all. This applies to both apache and sshd.

---

