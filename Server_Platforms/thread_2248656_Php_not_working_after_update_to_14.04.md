---
title: "Php not working after update to 14.04"
date: 2014-10-16
forum: Server Platforms
---

### Post by faroutliving on 2014-10-16
On my server, I've been holding off on upgrading to 14.04 but today a new video card forced my hand. So I upgraded to 14.04 from 12.04, and since then my php pages just spit out the source. I've been searching for a solution for 8+ hours and I'm hoping this is not so complicated as it appears. Nothing appears in any log file that I can find, and I've tried a simple web page called test.php which is nothing more than:

[PHP]
<?php phpinfo(); ?>
[/PHP]


Is there some way to make apache2 output useful debug info? Maybe that is where I should focus my question.


The amount of configuration files involved seems enormous, but I'll take a swing at providing the relevant bits in hopes that someone can lead my down a more promising trail.

/etc/apache2/mods-available/php5.conf:
```

<FilesMatch ".+\.ph(p[345]?|t|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>
<FilesMatch ".+\.phps$">
    SetHandler application/x-httpd-php-source
    # Deny access to raw php sources by default
    # To re-enable it's recommended to enable access to the files
    # only in specific virtual host or directory
    Order Deny,Allow
    Deny from all
</FilesMatch>
# Deny access to files without filename (e.g. '.php')
<FilesMatch "^\.ph(p[345]?|t|tml|ps)$">
    Order Deny,Allow
    Deny from all
</FilesMatch>

# Running PHP scripts in user directories is disabled by default
# 
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
#<IfModule mod_userdir.c>
#    <Directory /home/*/public_html>
#        php_admin_flag engine Off
#    </Directory>
#</IfModule>

```

/etc/apache2/sites-available/domain.tld.conf (generated from virtualmin, which I am sure is not helping the situation)
```

<VirtualHost 88.99.111.77:80>
SuexecUserGroup "#1026" "#1007"
ServerName domain.tld
ServerAlias www.domain.tld
ServerAlias webmail.domain.tld
ServerAlias admin.domain.tld
DocumentRoot /home/domain.tld/public_html
ErrorLog /var/log/virtualmin/domain.tld_error_log
CustomLog /var/log/virtualmin/domain.tld_access_log combined
ScriptAlias /cgi-bin/ /home/domain.tld/cgi-bin/
ScriptAlias /awstats/ /home/domain.tld/cgi-bin/
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/domain.tld/public_html>
Options -Indexes +IncludesNOEXEC +SymLinksifOwnerMatch +ExecCGI
Require all granted
AllowOverride All Options=ExecCGI,Includes,IncludesNOEXEC,Indexes,MultiViews,SymLinksIfOwnerMatch
AddHandler fcgid-script .php
AddHandler fcgid-script .php5
FcgidWrapper /home/domain.tld/fcgi-bin/php5.fcgi .php
FcgidWrapper /home/domain.tld/fcgi-bin/php5.fcgi .php5
</Directory>
<Directory /home/domain.tld/cgi-bin>
Require all granted
AllowOverride All Options=ExecCGI,Includes,IncludesNOEXEC,Indexes,MultiViews,SymLinksIfOwnerMatch
</Directory>
RewriteEngine on
RewriteCond %{HTTP_HOST} =webmail.domain.tld
RewriteRule ^(.*) https://domain.tld:20000/ [R]
RewriteCond %{HTTP_HOST} =admin.domain.tld
RewriteRule ^(.*) https://domain.tld:10000/ [R]
IPCCommTimeout 9999
<Files awstats.pl>
AuthName "domain.tld statistics"
AuthType Basic
AuthUserFile /home/domain.tld/.awstats-htpasswd
require valid-user
</Files>
php_admin_value engine Off
FcgidMaxRequestLen 1073741824
</VirtualHost>
<VirtualHost 88.99.111.77:443>
SuexecUserGroup "#1026" "#1007"
ServerName domain.tld
ServerAlias www.domain.tld
ServerAlias webmail.domain.tld
ServerAlias admin.domain.tld
DocumentRoot /home/domain.tld/public_html
ErrorLog /var/log/virtualmin/domain.tld_error_log
CustomLog /var/log/virtualmin/domain.tld_access_log combined
ScriptAlias /cgi-bin/ /home/domain.tld/cgi-bin/
ScriptAlias /awstats/ /home/domain.tld/cgi-bin/
DirectoryIndex index.html index.htm index.php index.php4 index.php5
<Directory /home/domain.tld/public_html>
Options -Indexes +IncludesNOEXEC +SymLinksifOwnerMatch +ExecCGI
Require all granted
AllowOverride All Options=ExecCGI,Includes,IncludesNOEXEC,Indexes,MultiViews,SymLinksIfOwnerMatch
AddHandler fcgid-script .php
AddHandler fcgid-script .php5
FcgidWrapper /home/domain.tld/fcgi-bin/php5.fcgi .php
FcgidWrapper /home/domain.tld/fcgi-bin/php5.fcgi .php5
</Directory>
<Directory /home/domain.tld/cgi-bin>
Require all granted
AllowOverride All Options=ExecCGI,Includes,IncludesNOEXEC,Indexes,MultiViews,SymLinksIfOwnerMatch
</Directory>
RewriteEngine on
RewriteCond %{HTTP_HOST} =webmail.domain.tld
RewriteRule ^(.*) https://domain.tld:20000/ [R]
RewriteCond %{HTTP_HOST} =admin.domain.tld
RewriteRule ^(.*) https://domain.tld:10000/ [R]
RemoveHandler .php
RemoveHandler .php5
IPCCommTimeout 9999
SSLEngine on
SSLCertificateFile /home/domain.tld/ssl.cert
SSLCertificateKeyFile /home/domain.tld/ssl.key
<Files awstats.pl>
AuthName "domain.tld statistics"
AuthType Basic
AuthUserFile /home/domain.tld/.awstats-htpasswd
require valid-user
</Files>
SSLCACertificateFile /home/domain.tld/ssl.ca
php_admin_value engine Off
FcgidMaxRequestLen 1073741824
</VirtualHost>

```

---

### Post by SeijiSensei on 2014-10-16
What is the purpose of these?
```

AddHandler fcgid-script .php
AddHandler fcgid-script .php5
FcgidWrapper /home/domain.tld/fcgi-bin/php5.fcgi .php
FcgidWrapper /home/domain.tld/fcgi-bin/php5.fcgi .php5

```

Usually PHP is invoked by this entry at the top of /etc/apache2/mods-available/php5.conf like in your example above:
```

<FilesMatch ".+\.ph(p[345]?|t|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>

```

Beyond that I can't help much.  There's a lot of unusual stuff in your configuration compared to a vanilla Apache/PHP system.

---

### Post by faroutliving on 2014-10-16
I'm not sure what the purpose is either, the entire file was created (and since managed) by virtualmin. I've removed most every item relating to .php from the sites-available AND IT STARTED WORKING AGAIN.

So I'll try and figure out exactly which item did what (and learn a little more in the process) and move on. Thanks so much for the help!

---

