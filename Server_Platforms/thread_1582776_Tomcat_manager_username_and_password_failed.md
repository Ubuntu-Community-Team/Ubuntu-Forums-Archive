---
title: "Tomcat manager username and password failed"
date: 2010-09-27
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-27
I have tomcat 5.x installed and is running on port 80(with mod_jk setup). The directories 'manager', 'examples' and 'ROOT' were removed under /usr/share/tomcat/webapps/ and rebuilt them copying from a working tomcat server. When I acces [http://localhost:8080/manager/html](http://localhost:8080/manager/html) (or) [http://localhost/manager/html](http://localhost/manager/html), it keeps on prompting for the password even after enter correct username and password.

---

### Post by Thyagaraj on 2010-09-27
I got it solved. There were entries for tomcat ldap url authentication in the server.xml file and just removed it.

---

