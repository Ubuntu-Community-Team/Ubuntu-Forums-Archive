---
title: "Server - Memory problem"
date: 2011-12-16
forum: Server Platforms
---

### Post by brunoskrebs on 2011-12-16
Hi there,

I have a Ubuntu server 10.04 LTS installed on a machine that has 1GB of ram memory. The main purpose of this server is to hold Tomcat 6 and Postgres 8.4, which both start automatically on startup.

In the beginning my server has a total of 380MB of memory ram used, but after a few days it goes to 1GB of memory used, i.e. all memory (swap memory is almost never used).

I don't really get any errors and the server still answers quite fast, but since I'm willing to deploy a few more applications on this Tomcat+Postgres I'm worried that this will start to happen.

After this days (when all memory is used) if I stop both Tomcat and Postgres my server still stays with 700MB of memory being used.

Any idea on what could that be? Is it something that is going wrong with Tomcat/Postgres or is it another daemon?

Thanks in advance!

Bruno

---

