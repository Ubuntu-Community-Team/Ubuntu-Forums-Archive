---
title: "website mystery..."
date: 2010-08-23
forum: Server Platforms
---

### Post by darkapec on 2010-08-23
Here is the setup, ubuntu 10.04 LAMP server, webmin remote gui and shorewall. My router is the well known wrt54g with ddwrt installed on it. I have the website working, the domain name is [www.darkapec.com]("http://www.darkapec.com"), I can access it fine from any of the intranet computers. I can access it by typing [www.darkapec.com]("http://www.darkapec.com") i can access it by typing 192.168.1.125, it will even show up if i type in my routers ip address. However if I try to access the website off my network (with cell phone, friends computer, wifi hotspot) the website says it timed out and cannot be displayed. And to top everything off if I am at the hotspot and I type [www.darkapec.com:1000/]("http://www.darkapec.com:1000/") sure enough the webmin login will show up and it works fine. I was thinking it was a router problem at first. But I dmz port forwarded almost every port and still the same situation. I have setup all the ports on shorewall (i think) I have put ports 80, 8080, 22 and 10000. There all setup for both UDP and TCP. Any ideas?? Is there permissions that need to be changed??

Thanks

---

