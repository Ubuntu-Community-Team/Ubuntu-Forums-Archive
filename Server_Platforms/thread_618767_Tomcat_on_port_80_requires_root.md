---
title: "Tomcat on port 80 requires root?"
date: 2007-11-20
forum: Server Platforms
---

### Post by TurboRush on 2007-11-20
Hello,

I am a relatively new to Linux. I've played with it here and there over the years but am now jumping in head first, but please go easy on me, I tried to search... :)

I have a small web app that I am playing around with. I installed Tomcat and changed the port it listens to from 8080 to 80, simple enough. However, when I try to startup Tomcat as a non-root user I get the following error:

SEVERE: Error initializing endpoint
java.net.BindException: Permission denied:80

So, this is probably obvious to all of you, but I researched and it appears that I cannot bind to ports below 1024 without root access. This seems like a security risk... do I have any options? Is this a real security risk? or should I be comfortable doing "sudo ./startup.sh"?

I have NO sensitive data on the computer... I just don't want the hassle if I get hacked.

Thoughts?

---

### Post by sciurus on 2007-11-22
"jsvc has other useful parameters, such as -user which causes it to switch to another user after the daemon initialization is complete. This allows, for example, running Tomcat as a non privileged user while still being able to use privileged ports. "

[http://tomcat.apache.org/tomcat-5.5-doc/setup.html](http://tomcat.apache.org/tomcat-5.5-doc/setup.html)

---

### Post by steve.horsley on 2007-11-23
So you can launch jsvc as root, and after it has opened port 80, you can have it change user to a lower priviledge user. This is a common thing for *nix services to do.

Alternatively, you can configure iptables to mangle incoming connections to port 80 and change them so they are addressing port 8080 instead. But changing user after launch is the preferred way to do it.

---

