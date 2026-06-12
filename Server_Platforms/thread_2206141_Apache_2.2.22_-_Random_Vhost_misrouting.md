---
title: "Apache 2.2.22 - Random Vhost misrouting"
date: 2014-02-17
forum: Server Platforms
---

### Post by Juan_Manuel on 2014-02-17
[COLOR=#000000][FONT=Arial]I have a Apache 2.2.22 + PHP 5.4.9 running on a Ubuntu 12.04[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm hosting three sites here. For that, i have 2 virtual host pointing to three differents folders.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]For example, this is one Vhost for *domain1*[/FONT][/COLOR]
```
<VirtualHost *:80>
        ServerName domain1.com
        ServerAlias [www.domain1.com]("http://www.domain1.com")
        ServerAdmin [EMAIL="support@server.com"]support@server.com[/EMAIL]
    DocumentRoot /mnt/htdocs/domain1.com/public
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /mnt/htdocs/domain1.com/public>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/domain1.com-error.log
    CustomLog ${APACHE_LOG_DIR}/domain1.com-access.log combined
</VirtualHost>
```
[COLOR=#000000][FONT=Arial]The this here is that the 1% of the hits goes to incorrect folder. the other 99% goes to the correct folder and resolve the correct domain/code.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Example of the error in domain1.com's error log[/FONT][/COLOR]
```
[Fri Feb 14 15:21:45 2014] [error] [client 10.183.250.134] PHP Fatal error:  Class 'Sitemap\\SitemapServiceProvider' not found in /mnt/htdocs/domain1.com/vendor/laravel/framework/src/Illuminate/Foundation/ProviderRepository.php on line 123, referer: [http://www.site2.com/someurl](http://www.site2.com/someurl)

```[COLOR=#000000][FONT=Arial]This service provider doesn't exists because domain2.com is routed to domain1.com's folder.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This error is COMPLETELY RANDOM. If I reload the error page, the site render ok.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I checked all the lines of vhosts, erasing all the non critical to keep it simple but the error continues.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Any thought?[/FONT][/COLOR]

---

### Post by volkswagner on 2014-02-17
> **Juan_Manuel said:**
> [COLOR=#000000][FONT=Arial]I have a Apache 2.2.22 + PHP 5.4.9 running on a Ubuntu 12.04[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I'm hosting three sites here. For that, i have 2 virtual host pointing to three differents folders.[/FONT][/COLOR]


Perhaps you can explain why you only have 2 vhost files for three domains (sites).

It may help to post the remaining vHost files.

---

