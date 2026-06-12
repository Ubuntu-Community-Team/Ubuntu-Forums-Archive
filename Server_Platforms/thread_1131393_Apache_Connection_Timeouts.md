---
title: "Apache Connection Timeouts"
date: 2009-04-20
forum: Server Platforms
---

### Post by matt912836 on 2009-04-20
Right now im running Webmin on a dedicated computer running Ubuntu at home. The connection I have is a 30mbps downstream and 5mbps upstream. Im starting to have problems with apache and accessing the site. At any time for a few minutes, I cant access any page at all. I try to visit the site but nothing wants to go through, and then after a few refreshes or waiting a minute or two, the site works just fine, pages loading instantly. Then when it goes back 'down' i just get a "page taking to long to load" error or connection timeout error. When I access other things like the webmin panel on a different port it loads up instantly just fine, while apache doesnt want to respond, and im able to connect through remote desktop just fine, so im not thinking its my connection. The server isnt under any load (plenty of ram available 300MB out of 2GB used, barely any cpu usage), and the confusing part is that when im able to actually access the site, pages load up instantly. Also, while apache doesnt respond when im trying to connect to the external IP, when i load up localhost on the server in a web browser, it loads up instantly... Any help? The site is sidekickprofiles.com

---

### Post by matt912836 on 2009-04-21
Bump.. really need help with this

---

### Post by Spikerok on 2009-04-21
hi, was it working before? I think i know how to solve your problem

---

### Post by Spikerok on 2009-04-21
your computers are using same connection?
if they do then you are accessing webmin and remote desktop locally.
First thing to do is to check if your server(connection, modem, router) does not blocks connections.
here is useful website to check externally, if you have any firewall problems..
[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)
here you need to check if any ports are blocked.. 
apache port is 80

---

### Post by matt912836 on 2009-04-21
Everything is already set up, ports are forwarded and opened. Its actually not hosted in my home so I have to access everything 'remotely', everything but apache isnt effected like apache is. It started once users started using the site and such.

The weird part about this is that when the site doesnt have connection timeouts, all the pages load up instantly and fine, and the slow connection problems go and come every few minutes

---

