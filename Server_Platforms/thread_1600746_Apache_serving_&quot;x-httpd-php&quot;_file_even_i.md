---
title: "Apache serving &quot;x-httpd-php&quot; file even in non-existent directory"
date: 2010-10-19
forum: Server Platforms
---

### Post by PhoenixIgnis on 2010-10-19
I awoke this morning and updated my ubuntu server installation from webmin to apache 2 and it pretty much broke my php site.

 I did a reinstall of PHP5.  sudo apt-get install php5   This repaired my installation mostly, however a problem persists.   I have a phpbb3 forum installed under the directory 'forum' and apache continuously tries to let me download a file in firefox &quot;x-httpd-php&quot; with some random name followed by .part.  

Example "Pzya1fv6.part".

Even if I change the forum to another directory, apache still tries serving the file from the old one. 

(The problem is only hidden with a directory change, the new forum directory does not serve this file).  

Basically I would like to understand why Apache is doing this.   Also certain directory alias' like /phpmyadmin/ to &quot;/usr/share/phpmyadmin/&quot; no longer work (this is on port 443, SSL enabled).

---

