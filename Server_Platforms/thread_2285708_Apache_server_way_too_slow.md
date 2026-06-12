---
title: "Apache server way too slow"
date: 2015-07-08
forum: Server Platforms
---

### Post by Xiayang_Fan on 2015-07-08
I have Apache 2.4 set up on my Ubuntu 14.04 and right now it is way too slow. Like its taking 3-5 minutes to load a webpage on the server. I tried several suggestion online, like disabling certain modules, switching mpm, and editing the apache2.conf and mpm configuration files. I need htaccess for the /var/www/html directory so I have AllowOverride All under the <Directory /var/www > tag in the conf files. In the mpm configuration files, I lowered the MaxRequestWorkers (which was formerly called MaxClients) as per some suggestions. I also increased MaxConnectionsPerChild from 0 in the mpm configuration files as well. Unfortunately, nothing I'm doing seem to be having any effect in speeding things up. Does anyone have tips on how to approach this? Thanks!

---

### Post by gordintoronto on 2015-07-08
Is Ubuntu (server or desktop?) running in a VM? Without a description of your computer, it's hard to say what you should expect.

---

### Post by nerdtron on 2015-07-08
Is the server not busy when you're trying to load the webpage? Can can also view the error log and access on /var/log/apache2 to see what happens when you load the page.

---

### Post by TheFu on 2015-07-08
You've probably seen this already: [https://httpd.apache.org/docs/2.4/misc/perf-tuning.html](https://httpd.apache.org/docs/2.4/misc/perf-tuning.html)
Also - setup monitoring on the server so you know what is holding up the performance. Something like munin should take less than 10 min to setup.

---

