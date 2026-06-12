---
title: "FastCGI and Apache"
date: 2010-04-11
forum: Server Platforms
---

### Post by DayTripper on 2010-04-11
Hi all,

I have made a clean install of Ubuntu server 10.04 Beta2
Then I intalled Apache using: sudo apt-get install apache
Next I installed FastCGI using: sudo apt-get install libapache2-mod-fastcgi

Both steps went without any problem, but I run into problem when trying to setup FastCGI with fastcgiexternalserver.

I only want to use Ubuntu as a apache web server, while FastCGI application is running on Windows PC.

So I put this on Ubuntu apache2.conf (IP .6 is Win PC with FasctCGI application):
fastcgiexternalserver cgi-bin/DemoSite –host 192.168.0.6:2018 –idle-timeout 60

While this is working just fine on WinXp apache server (I wrote that line in httpd.conf), I can't get it working with Ubuntu apache server. 

Can anybody give me any clues? Thanks.

Regards

---

