---
title: "Request forwarding"
date: 2009-10-15
forum: Server Platforms
---

### Post by WitchCraft on 2009-10-15
Question:

I run a Linux server and a Windows server in a virtual machine.
Is it possible for the apache/lighthttp server on Linux to forward requests for an asp.net site to IIS to the windows server ?

In essence, the user shouldn't see any difference.

e.g. 
you go to page.php on [http://www.mydomain.com](http://www.mydomain.com), there press a link and get forwarded to [http://www.mydomain.com/page2.aspx](http://www.mydomain.com/page2.aspx)

where page.php runs on lighthttp on Linux
and page2.aspx runs on IIS on Windows

---

### Post by t3r0 on 2009-10-15
Yes, its possible. look at apache mod_proxy for details. (lighty can do this also if you want to use it insted of apache)

---

