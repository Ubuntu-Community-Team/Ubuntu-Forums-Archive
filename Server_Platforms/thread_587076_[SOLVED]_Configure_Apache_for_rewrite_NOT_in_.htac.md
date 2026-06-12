---
title: "[SOLVED] Configure Apache for rewrite NOT in .htaccess"
date: 2007-10-22
forum: Server Platforms
---

### Post by twistedtwig on 2007-10-22
Hi all,

I am having a real issue with rewriterule... I have enabled mod rewrite. rewrite.load is in apache2/mods-enabled

PHPINFO() [http://www.houseofhawkins.com/info.php](http://www.houseofhawkins.com/info.php) shows that the mod is enabled.

I am trying to get a rewriterule to work that is not in a .htaccess file.  After some fiddling I am completely lost now.

I have changed my vhosts.conf file to be the most basic I can get it (i.e. no extra sub domains etc).

I had this rule working fine in the .htaccess file which was in the root folder:

<IfModule mod_rewrite.c>
Options +FollowSymlinks
RewriteEngine on
RewriteRule ^sitemap.xml$ sitemapxml.php [L]
</IfModule>

<IfModule mod_rewrite.c>
Options +FollowSymlinks
RewriteEngine on
RewriteRule ^sitemap.html$ sitemaphtml.php [L]
</IfModule>

I have removed the .htaccess file.  Where and how should I put these rules to have them working in the config file(s) please?

The reason I am trying to move them from the .htaccess file is for:

1) more central control

2) I want to put other rules in but don't like lots of htaccess files.

Thanks for the help.

---

### Post by MJN on 2007-10-22
Put the rules in the appropriate virtual host container.

e.g.
```
<Virtualhost *:80>
     ServerName ...
     .
     .
     RewriteEngine On
     RewriteRule ...
     .
     .
</Virtualhost>
```Mathew

---

### Post by twistedtwig on 2007-10-23
/sulk... I tried the following virtual host but no joy:

```

################### default root directory #################

<VirtualHost *>
ServerName houseofhawkins.com
ServerAlias www.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root

RewriteEngine on
RewriteRule ^sitemap.xml$ sitemapxml.php [L]

</VirtualHost>


```

don't really know where I am going wrong :(

---

### Post by MJN on 2007-10-23
You likely just need a leading slash (e.g. **RewriteRule ^/sitemap.xml$ /sitemapxml.php [L]**) as now that you're in the Apache config (not .htaccess), and hence matching URIs from the perspective of the whole server (not a particular directory), then this is how the URI will appear.

Mathew

---

### Post by twistedtwig on 2007-10-23
sorry I just looked at my reply and realized how poop it was!!!

I tried the slash but it didn't do anything:

[http://houseofhawkins.com/sitemap.xml](http://houseofhawkins.com/sitemap.xml)

it does not find the page, error 300 mulitple choices.

I have had a look at /var/log/apache2/error.log and access.log and I can not see any references to trying to find it.

---

### Post by MJN on 2007-10-23
It wasn't poop - the omission of the leading slash is a very common (and forgiveable) mistake to make when moving redirects from .htaccess to the server config.

The redirect seems to be working fine from here - /sitemap.xml and /sitemapxml.php both result in the same page (and presumably the former file doesn't actually exist?).

Try restarting your browser - it's probably using cached info (and hence not aware the page has effectively changed).

Mathew

---

### Post by twistedtwig on 2007-10-23
bloody firefox!!!!!!

<--- NOOB!!! lol

thank you so much :)

---

### Post by MJN on 2007-10-23
A bad workm... ;)

---

### Post by twistedtwig on 2007-10-24
Rofl!!!

---

