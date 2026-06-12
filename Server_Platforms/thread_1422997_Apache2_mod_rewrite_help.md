---
title: "Apache2 mod_rewrite help"
date: 2010-03-06
forum: Server Platforms
---

### Post by Sotobar on 2010-03-06
Hello,
I am working with 1 Apache2 and 3 Tomcat instances.
I would like to redirect an application , for example /path/to/webapps/mywebapplication ,
to my SSL Port (443).
I want to view this application from my browser only from port:443  ,using the rewrite module!!
Can anyone help ?!
Cheers

---

### Post by raffaele181188 on 2010-03-06
I have not fully understood you... Anyway, I hope it'll help ;)
[Apache configuration]("http://www.cyberciti.biz/tips/howto-apache-force-https-secure-connections.html")
[Tomcat configuration]("http://marc.info/?l=tomcat-user&m=104951559722619&w=2")

---

### Post by Sotobar on 2010-03-06
My English suck.
Anyway,I have read the links you've sent me and the tomcat link was very interesting.
But I am using an Apache as Loadbalancer and 3 Tomcat instances and i would like to redirect: JkMount /a_folder_in_webapps loadbalancer
             JkMount /a_folder_in_webapps/* loadbalancer
using mod_rewrite to port:443.

---

