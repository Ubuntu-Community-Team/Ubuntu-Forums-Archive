---
title: "Document Types for Web Server"
date: 2009-02-28
forum: Server Platforms
---

### Post by lightningrod66 on 2009-02-28
Not sure where this should be posted, so I apologize if this is the wrong area.

I have a LAMP server with Ubuntu Server 8.10.  My root web directory is /var/www.  I have an index.html page in there now, and if I browse to "http://www.yoursite.com" the index.html page is displayed.  If I replace the index.html file with an index.**php** page and browse to "http://www.yoursite.com" then a dialog box comes up asking if I want to open or save the index.php file.  I have to actually type in "http://www.yoursite.com**/index.php**" in order to display the page.  Is there a problem with my php setup?  Or is it something with apache? Please help if you can.

---

### Post by ad_267 on 2009-02-28
Have a look at /etc/apache2/mods-available/dir.conf, it should have index.php included in the list and look something like:

```
<IfModule mod_dir.c>
    DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>

```

---

