---
title: "mod rewrite inconsistency"
date: 2011-11-01
forum: Server Platforms
---

### Post by Geoff_L on 2011-11-01
I'm using Ubuntu 10.10 under VirtualBox for web development. An existing project uses the following .htaccess to rewrite "/" and "*.html" to master.php with the appropriate page passed on the querystring:
```

RewriteEngine On

RewriteRule ^/$ master.php?url=index.html [L]
RewriteRule ^(.+\.html)$ master.php?url=$1 [QSA,L]

```On the existing project, this works as I'd expect. So when I needed a new instance for a new project, I built another virtual Ubuntu 10.10 machine, installed LAMP, enabled mod_rewrite then copied the .htaccess file to the new server. On this VM, "*.html" is correctly passed to master.php with the requested page on the querystring, but "/" is not and instead a directory listing is returned. IOW, on the new machine, the second rewrite rule works but not the first.

I've checked httpd.conf and sites-enabled/000-default and they appear to be identical in both VMs, so I'm at a loss as to what the problem is.

Can anyone help?

TIA,

Geoff

---

