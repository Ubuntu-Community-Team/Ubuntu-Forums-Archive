---
title: "How do I create a short URL using mod_rewrite in Apache"
date: 2017-11-18
forum: Server Platforms
---

### Post by jaytel on 2017-11-18
Hi everyone, I feel really stupid having to ask this but I am having more trouble than I should be.  I have installed MediaWiki onto my server, which I intend to use to provide manual pages for my Minecraft world that I am creating.  So the install went okay but when I visit the wiki at [https://lumaria.online/wiki](https://lumaria.online/wiki) I get redirected this appearing in my address bar [https://lumaria.online/wiki/index.php?title=Main_Page](https://lumaria.online/wiki/index.php?title=Main_Page)

After searching through the MediaWiki help and installation pages, I noticed that I have to manually setup short URLs using Apache if I want the addresses of my wiki pages to appear like [https://lumaria.online/w/wiki/Article_Title](https://lumaria.online/w/wiki/Article_Title)

Thats not a problem.  I don't mind doing that and the help pages even assisted me in writing the code that I need.  So now I have this code 

```

[SIZE=2][COLOR=#000000][FONT=&amp]RewriteEngine On
[/FONT][/COLOR][/SIZE][FONT=&amp][SIZE=2]
[COLOR=#000000]RewriteRule ^/?w(/.*)?$ %{DOCUMENT_ROOT}/wiki/index.php [L][/COLOR]
[COLOR=#000000]RewriteRule ^/?$ %{DOCUMENT_ROOT}/wiki/index.php [L][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} !-f[/COLOR]
[COLOR=#000000]RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} !-d[/COLOR]
[COLOR=#000000]RewriteRule ^/?wiki/images/thumb/[0-9a-f]/[0-9a-f][0-9a-f]/([^/]+)/([0-9]+)px-.*$ %{DOCUMENT_ROOT}/wiki/thumb.php?f=$1&width=$2 [L,QSA,B][/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} !-f[/COLOR]
[COLOR=#000000]RewriteCond %{DOCUMENT_ROOT}%{REQUEST_URI} !-d[/COLOR]
[COLOR=#000000]RewriteRule ^/?wiki/images/thumb/archive/[0-9a-f]/[0-9a-f][0-9a-f]/([^/]+)/([0-9]+)px-.*$ %{DOCUMENT_ROOT}/wiki/thumb.php?f=$1&width=$2&archived=1 [L,QSA,B][/COLOR][/SIZE]
[/FONT]
```

and the instructions tells me that this configuration is meant to go the "same block as whatever VirtualHost or other directive you have your wiki's DocumentRoot, ServerName, etc... already defined in" but I don't actually understand what it means by "same block or directive".  

Where am I mean to put this?  Also, what configuration file am I meant to put this into, the instructions for writing the this was really good but the instructions about where it goes are extremely bad.

I am running Ubuntu 16.04.3 LTS on a cloud server with Plesk Onyx control panel, just in case that matters to where the configuration goes.  I also have full root access to the server as well though, so I can edit all aspects of it and create any files that I need to.

---

