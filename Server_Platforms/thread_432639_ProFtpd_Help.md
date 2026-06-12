---
title: "ProFtpd Help"
date: 2007-05-04
forum: Server Platforms
---

### Post by mattc908 on 2007-05-04
When I installed ProFTPd fine. As soon as it was done installing it says

ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

Im not sure what to check in my configuration?

---

### Post by gabkdlly on 2007-05-04
It has been a while since I used proftpd.

If I remember correctly, the default configuration is pretty restrictive for security reasons.
You have to edit it or replace it with one that works.
They have some example configurations on their website

[http://www.proftpd.org/docs/example-conf.html](http://www.proftpd.org/docs/example-conf.html)

Take a look at what is in /etc/proftpd
Those files are pretty well commented.
Or, if you would like a graphical user interface to help you, try out gproftpd

Hope that helps.

---

