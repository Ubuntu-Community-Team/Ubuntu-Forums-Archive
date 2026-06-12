---
title: "Redirect FTP Traffic To Separate Domain"
date: 2007-01-15
forum: Server Platforms
---

### Post by gopig on 2007-01-15
I'm new to Ubuntu and have set up a small box to use as a webserver (6.10 LAMP). I'm currently running an FTP (where the majority of my hard drive space is) on another box at a different IP. I plan to use the webserver to host my site and act as a small fileserver through ssh/scp.

Ideally I'd like to be able to access the webserver through http://domain.com while having ftp://domain.com redirect to the other box's IP. I've been looking around at doing this through the SUSE proxy suite or through Apache but haven't had any luck. It doesn't really matter to me whether it's accomplished through a redirect or a proxy as long as it works with most FTP clients. Is this setup possible?

---

