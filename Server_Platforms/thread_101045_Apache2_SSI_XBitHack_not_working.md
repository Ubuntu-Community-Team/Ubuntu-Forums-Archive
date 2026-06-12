---
title: "Apache2 SSI XBitHack not working"
date: 2005-12-08
forum: Server Platforms
---

### Post by cowb0y on 2005-12-08
I'm trying to configure SSI on Apache2 (2.0.54) on Breezy. I've got .shtml working, but can't get XBitHack to work. vhost config: ```
 <Directory /> Options -Indexes -FollowSymLinks AllowOverride None </Directory> <Directory /var/www/[mydir]> Options MultiViews +Includes AllowOverride None Order allow,deny allow from all XBitHack on </Directory> 
``` Tried it with XBitHack in one or the other dirs, or both. Also tried ```
XBitHack full
```. error.log: ```
 [Thu Dec 08 23:25:24 2005] [notice] SIGHUP received. Attempting to restart [Thu Dec 08 23:25:24 2005] [warn] NameVirtualHost *:0 has no VirtualHosts [Thu Dec 08 23:25:24 2005] [notice] Apache/2.0.54 (Ubuntu) configured -- resuming normal operations 
``` ls -l index.* ```
 -rwxr-xr-- 1 root root 3431 2005-12-08 22:35 index.html -rwxr-xr-- 1 root root 3362 2005-12-08 01:30 index.shtml 
``` snip of index.html source (from Firefox or Konqueror) ```
 <!--#echo var="DATE_LOCAL" --> 
``` snip of index.shtml source (from Firefox or Konqueror) ```
 Thursday, 08-Dec-2005 23:33:40 EST 
``` Clearly .shtml SSI is working, but XBitHack SSI is not. I've reviewed all the Apache2 docs and tutorials on SSI and XBitHack that I've found, and it all seems very straightforward. I've even tried adding ```
 AddType text/html .html AddOutputFilter INCLUDES .html 
``` to my vhost config. If anyone has a clue or suggestion, it would be most welcome.

[RESOLUTION]
Well, it turns out that I was accessing the files directly (like [http://localhost.localdomain/index.html](http://localhost.localdomain/index.html)) without having localhost.localdomain in the ServerAlias directive. So, although it was serving the files, and processing the .shtml files correctly, it wasn't processing the .html files via XBitHack (or even when I had an .html outputFilter). Once I added the ServerAlias, it processed the executable-tagged .html files correctly.

---

