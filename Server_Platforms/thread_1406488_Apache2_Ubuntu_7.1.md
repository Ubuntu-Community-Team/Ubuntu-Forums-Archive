---
title: "Apache2 Ubuntu 7.1"
date: 2010-02-14
forum: Server Platforms
---

### Post by josmcc on 2010-02-14
I have password protected a webpage in apaches default root as it comes set up which works. I use the AuthUserFile AuthType <Files "blah.html> require user blah </File> etc.. I am specifying this under the <Virutal Host> setting in /etc/apache2/sites-available/default

This works just fine, however when I try to password protect another file located under another virtual host it doesn't work. ( I have several virtual hosts up and running just fine). Any suggestions please. I am pretty new to apache and also linux in general so please bear with me.

I have also tried with a .htaccess file in the directory with AllowOveride All in the <Virtual Host>

---

