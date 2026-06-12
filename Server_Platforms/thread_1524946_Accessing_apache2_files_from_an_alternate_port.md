---
title: "Accessing apache2 files from an alternate port"
date: 2010-07-06
forum: Server Platforms
---

### Post by kslacker on 2010-07-06
I recently setup apache2 to listen on port 8000 in addition to port 80. This was done to bypass my ISP's blocking of port 80 incoming traffic.

When I visit [http://mysite.com:8000](http://mysite.com:8000), I see my site and the page works. However, when I try to visit one of the subpages (example: [http://mysite.com/test/index.html:8000](http://mysite.com/test/index.html:8000)) I get an error that it cannot find the desired page. At the bottom of the 404 error page in Firefox it lists the following error Apache/2.2.14 (Ubuntu) Server at mysite.com Port 80.

1) Why is it using port 80 and not the port that I have specified?
2) Why am I not able to access subfolders or other files on my domain via a different port? How can I make these files accessible to the web via this alternate port?

---

### Post by GreenN00b on 2010-07-06
Use [http://mysite.com:8000/test/index.html](http://mysite.com:8000/test/index.html) instead of [http://mysite.com/test/index.html:8000](http://mysite.com/test/index.html:8000)

---

### Post by kslacker on 2010-07-07
Thanks. That solved the issue. I figured it was something simple.

---

