---
title: "Is Tomcat running?"
date: 2007-10-16
forum: Server Platforms
---

### Post by purban on 2007-10-16
Hello. I'm a Linux newbie working on new installation of Ubuntu Server 7.04. I have installed Tomcat using the tomcat5.5 package. Everything seemed to go fine during this installation. Howevere, when I try to access using http://<ipaddress>:<port> I get a message "Internet Explorer cannot display the webpage." I have tried accessing locally using localhost and tenet-ing to the IP and port -- all without success. Did I not install Tomcat correctly because I used the package manager? I see some different instructions here - [http://ubuntuforums.org/showthread.php?t=44006](http://ubuntuforums.org/showthread.php?t=44006).

How can I tell if I installed Tomcat correctly and if it is running?

Thanks!
-Peter

---

### Post by sgordon on 2007-10-26
Well,
ps -ef | grep java
should show a process running

Even better would be
netstat -an | grep <port>

For some reason tomcat 5.5 on ubuntu uses a different port from the usual 8080, I think it's 8180, so:

netstat -an | grep 8180

what are you using when accessing using web browser. If my port above is right, you should be using [http://localhost:8180/](http://localhost:8180/)

Good luck, will try to check the port number a bit later.

  Si

---

