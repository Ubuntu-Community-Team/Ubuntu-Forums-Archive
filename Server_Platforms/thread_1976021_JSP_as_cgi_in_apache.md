---
title: "JSP as cgi in apache"
date: 2012-05-08
forum: Server Platforms
---

### Post by aditya3098 on 2012-05-08
I want to use both an apache2 and tomcat on the same port. Can I create something like a cgi handler for jsp files?

---

### Post by aditya3098 on 2012-05-10
Anyone?

---

### Post by Sergius14 on 2012-05-11
? I'm not sure what are you trying to do or mean, but using Apache/Tomcat on the same machinne is posible but on diferent ports.

BUT

I'm guessing what you need is the AJP connector. With it, all .JSP .JSF requests are forwarded to the Tomcat engine (usually runing on tcp 8080 while Apache http engine runs on 80).

---

