---
title: "[SOLVED] Ports 80 and 443 open by default?"
date: 2008-11-17
forum: Security
---

### Post by HDave on 2008-11-17
Hi -- I have a new install of Intrepid and went to [www.grc.com]("www.grc.com") to do a port scan.  It's reporting that both port 80 (http) and 443 (shttp) are open.

Why is this?  I am not running a web server (that I know of).

Should I close them?  How can I?

---

### Post by cdenley on 2008-11-17
> **HDave said:**
> Hi -- I have a new install of Intrepid and went to [www.grc.com]("www.grc.com") to do a port scan.  It's reporting that both port 80 (http) and 443 (shttp) are open.

Why is this?  I am not running a web server (that I know of).

Should I close them?  How can I?

If you haven't installed a web server, then that site is seeing your router's web server, or a web server which the router is forwarding traffic to.

---

### Post by HDave on 2008-11-17
> **cdenley said:**
> If you haven't installed a web server, then that site is seeing your router's web server, or a web server which the router is forwarding traffic to.

You are right. I installed nmap on another machine on my LAN and sure enough, all ports are closed.  

Thanks.

---

### Post by sirjoebob on 2008-11-17
Mark thread as solved.

---

