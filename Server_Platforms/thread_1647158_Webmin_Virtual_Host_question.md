---
title: "Webmin Virtual Host question"
date: 2010-12-16
forum: Server Platforms
---

### Post by franco81 on 2010-12-16
I have webmin 1.530 installed on Ubuntu 10.10, adding virtual hosts, I add a domain like:

mysite.local

To point to a folder like:
/var/www/mysite

The virtual host for localhost still exists and points to:
/var/www

But once I restart Apache2 with the new mysite virtual host created, going to [http://localhost](http://localhost) also points my browser at /var/www/mysite and I am no longer getting the directory listing of /var/www

Any ideas on why the localhost virtual directive is getting 'hijacked'?

---

