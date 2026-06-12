---
title: "tomcat + apache, how to get 80 for tomcat?"
date: 2007-09-27
forum: Server Platforms
---

### Post by dotku on 2007-09-27
how can tomcat get 80 port without shutdown apache?

---

### Post by jpeddicord on 2007-09-28
No two servers can share a port. If you want Tomcat to use port 80, you will need to change Apache to use another port. The file you will need to edit is /etc/apache2/ports.conf. Restart apache [1] to apply the ports and 80 should open up again.

---

### Post by ato on 2007-09-28
You can use mod_jk

---

### Post by HermanAB on 2007-09-28
There is an explanation on mod_jk2 connector in this guide:
[http://www.aeronetworks.ca/tomcat-howto.html](http://www.aeronetworks.ca/tomcat-howto.html)

Cheers,

Herman

---

