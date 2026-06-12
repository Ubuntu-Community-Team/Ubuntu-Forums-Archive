---
title: "Apache 2.2 with SSL"
date: 2009-05-27
forum: Server Platforms
---

### Post by wonderingwout on 2009-05-27
Hi,

I installed a SSL certificate on my Ubuntu Apache2 Server.
The certificate installed but I'm a bit stuck with the Apache configuration.

When I try to start apache with SSL enabled I get this error:

The startssl option is no longer supported. Please edit httpd.conf to include the SSL configuration settings and then use apachectl start. 

Chan anybody give me a quick tip on how to solve this?

---

### Post by cyborg2912 on 2009-05-27
Hi.
The 'startssl' argument is no longer supported by ApacheCtl. Using the 'start' or 'restart' should initialize the ssl module if it is configured correctly.

good luck!

---

### Post by wonderingwout on 2009-05-28
Ah ok, I got it working now.
Thanx for your reply.

---

