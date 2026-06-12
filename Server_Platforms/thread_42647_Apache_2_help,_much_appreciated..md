---
title: "Apache 2 help, much appreciated."
date: 2005-06-18
forum: Server Platforms
---

### Post by KingBahamut on 2005-06-18
First time ive dealt with Apache 2. 

Im continuing to get this error msg when I attempt to start apache. 

httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address 1.2.3.4:80
(Where 1.2.3.4 is the IP address of the server on my internal network)
no listening sockets available, shutting down
Unable to open logs


Im relatively sure theres a fairly logical reason for this, but im uncertain how to correct.

---

### Post by LordHunter317 on 2005-06-18
You have something already running on port 80, either another instance of Apache2 or another webserver.

---

