---
title: "Slow Web Server"
date: 2007-02-19
forum: Server Platforms
---

### Post by simonbowen on 2007-02-19
Hi,

I am fairly new to the linux and especially to the Ubuntu community. I have been loving the experience I have been having over the past couple of months running Ubuntu as a desktop and a server. Its been surprisingly easy to convert from Windows. Anyway, onto my problem.

I am running a Ubuntu server with Apache2, MySQL 5 and PHP5. Things seem to be running really slow when it is serving webpages. I first noticed this when I tried access TorrentFlux which runs on this server. Since I had phpmyadmin install on there as well I thought I'd test the speed that delivered, but it was just as slow to load.

I am after some pointers on where I should look to find the source of this problem? Any help would be really appreciated!

Simon

---

### Post by exp0zed on 2007-04-14
I'm experiencing similar issues, the odd part is phpmyadmin is fairly quick and all other pages (PHP) pages load fine, its just an issue when attempting to connect to MySQL it has issues.

---

### Post by fmtech on 2007-04-17
I've recently installed  MySQL Server on a brand new Dell server and it supposed to be lightening fast it was slower then the older box and at some point it the web server lost connection to the MySQL server. 

Doe's anyone know why the MySQL server runs so slow on the Ubuntu (Server version) and how  it can be fixed?

---

### Post by chartman on 2007-05-03
Very similar problem here. I was running dapper before and never had an issue. After the upgrade to feisty some of my pages (php5, apache2,mysql) take ages to load.  System process list shows mysqld using 50% of the CPU. Any ideas or help welcome!!!

---

### Post by coxy on 2007-06-05
I have the same issue on a Debian 4.0 (Etch) server. It was running fine and now it is really slow. I have a wordpress site on the server.

---

