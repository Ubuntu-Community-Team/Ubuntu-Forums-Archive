---
title: "install 32-bit packages (jre+mysql) on 64-bit server"
date: 2011-06-06
forum: Server Platforms
---

### Post by alex_sv on 2011-06-06
Hi!

I've rented cheap VPS based on the OpenVZ technology with 64-bit Debian (and there is no option to use 32-bit edition).

I've chosen a pretty cheap VPS option with only 500M RAM and therefore memory is quite a scarce resource.

I'd like to install 32-bit jre and mysql in order to minimize memory consumption because now all the processes barely fitting into the 500M bounds. The memory allocation is as follows:

[FONT="Lucida Console"]
1) nginx:          16M
2) tomcat 6.0.32:  300-350M
3) mysql:          100-150M
[/FONT]

What is the best way to install 32-bit jre/mysql packages on the Debian-based OS?

---

