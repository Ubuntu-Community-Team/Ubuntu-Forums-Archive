---
title: "Apache2 not reading the config file"
date: 2010-06-12
forum: Server Platforms
---

### Post by grizdog on 2010-06-12
Just installed apache2, and added a DocumentRoot directive to httpd.conf, then to apache2.conf - both are /etc/apache2, just where the installation left them.  When I stop and then start apache2, using 'service", neither file is read, as determined by 'ls -alurt', and the document root does not change.  Nothing in the logfiles.

Any ideas?

Thanks

---

### Post by Ryan Dwyer on 2010-06-12
It's highly unlikely you want your DocumentRoot to be /etc/apache2. If you configure it like that then your webserver will be serving its configuration files to the user when you browse to it!

That said, it's probably setting the DocumentRoot but then the virtual hosts are overriding it (in /etc/apache2/sites-available/default).

EDIT: I just re-read your post and realised I probably misinterpreted the part when you said "both are /etc/apache2". Ignore my first paragraph. And I don't know why ls -alurt isn't showing the files being read.

---

### Post by grizdog on 2010-06-12
Yes, that was it.  Thanks.

---

