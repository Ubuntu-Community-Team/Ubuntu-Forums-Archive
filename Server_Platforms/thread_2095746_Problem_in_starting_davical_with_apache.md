---
title: "Problem in starting davical with apache"
date: 2012-12-17
forum: Server Platforms
---

### Post by eng_asa on 2012-12-17
Hello,

I am trying to install Davical on an existing mail server, but have troubled to get it into live.

Here is my configuration:
# Virtual Host def for Debian packaged DAViCal
<VirtualHost *:80>
DocumentRoot /usr/share/davical/htdocs
DirectoryIndex index.php index.html
ServerName davical.example.net
ServerAlias calendar.example.net
Alias /images/ /usr/share/davical/htdocs/images/
<Directory /usr/share/davical/htdocs/>
AllowOverride None
Order allow,deny
Allow from all
</Directory>
php_value include_path /usr/share/awl/inc
php_value magic_quotes_gpc 0
php_value magic_quotes_runtime 0
php_value register_globals 0
php_value error_reporting "E_ALL & ~E_NOTICE"
php_value default_charset "utf-8"

</VirtualHost>


mail:/etc/apache2# cat ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
# If you add NameVirtualHost *:443 here, you will also have to change
# the VirtualHost statement in /etc/apache2/sites-available/default-ssl
# to <VirtualHost *:443>
# Server Name Indication for SSL named virtual hosts is currently not
# supported by MSIE on Windows XP.
Listen 443
</IfModule>

<IfModule mod_gnutls.c>
Listen 443
</IfModule>


some how when I try to open it by the browser http://<server-IP>/cal ---> it turns to ---> https://<server-name>/cal
How can I override this? I just need to complete the davical installation and don't really care about using ssl!

Thanks.

---

