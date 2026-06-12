---
title: "Use mod_rewrite to completely remove query string."
date: 2008-11-04
forum: Server Platforms
---

### Post by chez17 on 2008-11-04
I have looked all over the internet and can't find any help on this subject. Everyone seems to want to rewrite the string for SEO purposes. I want search.php?search=true&value=awesome to be displayed as just search.php. But I want to try and make this site wide, for every page. Any help is most appreciated.

Dave

---

### Post by chez17 on 2008-11-04
I think I have made some progress but it isn't working yet. Here is what I've got:

RewriteEngine on

RewriteCond %{THE_REQUEST} ^GET\ /.*\;.*\ HTTP/
RewriteCond %{QUERY_STRING} !^$
RewriteRule .* http://mydomain.com%{REQUEST_URI}? [R=301,L]

Can somebody take a look and let me know if I'm missing something obvious?

---

