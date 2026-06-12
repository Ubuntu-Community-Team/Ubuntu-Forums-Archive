---
title: "Multiple websites with Apache 2 showing same after Joomla installed"
date: 2010-12-18
forum: Server Platforms
---

### Post by Kainwolf on 2010-12-18
I have a fresh build of an Ubuntu 10.04 server, with Apache 2 installed.

The following is added to /etc/apache2/sites-available/default file (a replacement for this portion of httpd.conf?):
```
<VirtualHost *:80>
  ServerName [www.domain1.com](www.domain1.com)
  ServerAlias domain1.com
  DocumentRoot /home/web/domain1.com/www
</VirtualHost>

<VirtualHost *:80>
  ServerName [www.domain2.org](www.domain2.org)
  ServerAlias domain2.org
  DocumentRoot /home/web/domain2.org/www
</VirtualHost>
```
I had a slightly modified index.html page in each directory, and sure enough, when I visited each site, the correct index.html page will load for each.

Now, I installed Joomla 1.5.22 in /home/web/domain1.com/www and it works fine.

The problem is, now when I visit [www.domain2.org](www.domain2.org), the Joomla installation comes up, though under the url of [www.domain2.org](www.domain2.org).

The sites-available file is unchanged, the only thing I can think of is that there is some other file that changed something somewhere, to change a universal document root to the document root of domain1.com - but I can't find it.

Even after removing the domain2.org block from sites-available and restarting Apache, [www.domain2.org](www.domain2.org) still points to the Joomla installation and [www.domain2.org/index.html](www.domain2.org/index.html) points to /home/web/domain1.com/www/index.html

---

