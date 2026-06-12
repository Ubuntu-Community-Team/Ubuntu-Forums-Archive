---
title: "redirecting directory in apache2 to https"
date: 2011-05-11
forum: Server Platforms
---

### Post by tiercel on 2011-05-11
This seems to be a common question but I am having the devil's own time getting it working.

I want to have a subdirectory of DocumentRoot being served by apache2 to force-redirect to https.  The directory accesses OK when I manually type [https://www.myserver.com/subdirectory](https://www.myserver.com/subdirectory), but I want to force any [http://www.myserver.com/subdirectory](http://www.myserver.com/subdirectory) requests to redirect to https instead.

I am putting commands inside of Directory directive inside a config file; putting SSLRequireSSL in httpd.conf just kicks me to 403 Forbidden error.  I have tried blocks of code (with mod_rewrite enabled) like:

RewriteEngine On

RewriteCond %{SERVER_PORT} !443$
  #or
#RewriteCond %{SERVER_PORT} ^80$
  #or 
#RewriteCond %{HTTPS} off

RewriteRule ^/securesubdir(.*) https://%{HTTP_HOST}%{REQUEST_URI}

and I've tried this inside of httpd.conf, inside of sites_enabled/000-default-ssl, even inside of sites_enabled/000-default

What other commands should I try (and in which of the myriad config files should they go)?

---

### Post by SeijiSensei on 2011-05-12
Use a Redirect rather than a Rewrite rule:

```

<VirtualHost *:80> 
ServerName    www.example.com
Redirect      /     https://www.example.com/ 
<VirtualHost>

<VirtualHost *:443>
ServerName    www.example.com
[stuff]
</VirtualHost>

```

---

### Post by tiercel on 2011-05-12
**Thank** you.  I'm not sure why every search I tried yielded folks giving examples of using Rewrite rather than Redirect.

While I'm looking to redirect just a subdirectory, rather than everything, once I was put onto the track of Redirect I found that's do-able too:

```

<VirtualHost *:80> 
ServerName    www.example.com
Redirect      permanent     /subdir     https://www.example.com/subdir 
<VirtualHost>

<VirtualHost *:443>
ServerName    www.example.com
[stuff]
</VirtualHost>

```

where the subdirectory argument with the Redirect had to be ```
/subdir
``` not ```
subdir
``` or ```
subdir/
```.  

(I included the "permanent" option since it sends a different status code, 301; apparent the default is "temporary" code 302 -- I'm not sure in what contexts that is important but this redirection is designed to be permanent in nature so I figured it's better to be precise.)

Thanks again!

---

### Post by Lars Noodén on 2011-05-13
> **tiercel said:**
> **Thank** you.  I'm not sure why every search I tried yielded folks giving examples of using Rewrite rather than Redirect.

[redirect](http://httpd.apache.org/docs/2.2/mod/mod_alias.html#redirect) is simpler to use and generates fewer posts in forums and blogs that rewrite does.

---

