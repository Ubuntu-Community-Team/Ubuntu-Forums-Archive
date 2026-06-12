---
title: "Apache change file extension"
date: 2007-07-11
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-11
Hi all,

I am stuck and rather confused with mod-rewrite.c

what I want to achieve is that some one requests sitemap.xml (which doesn't exist) and they get servered back sitemap.php.

As I understand it this can be done with mod rewrite.

I have a .htaccess file in /var/www/ :

[php]<IfModule mod_rewrite.c>
Options +Followsymlinks
RewriteEngine on
RewriteRule ^/sitemap.xml$ /sitemap.php
</IfModule>[/php]

in /etc/apache2/sites-available/default

I have changed <Direcotry /var/www>
where it was AllowOverride None
it is now AllowOverride All

I don't get why this doesn't work to be honest.

in the apache2/error.log file I get File does not exist: sitemap.xml 

I am assuming I have the right module downloaded and installed but to be completely honest I am not sure which / what that is to double check.

any and all advice MORE than welcome.

Thank you all for your help

Twiggy

---

### Post by twistedtwig on 2007-07-12
the answer to my question was as follows:

I didn't have module rewrite enabled, which I found out by trying to enable it:

[php]a2enmod rewrite[/php]

The follow code takes my sitemapxml.php and masks it to sitemap.xml

[php]
<IfModule modrewrite.c>
Options +FollowSymlinks
RewriteEngine on
RewriteRule ^sitemap.xml$ sitemapxml.php [L]
[/php]

I also had to add a header to the php file to make it appear as a correct XML file.

---

