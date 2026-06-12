---
title: "apache2 caching don't work on non image files"
date: 2014-08-24
forum: Server Platforms
---

### Post by fistuks on 2014-08-24
Hello,

I'm having problems with mods - expires/headers.

I have set the following in apache2.conf:

ExpiresActive on
ExpiresDefault "access plus 1 hour"
ExpiresByType application/javascript "access plus 1 months"
ExpiresByType image/jpg "access plus 1 month"
ExpiresByType image/jpeg "access plus 1 month"
ExpiresByType image/gif "access plus 1 month"
ExpiresByType image/png "access plus 1 month"
ExpiresByType text/css "access plus 1 months"

Yet all js/css files end up with 200 status and not 304 as images.

When inspecting the response header for the js/css files, it looks good and all expatriation settings are ok ( a month to the future ).

I there any special settings add in 14.04 for these type of files?

Help will be appreciated...

---

### Post by fistuks on 2014-08-24
Just found out i needed to create new conf file on /etc/apache/conf-available and sudo a2enconf on it....

I hope this understanding will help others :)

---

