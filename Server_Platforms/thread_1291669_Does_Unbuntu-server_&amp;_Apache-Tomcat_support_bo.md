---
title: "Does Unbuntu-server &amp; Apache-Tomcat support both JSP -AND- PHP on a single server?"
date: 2009-10-15
forum: Server Platforms
---

### Post by --Steve on 2009-10-15
Does the unbuntu-server and Apache-Tomcat support both JSP -AND- PHP on a single server?

I'm not getting anywhere with searches and suffering from information overload and just want to know (yes or No).  But any/all replies and links will be greatly appreciated.  


So are Apache and Tomcat two separate stand-alone servers or is Tomcat a component installed into Apache?   


It is my understanding that Apache supports PHP but it is Apache-Tomcat that enables JSP development, so when I install my unbuntu-server am I going to simply install/set-up Apache-Tomcat or will first need to set-up Apache then set-up Apache-Tomcat?   Assuming a flawless/correct install, am I then going to have a webserver that will understand both JSP -AND- PHP?


Additional information...

Version: ubuntu-9.04-server-i386.iso

Objective: be able to develop JSP and PHP on an Unbuntu-server set-up with Apache-Tomcat.  I believe (but not sure) that I don't need Unbuntu-server to do this, but still prefer to load and develop with  the Unbuntu-server OS rather than the Unbuntu-GUI OS.     

Background: I have burned to CD and booted and verified the 9.04 ISO file (ubuntu-9.04-server-i386.iso).  I'm still reading through the documentation but would just like to know if I'm headed in the right direction to achieve my objective.  

Thanks,  --Steve

---

### Post by t3r0 on 2009-10-15
Yes, its possible.

Apache httpd and apache tomcat are separate software.

If you have two IPs in your server apache can listen to one and serve php pages and tomcat will serve jsp pages from the other ip.

If you have only one ip then you need to setup apache to listen that ip and tomcat to listen an internal ip (localhost) on a port other than 80 (eg. 8080) and use apache mod_proxy to forward some locations to tomcat ( => localhost:8080)

---

### Post by --Steve on 2009-10-15
Thank you sir, that helps me very much.     

Maybe when I install I could also configure both to only start manually.   I am not creating a server that will be connected to the internet, I only want to develop and learn on it at home.  

Thank You!

---

