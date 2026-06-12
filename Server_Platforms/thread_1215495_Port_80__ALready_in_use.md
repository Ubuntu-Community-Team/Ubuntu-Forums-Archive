---
title: "Port 80  ALready in use"
date: 2009-07-17
forum: Server Platforms
---

### Post by Chetan26 on 2009-07-17
Hi,
     Iam trying to run my web application on server  but iam getting foll exception.

 ERROR [Http11Protocol] Error starting endpoint
java.net.BindException: Address already in use:80
	at org.apache.tomcat.util.net.JIoEndpoint.init(JIoEndpoint.java:500)
	at org.apache.tomcat.util.net.JIoEndpoint.start(JIoEndpoint.java:514)
	at org.apache.coyote.http11.Http11Protocol.start(Http11Protocol.java:203



When I check command  netstat -an

netstat -an | grep 80
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.1.1:8083          0.0.0.0:*               LISTEN     


How  can  I resolve the error and get my app running on 80.


Please provide help.


Many thanks
CHetan

---

### Post by heebus on 2009-07-17
Looks like you already have a webserver running.  Are you trying to setup a new version of Apache?  Maybe you're running a different webserver.

Run this command to see whats up.
  sudo fuser -v 80/tcp

Also, I noticed you are trying to startup tomcat on port 80.  Use port 8080 for tomcat.  If you want to have it running on 80 you can have Apache listen on port 8080 and keep tomcat on 80.

---

### Post by philcamlin on 2009-07-17
Are you trying to install a newer version of apache over an older one

Try removing it then install the new one if that's your issue

---

