---
title: "Two apache virtual servers are going to the same root folder."
date: 2009-10-14
forum: Server Platforms
---

### Post by kevin11951 on 2009-10-14
In apache, two of my virtual servers (blog and forum) are pointing to blog's root folder. I am using ubuntu 9.04 server ed.  httpd.conf:

```
<VirtualHost *>
DocumentRoot "/var/www/blog.kviero.com"
ServerName blog.kviero.com
<Directory "/var/www/blog.kviero.com">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
<VirtualHost *>
DocumentRoot "/var/www/forum.kviero.com"
ServerName forum.kviero.com
<Directory "/var/www/forum.kviero.com">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
<VirtualHost *>
DocumentRoot "/var/www/kviero.com"
ServerName kviero.com
<Directory "/var/www/kviero.com">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
<VirtualHost *>
DocumentRoot "/var/www/kviero.com"
ServerName www.kviero.com
<Directory "/var/www/kviero.com">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

```

---

### Post by kevin11951 on 2009-10-14
Just got worse, now all of my sites are pointing to the blog root folder! :confused:

---

### Post by kevin11951 on 2009-10-14
I got it working, turns out apache2 needs "NameVirtualHost *" at the top of httpd.conf, and not "NameVirtualHost *:80"

---

