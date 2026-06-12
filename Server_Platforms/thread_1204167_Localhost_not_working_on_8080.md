---
title: "Localhost not working on 8080"
date: 2009-07-04
forum: Server Platforms
---

### Post by gaaurav_singh on 2009-07-04
Hi,

My name is Gaurav Singh, I was working on PHP for last 6 months and my localhost was working fine..but today i have installed an application (ERP)Openbravo needs apache-tomcat i have configured almost everything and this ERP is working very fine..it is running on port 8180..

BUT not i am unable to run my default [COLOR="black"][COLOR="Navy"]"localhost:80"[/COLOR][/COLOR] this throws the error..

[I][Failed to Connect
Firefox can't establish a connection to the server at localhost.][/I]

when i tried .. **sudo /etc/init.d/apache2 restart**

 [COLOR="Red"]* Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:8180
no listening sockets available, shutting down
Unable to open logs
                                                                   [fail]
[/COLOR]


One more thing All this happens after i have installed tomcat..
Kindly Suggest what to do..


Thanks in Advance
Gaurav

---

### Post by CrusaderAD on 2009-07-04
Try connecting to the servers ip address instead of localhost:

1.1.1.1:80

---

