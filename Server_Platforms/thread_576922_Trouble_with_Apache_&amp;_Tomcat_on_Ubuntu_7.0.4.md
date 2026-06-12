---
title: "Trouble with Apache &amp; Tomcat on Ubuntu 7.0.4"
date: 2007-10-15
forum: Server Platforms
---

### Post by gforce-industries on 2007-10-15
Hi all,

I'm having trouble getting Tomcat to work having installed it from the repository.

* Apache is working fine
* I've installed sun-java6-jdk and set JAVA_HOME in /etc/environment
* I've installed tomcat5.5 and libapache2-mod-jk and followed all of the suggested steps in these threads - [http://ubuntuforums.org/showthread.php?t=565462](http://ubuntuforums.org/showthread.php?t=565462) and [http://ubuntuforums.org/showthread.php?t=436295](http://ubuntuforums.org/showthread.php?t=436295)

The problem I'm having is that when I run /etc/init.d/tomcat5.5 start I'm told that Tomcat has started, but when I browse to [http://localhost:8080](http://localhost:8080) (on that server) I get the standard 'not found' error in my browser. I've also tried port 8180 as recommended in the other thread, and port 80 (having stopped Apache first) all with no luck. I was interested to note that someone pointed out that a modification was required to /usr/local/tomcat/conf/server.xml but on my system the /usr/local/tomcat directory does not exist.

Can anyone suggest what I can do to get Tomcat working correcty (or at all), or even better how to get Tomcat to handle requests for JSP resources through Apache? Let me know if you require more information.

Thanks in advance
Gareth :)

PS

At the bottom of Apache's index listing, the server is shown as "Apache/2.2.3 (Ubuntu) mod_jk/1.2.18 PHP/5.2.1 Server at <IP> Port 80"

---

