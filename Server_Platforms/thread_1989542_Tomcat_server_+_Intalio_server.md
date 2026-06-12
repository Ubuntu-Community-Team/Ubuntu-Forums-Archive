---
title: "Tomcat server + Intalio server"
date: 2012-05-28
forum: Server Platforms
---

### Post by PiniFloyd84 on 2012-05-28
I installed the version of tomcat from the packages and I need to start Intalio server (still using tomcat). I set a different port for Intalio, using the groovy script inside, only when I start  intalio the first server is stopped and intalio correctly use the alternative port. How can I get these two instances of tomcat start simultaneously (I can not join them for other reasons)?

---

### Post by PiniFloyd84 on 2012-05-29
Solved. I use this guide [http://www.hiteshagrawal.com/apache/running-multiple-apache-tomcat-on-same-machine](http://www.hiteshagrawal.com/apache/running-multiple-apache-tomcat-on-same-machine). Need to change redirect port and shutdown port.

---

