---
title: "Force HTTP redirect to HTTPS LAMPP server"
date: 2014-10-10
forum: Server Platforms
---

### Post by scojopa on 2014-10-10
I have SSL installed and configured - If I go to the site I can manually [https://site.domain.com/page](https://site.domain.com/page) use SSL. But I cannot figure out how to redirect http to https - if I just enter site.domain.com/page it does not redirect. 

Can someone please provide some insight. 

Here is what I have set in my htaccess file- is there someone else that controls this?

RewriteEngine on


# Force SSL on entire Site
RewriteBase /
RewriteCond %{ENV:HTTPS} !on [NC]
RewriteRule ^/?page/(.*) https://%site.domain.com/page/$1 [R,L]


# Allow only GET and POST verbs
RewriteCond %{REQUEST_METHOD} !^(GET|POST)$ [NC,OR]

---

