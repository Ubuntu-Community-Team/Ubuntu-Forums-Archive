---
title: "Apache RewriteRule while keeping url"
date: 2011-08-30
forum: Server Platforms
---

### Post by josh6847 on 2011-08-30
I would like to redirect example.com to [IP-Address]:Port. But, whenever I redirect, I would like to keep example.com as the base URL. Is this possible? Here's what I have tried (with diff combinations of [R=Num]):

<VirtualHost *:80>
        ServerName example.com
        ServerAlias [www.example.com](www.example.com)
        RewriteEngine On
        RewriteCond %{HTTP_HOST} ^(www\.)?example\.com
        RewriteRule (.*) http://72.198.123.230:40/$1 [R=301,L]
</VirtualHost>

I am trying to do some navigating as the ISP has blocked port 80.

---

