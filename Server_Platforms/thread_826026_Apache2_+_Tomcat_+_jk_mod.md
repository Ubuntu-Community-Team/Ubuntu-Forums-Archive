---
title: "Apache2 + Tomcat + jk_mod"
date: 2008-06-11
forum: Server Platforms
---

### Post by vtec on 2008-06-11
I have apache configure with two virtual hosts. I have tomcat set up to work with one of the hosts. In the virtual host that is using tomcat I have 'JkMount /* eas'. In this configuration everything works fine. I have a webapp called EAS that I can access by going to localhost/EAS. However I would like to have the webapp accessed by going to localhost/webapps/EAS, and have apache provide static html to anything not in webapps. To do this I thought all I had to do was change Jkmount to 'JkMount /webapps/* eas'. When the system is configured like this I do have static html outside of webapps, but tomcat can't seem to find my EAS app. localhost/webapps/EAS is just a blank page, this is true for any address in the webapps directory. Does anyone know what is going on here. The logs do not show any errors???

---

### Post by datajelly on 2008-08-12
vtec,

I'm not sure if it will help, but we have setup Apache to be able to proxy requests for our Tomcat server. You should be able to setup Apache so that it handles static content, and proxies any JSP/servlet requests over to Tomcat. I'm not familiar with JkMount, but perhaps you would want to read over how we've configured out Apache/Tomcat setup and see if it might help?

[http://blog.datajelly.com/2008/08/using-apache-front-end-with-tomcat-for.html]("http://blog.datajelly.com/2008/08/using-apache-front-end-with-tomcat-for.html")

---

