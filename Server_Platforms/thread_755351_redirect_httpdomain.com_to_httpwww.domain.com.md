---
title: "redirect http://domain.com to http://www.domain.com ?"
date: 2008-04-14
forum: Server Platforms
---

### Post by android6011 on 2008-04-14
I want to prevent domain.com and [www.domain.com](www.domain.com) from creating two different sessions so i just want domain.com to redirect to [www.domain.com](www.domain.com) . how do i configure apache to do this?

---

### Post by cdenley on 2008-04-15
I think something like this would work.
```

RewriteEngine On
RewriteCond %{HTTP_HOST}  ^mydomain.com
RewriteRule (.*) http://www.mydomain.com%{REQUEST_URI}

```

---

### Post by hyper_ch on 2008-04-15
and of course:

```

sudo a2enmod rewrite

```

---

### Post by FakeOutdoorsman on 2008-04-15
Here's another version.  Try it first without "Options +FollowSymLinks".  You may not need it depending on your server configuration.  The NC ignores upper and lowercase differences and the R=301 tells the browser that this is a permanent redirect.  You can place this in an .htaccess file in the root of your site directory or in the virtual hosting files: /etc/apache2/sites-available/yoursitefile.
```
Options +FollowSymLinks
RewriteEngine on
RewriteCond %{HTTP_HOST} ^example\.com [NC]
RewriteRule (.*) http://www.example.com/$1 [R=301,L]
```

In "yoursitefile" you may also need to add:
```
ServerAlias www.domain.com
```

Personally, I prefer dumping the www prefix:
```
RewriteEngine on
RewriteCond %{http_host} ^www\.domain\.com [NC]
RewriteRule ^(.*)$ http://domain.com/$1 [R=301,NC]
```

---

