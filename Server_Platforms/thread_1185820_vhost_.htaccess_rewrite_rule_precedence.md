---
title: "vhost .htaccess rewrite rule precedence"
date: 2009-06-12
forum: Server Platforms
---

### Post by hmsims on 2009-06-12
I have a server up with two ssl enabled sites
I've declared each vhost in my default-ssl file as follows:

NameVirtualHost xxx.xxx.xxx.xxx:80
NameVirtualHost xxx.xxx.xxx.xxx:443

<VirtualHost xxx.xxx.xxx.xxx:80>
        ServerName [www.firstwebsite.com]("http://www.firstwebsite.com")
        ServerAdmin [EMAIL="webmaster@firstwebsite.com"]webmaster@firstwebsite.com[/EMAIL]
        DocumentRoot /var/www/fws
        <Directory /var/www/fws>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                <IfModule mod_rewrite.c>
                        RewriteEngine on
                        RewriteBase /
                        RewriteOptions Inherit
                </IfModule>
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
</VirtualHost>
<VirtualHost xxx.xxx.xxx.xxx:443>
        ServerName [www.firstwebsite.com]("http://www.firstwebsite.com")
        ServerAdmin [EMAIL="webmaster@firstwebsite.com"]webmaster@firstwebsite.com[/EMAIL]
        DocumentRoot /var/www/fws
        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        SSLCertificateFile /etc/ssl/certs/www_firstwebsite_com.crt
        SSLCertificateKeyFile /etc/ssl/private/www_firstwebsite_com.key
        SSLCertificateChainFile /etc/ssl/certs/DigiCertCA.crt
        <Directory /var/www/fws>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                <IfModule mod_rewrite.c>
                        RewriteEngine on
                        RewriteBase /
                        RewriteOptions Inherit
                </IfModule>
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
</VirtualHost>

<VirtualHost xxx.xxx.xxx.xxx:80>
        ServerName [www.secondwebsite.com]("http://www.secondwebsite.com")
        ServerAdmin [EMAIL="webmaster@secondwebsite.com"]webmaster@secondwebsite.com[/EMAIL]
        DocumentRoot /var/www/sws
        <Directory /var/www/sws>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                <IfModule mod_rewrite.c>
                        RewriteEngine on
                        RewriteBase /
                        RewriteOptions Inherit
                </IfModule>
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
</VirtualHost>
<VirtualHost xxx.xxx.xxx.xxx:443>
        ServerName [www.secondwebsite.com]("http://www.secondwebsite.com")
        ServerAdmin [EMAIL="webmaster@secondwebsite.com"]webmaster@secondwebsite.com[/EMAIL]
        DocumentRoot /var/www/sws
        <Directory /var/www/sws>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                <IfModule mod_rewrite.c>
                        RewriteEngine on
                        RewriteBase /
                        RewriteOptions Inherit
                </IfModule>
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        SSLCertificateFile /etc/ssl/certs/www_secondwebsite_com.crt
        SSLCertificateKeyFile /etc/ssl/private/www_secondwebsite_com.key
        SSLCertificateChainFile /etc/ssl/certs/DigiCertCA.crt
</VirtualHost>

Now the rewrite is in the mods-enabled folder and it is enabled in the apache2.conf

This is the /etc/hosts file:

127.0.0.1                server
127.0.0.1                localhost localhost.localdomain
xxx.xxx.xxx.xxx.     firstwebsite.com [www.firstwebsite.com]("http://www.firstwebsite.com")
xxx.xxx.xxx.xxx.     secondwebsite.com [www.secondwebsite.com]("http://www.secondwebsite.com")


Now here is the odd part....in the .htaccess file for the firstwebsite the rewrite rules take precedence over the .htaccess in the secondwebsite's folder

To get the rewrite rules for the secondwebsite to take place I had to add them to the .htaccess for the first vhost listed in the default-ssl file.

Why won't the rewrite rules change depending on which site is accessed, using the local .htaccess file?

---

