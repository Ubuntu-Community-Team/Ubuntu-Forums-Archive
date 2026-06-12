---
title: "How to redirect from apache web server to tomcat"
date: 2008-04-02
forum: Server Platforms
---

### Post by Bjerrum on 2008-04-02
I have a ubuntu server running with apache2.2 and tomcat6 as a standalone. How do I redirect jsp and servlets request to tomcat from apache.

Is there a build in function or do i need a connector like mod_jk?

---

### Post by Atomsmasher on 2008-04-23
Bjerrum, did you figure this out?

I downloaded the mod_jk binary.  There was one for Apache 2.0.61 that I used.

I followed all the steps in the Apache documentation for setting up my connector, but I'm still having problems.  

It can't find any of my servlets and instead Apache is saying "/var/www/..." does not exist, as if its looking for a static page for the URL.  I'm wondering if it's because that latest Apache package I have installed is 2.0.55.

---

