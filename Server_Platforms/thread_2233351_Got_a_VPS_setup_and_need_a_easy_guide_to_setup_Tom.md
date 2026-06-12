---
title: "Got a VPS setup and need a easy guide to setup Tomcat as default web service"
date: 2014-07-08
forum: Server Platforms
---

### Post by Nixforce on 2014-07-08
Hi,

Ive signed up for a VPS and have Ubuntu 14.04 LTS (Trusty) (x86_64) as the OS. Im going to use it for myself, no clients on it. I need to setup Tomcat on it as I develop using CFML, and plan on installing the OpenBD server on tomcat. Does anyone have a simple guide to setup tomcat on port 80, so its my default webserver.

Thanks

Glenn

---

### Post by nerdtron on 2014-07-08
When you run sudo apt-get install tomcat6, the tomcat service will be automatically installed. You can confirm that it is running when you point you web browser to [http://ServerIPaddress:8080](http://ServerIPaddress:8080)
If you want to change the port from 8080 to port 80, look at this link. [http://stackoverflow.com/questions/4756039/how-to-change-the-port-of-tomcat-from-8080-to-80](http://stackoverflow.com/questions/4756039/how-to-change-the-port-of-tomcat-from-8080-to-80)

---

