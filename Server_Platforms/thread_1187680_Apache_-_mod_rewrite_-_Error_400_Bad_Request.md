---
title: "Apache - mod_rewrite - Error 400 Bad Request"
date: 2009-06-14
forum: Server Platforms
---

### Post by claustin on 2009-06-14
Hello,

I am developing a Facebook application that's pointed at my Apache webserver.

I have a CSS file that needs to load an image directly from my web server, the HTTP_REFERER is apps.facebook.com.

I have enabled mod_rewrite via a2enmod.  I have AllowOverride All in my virtual host config file.

In my .htaccess file I have the follow mod_rewrite rules :-

RewriteEngine On

RewriteCond %{HTTP_REFERER} !^$
RewriteCond %{HTTP_REFERER} !^http://(apps\.)?facebook.com/.*$ [NC]
RewriteRule \.(gif|jpe?g|png|bmp)$ - [F]

But no matter what, every request for the image from by server is getting :-

400 Bad Request
Cross Site Action detected!


What can I do?

Thanks for any info,
Chris

---

