---
title: "Apache - access via IP - which Virtual Host?"
date: 2006-02-24
forum: Server Platforms
---

### Post by jimwillsher on 2006-02-24
Hi all,

This relates loosely to a previous thread, but it's a new subject for me so...new thread.

Breezy, with Apache and Virtual hosts configured.

All my virtual hosts stuff is working fine, with one exception. If I enter the IP address of my server into a browser I get the SECOND website displayed. What I really want displayed is a specific virtual host (or more precisely, I want a folder called "Default" to become the DocRoot).

My 000-default file (in sites-enabled) contains

```
NameVirtualHost *:80
RewriteEngine on
RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
RewriteRule .* - [F]

```

and my other files contain normal stuff like:

```



<VirtualHost *:80>
  ServerName www.bulkrenameutility.co.uk
  DocumentRoot /var/www/bulkrenameutility.co.uk
  ErrorLog /var/log/apache2/bulkrenameutility.co.uk/error_log
  CustomLog /var/log/apache2/bulkrenameutility.co.uk/access_log combined
  ErrorDocument 401 /Error401.html
  ErrorDocument 404 /Error404.html
  RewriteEngine on
  RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
  RewriteRule .* - [F]
</VirtualHost>

```

How can I configure Apache2 so that access via direct IP address goes to a specific site? I would have thought it would go to the 000-default site, as that's the first visrtual-host alphabetically, but it goes to the second one ( a site called 41Club......)

I'm pretty sure my individual Virtual Hosts files are correct, as all the sites work fine when accessed by domain name. But I want access by IP address to go to a specific site.

Many thanks,


Jim

---

### Post by suRoot on 2006-02-24
Just create another virtual host with the ServerName attribute set to be the IP of the server.  Point it at the appropriate document root / etc.  Restart apache.

---

### Post by jimwillsher on 2006-02-24
Doh! Can't believe I didn't try that.....many thanks!

---

### Post by MJN on 2006-02-25
Whilst I'm sure that will lead to the effect you're after there will be drawbacks if you're on a dynamic IP (are you?).. :)

You mentioned the 'contents' of 000-default - just to clarify you do mean the contents of the file in sites-available/ symlink'd by 000-default right?

Your assumption that a 'nameless' HTTP request would 'go to' 000-default is *almost* correct - specifically it looks for the first <virtualhost> container which would ordinarily be included in the file that 000-default symlinks to. However, your post suggests that perhaps your first <virtualhost> container is actually in your bulkrenameutility config file - this is not really how it's meant to work.

Put the <virtualhost> container for your default site (which is usually also your  '*nameless*' site) into the file symlink'd by 000-default then (I think!) you should be fine.

Mathew

---

