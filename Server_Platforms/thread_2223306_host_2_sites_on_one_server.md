---
title: "host 2 sites on one server"
date: 2014-05-10
forum: Server Platforms
---

### Post by Devan_Phillis on 2014-05-10
I have sucessfully setup the 2 virtual servers for my sites but now i need to know how to get their domains to point to the right place please help.
Thank You
KD8MST

---

### Post by Lars Noodén on 2014-05-10
You want to set up name-based virtual hosts in your web server.  Both domains can point to the same ip number.  Are you using Apache2 or nginx?  And which version of Ubuntu are you using?  The defaults are a little different in 14.04.

---

### Post by Devan_Phillis on 2014-05-10
Using Apache2 and 14.04

---

### Post by Lars Noodén on 2014-05-11
I guess you have the DNS entries all set.  That would depend on your registrar anyway. 

Have you had a look at the 14.04 server guide's section on Apach2 name-based virtual hosts?

[https://help.ubuntu.com/14.04/serverguide/httpd.html](https://help.ubuntu.com/14.04/serverguide/httpd.html)

---

