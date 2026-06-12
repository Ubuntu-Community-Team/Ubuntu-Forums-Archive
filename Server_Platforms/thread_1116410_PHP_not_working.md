---
title: "PHP not working"
date: 2009-04-04
forum: Server Platforms
---

### Post by pat23_2007 on 2009-04-04
Hi everybody

I have recently set up a home http server, I installed PHP5, Apache2 mySQL, Curl, SSH, and PHPMYADMIN. 

The problem is when I go to [http://localhost/](http://localhost/) and click on test.php it asks if I want to save the file or to open it. 

How do I get PHP5 to work?

Thank You in advance.

---

### Post by pat23_2007 on 2009-04-04
Never mind adding the line:

AddType application/x-httpd-php .php

to the httpd.conf fixed it.

---

