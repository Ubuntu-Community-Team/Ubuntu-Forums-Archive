---
title: "Tomcat via the Web?"
date: 2010-01-18
forum: Server Platforms
---

### Post by SoulMazer on 2010-01-18
Okay I'm trying to access a .jsp page that is located on my apache/tomcat server from the web. I changed the connection port of tomcat to port 80 and changed my doc root from the default "webapps" to my normal web directory. However, whenever I try to visit the page, I only see the code of the page.

If you would like to see what I am talking about, feel free to see it for yourself:
[http://patbriggs.net/jsp/test.jsp]("http://patbriggs.net/jsp/test.jsp")

What can I do to fix this?

Thanks in advance.

---

### Post by volkswagner on 2010-01-19
I never used TomCat, but have you looked into the vhost documents.  I am not sue what version you are using but check out the steps [vhost for TomCat 6.0.]("http://tomcat.apache.org/tomcat-6.0-doc/virtual-hosting-howto.html")

---

