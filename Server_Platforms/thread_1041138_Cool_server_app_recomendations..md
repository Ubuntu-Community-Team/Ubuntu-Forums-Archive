---
title: "Cool server app recomendations."
date: 2009-01-16
forum: Server Platforms
---

### Post by Grout58 on 2009-01-16
Hey guys, I just built a server and installed Ubuntu server 8.10.
I am looking for some recommendations for some cool server apps to run on it.  Currently im running ampache, webmin, phpsysinfo, and torrentflux.  I know theres probably a ton more stuff you can do with the server besides the obvious(Mail, http)  

What are your guys favorite?

---

### Post by Thirtysixway on 2009-01-16
I run [Folding@Home]("https://help.ubuntu.com/community/FoldingAtHome") on my server.  I also have vmware (you could use something like virtualbox or qemu if you wanted) to setup virtual machines.

Munin is another thing I have installed to track performance of the server/components (although I don't think I configured it right...)

Make sure you also install "uprecords" so that you can track your system's uptime records.  And mysql/php/proftpd will let you run more applications that are web based.

Oh and if you feel like exploring other web servers, you can try things like nginx, lighttpd, etc.

---

