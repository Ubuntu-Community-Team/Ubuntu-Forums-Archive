---
title: "Technical Question - vmware and ubuntu server 7.10"
date: 2007-12-19
forum: Server Platforms
---

### Post by Profusion on 2007-12-19
Hi Ubuntu Server Wisemen!

I have a question maybe someone can help me with it or direct me from here. 

I have a home server environment that consists of a single Dell poweredge 1800 server and a single static IP address provided by my ISP.

What im trying to accomplish if it is possible, is to use my VMware sessions as web servers to be accessed from the external single static IP address. I have not problem doing this with virtual servers in apache on a single server, but since this is no longer a single server it is treated as separate servers. How would I make this work with out needing another static IP for each vmware server session?

Currently I have my port DMZ forwarding to my main Ubuntu host Server that provides the other vmware sessions.

Any help with this is much appreciated.

---

### Post by deuce868 on 2007-12-19
Your best bet is to setup one web server to be the front line, and setup apache mod_proxy from there to proxy the external web requests into the multiple internal web servers.

---

### Post by Profusion on 2007-12-19
> **deuce868 said:**
> Your best bet is to setup one web server to be the front line, and setup apache mod_proxy from there to proxy the external web requests into the multiple internal web servers.

Thank you for your advice. I will look into this option.

---

