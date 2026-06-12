---
title: "Apache does not gzip .svg files (Ubuntu Server 14.04)"
date: 2014-10-19
forum: Server Platforms
---

### Post by Osvaldo on 2014-10-19
My Ubuntu Server 14.04 does not gzip .svg files. Html, css and JavaScript files are being gziped by default.

How can I set it up to gzip svg files too?

The Apache version is 2.4.7

---

### Post by Osvaldo on 2014-10-20
Is adding this code to default-ssl.conf the most efficient way of doing it?

[FONT=Courier New]AddOutputFilterByType DEFLATE image/svg+xml[/FONT]

---

