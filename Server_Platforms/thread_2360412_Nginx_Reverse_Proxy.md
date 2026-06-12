---
title: "Nginx Reverse Proxy"
date: 2017-05-04
forum: Server Platforms
---

### Post by condatis on 2017-05-04
Hello,
im am currently testing the nginx webserver and i try to get a reverse proxy working to reach the domain: **myDomain:8090** through **wiki.myDomain**

I saw many articles for this topic in the net but nearly all are pointing using nginx with apache to solve this. Is there a reason for that ?
I was in the opinion that nginx can handle something like that independend from apache.

Thank you :)

Greetings

---

### Post by TheFu on 2017-05-04
Are they on different machines? Is there a webapp involved on myDomain:8090?  If either of those are true, then some other server is necessary.  That could be another instance of apache, nginx, plackup, starman, or any other webserver/WSGI tool.

If both are on the same machine and no web-app server is needed, no need for any other webserver.

---

### Post by condatis on 2017-05-04
Thank you for your reply !
It is all on one machine. The myDomain:8090 is a webApp Tomcat (attlasian Confluence).
Should this be possible with only Nginx ? Or is there a reason why apache is needed ?
I try to avoid the system performance which is needed for apache to run.

---

### Post by TheFu on 2017-05-04
Is apache required for tomcat to run?  We don't use java where I work.

---

