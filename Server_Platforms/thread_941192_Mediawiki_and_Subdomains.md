---
title: "Mediawiki and Subdomains"
date: 2008-10-07
forum: Server Platforms
---

### Post by tspec on 2008-10-07
I'm having an issue at the moment getting subdomains to work with mediawiki. Subdomains are configured correctly and mediawiki is working ok when using localhost or the IP address.

How I've got it set up:

root domain example.com sits here:
/var/www/example/

wiki dir with mediawiki installed sits here:
/var/www/example/wiki/

Sites-enabled Virtual Host:

<VirtualHost *>
        ServerName wiki.example.com
        DocumentRoot /var/www/example/wiki/

    <Directory /var/www/example/wiki/>
        Options Indexes FollowSymLinks MultiViews +Includes
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>

mediawiki works if you go to localhost/example/wiki/ and the subdomain works if i create a dir called test and point it there:
/var/www/example/test/ 

but pointing it to /wiki/ always redirects to wiki.example.com/example/wiki/index.php/Main_Page which spits back an error of course.

What I'm trying to get the subdomain and mediawiki to do is something like this:
wiki.example.com/index.php/Main_Page

But not sure how to do this or where it would be configured, I would assume it'd be configured somewhere in mediawiki but haven't located the spot to do it as yet.

Thanks.

---

### Post by tspec on 2008-10-08
Fixed. Thought I'd post a solution incase anyone else hits this problem.

sudo vim /var/www/example/wiki/LocalSettings.php

change
$wgScriptPath       = "/example/wiki";
to
$wgScriptPath       = "";
and save.

That will break being able to use the wiki as [http://ip/example/wiki/](http://ip/example/wiki/) or [http://localhost/example/wiki/](http://localhost/example/wiki/) but as long as I can use with subdomain, it's all good.

---

