---
title: "Apache url rewrite endless loop"
date: 2009-03-19
forum: Server Platforms
---

### Post by botfish on 2009-03-19
Hi,

I'm trying to create search engine frendly URLs bu using Apache's mod_rewrite.

RewriteEngine on
RewriteCond %{REQUEST_URI} !^/index [nc,or]
RewriteCond %{REQUEST_URI} !^/fourms [nc,or]
RewriteCond %{REQUEST_URI} !^/wiki [nc,or]
RewriteCond %{REQUEST_URI} !\.(gif|jpg|css|js|php|pdf|xml|txt)$ [nc]
RewriteRule ^(.*)$ /index.php/%1

The above produced an endless loop because it keeps rewrites the URL.

I have tried to prevent this with the second line "RewriteCond %{REQUEST_URI} !^/index [nc,or]" but it dose not work.

From my error.log:
Request exceeded the limit of 10 internal redirects due to probable configuration error.

Any help much appreciated.

---

