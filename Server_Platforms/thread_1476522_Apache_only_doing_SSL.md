---
title: "Apache only doing SSL"
date: 2010-05-07
forum: Server Platforms
---

### Post by JigglyWiggly_ on 2010-05-07
So I followed this
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration](https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration)

And this

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration](https://help.ubuntu.com/8.04/serverguide/C/httpd.html#https-configuration)


How when I view my web page, it is only doing HTTPS
I want https to run on port 443, and default running on port 80.

Is this possible? In IIS I remember doing 1 year ago.

---

### Post by JigglyWiggly_ on 2010-05-07
Nevermind, just make a new directive in /etc/apache2/sites-available and like make a different virtual host in webmin for the different ports.

---

