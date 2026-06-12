---
title: "&quot;Apache2 + openssl&quot; Help please..."
date: 2010-12-26
forum: Server Platforms
---

### Post by charith123 on 2010-12-26
I have running apache2 and I want to enable ssl in my server for that I compile openssl without errors:lol: But when i start Apache it give following error,,,,,,,:confused:  

```
  
root@charith-desktop:/usr/local/apache2/bin# ./apachectl start
Syntax error on line 441 of /usr/local/apache2/conf/httpd.conf:
Invalid command 'SSLEngine', perhaps misspelled or defined by a module not included in the server configuration

```When I uncomment  "LoadModule ssl_module modules/mod_ssl.so" line in httpd.conf I get following error....

```

root@charith-desktop:/usr/local/apache2/bin# ./apachectl start
httpd: Syntax error on line 18 of /usr/local/apache2/conf/httpd.conf: Cannot load /usr/local/apache2/modules/mod_ssl.so into server: /usr/local/apache2/modules/mod_ssl.so: invalid ELF header

```This is my httpd.conf
```


ServerRoot "/usr/local/apache2"



  Listen 80
  Listen 443


# Example:
# LoadModule foo_module modules/mod_foo.so


    LoadModule php5_module        modules/libphp5.so

    LoadModule ssl_module modules/mod_ssl.so


<IfModule !mpm_netware_module>
<IfModule !mpm_winnt_module>


User daemon
Group daemon




</IfModule>
</IfModule>



ServerAdmin you@example.com



 DocumentRoot "/usr/local/apache2/htdocs"


<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>




<Directory "/usr/local/apache2/htdocs">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.2/mod/core.html#options
    # for more information.
    #
    Options Indexes FollowSymLinks

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   Options FileInfo AuthConfig Limit
    #
    AllowOverride None

    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>



<IfModule dir_module>
    DirectoryIndex index.htm index.html index.php index.php3 default.html index.cgi
</IfModule>



<FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy All
</FilesMatch>



ErrorLog "logs/error_log"


LogLevel warn

<IfModule log_config_module>
    
    LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %b" common

    <IfModule logio_module>
      # You need to enable mod_logio.c to use %I and %O
      LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
    </IfModule>

    
    CustomLog "logs/access_log" common

    
</IfModule>

<IfModule alias_module>
    
    ScriptAlias /cgi-bin/ "/usr/local/apache2/cgi-bin/"

</IfModule>

<IfModule cgid_module>
    
</IfModule>



<Directory "/usr/local/apache2/cgi-bin">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>


DefaultType text/plain

<IfModule mime_module>
   
    TypesConfig conf/mime.types

    
    #AddType application/x-gzip .tgz
     AddType application/x-httpd-php .php

AddType application/x-x509-ca-cert .crt
AddType application/x-pkcs7-crl .crl


    
    #AddEncoding x-compress .Z
    #AddEncoding x-gzip .gz .tgz
 
    AddType application/x-compress .Z
    AddType application/x-gzip .gz .tgz

    
    #AddHandler cgi-script .cgi

    # For type maps (negotiated resources):
    #AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    #AddType text/html .shtml
    #AddOutputFilter INCLUDES .shtml
</IfModule>


#MIMEMagicFile conf/magic

#
# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
#ErrorDocument 404 "/cgi-bin/missing_handler.pl"
#ErrorDocument 402 http://www.example.com/subscription_info.html
#


#EnableMMAP off
#EnableSendfile off

# Supplemental configuration


# Server-pool management (MPM specific)
#Include conf/extra/httpd-mpm.conf

# Multi-language error messages
#Include conf/extra/httpd-multilang-errordoc.conf

# Fancy directory listings
#Include conf/extra/httpd-autoindex.conf

# Language settings
#Include conf/extra/httpd-languages.conf

# User home directories
#Include conf/extra/httpd-userdir.conf

# Real-time info on requests and configuration
#Include conf/extra/httpd-info.conf

# Virtual hosts
#Include conf/extra/httpd-vhosts.conf

# Local access to the Apache HTTP Server Manual
#Include conf/extra/httpd-manual.conf

# Distributed authoring and versioning (WebDAV)
#Include conf/extra/httpd-dav.conf

# Various default settings
#Include conf/extra/httpd-default.conf

# Secure (SSL/TLS) connections
 
# Include conf/extra/httpd-ssl.conf
#
# Note: The following must must be present to support
#       starting without SSL on platforms with no /dev/random equivalent
#       but a statically compiled-in mod_ssl.
#
<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>


NameVirtualHost 127.0.0.1:80
NameVirtualHost 127.0.0.1:443




<VirtualHost 127.0.0.1:80>

ServerAdmin charith079@gmail.com
DocumentRoot "/usr/local/apache2/htdocs"
ServerName ...........
ServerAlias............
ErrorLog /usr/local/apache2/logs/server2log

</VirtualHost>

<VirtualHost 127.0.0.1:80>

ServerAdmin charith079@gmail.com
DocumentRoot "/usr/local/apache2/htdocs/Server2"
ServerName .......
ServerAlias ............
ErrorLog /usr/local/apache2/logs/server2log

</VirtualHost>

<VirtualHost 127.0.0.1:80>

ServerAdmin charith079@gmail.com
DocumentRoot "/usr/local/apache2/htdocs/Server1"
ServerName .......
ServerAlias .............
ErrorLog /usr/local/apache2/logs/server1log

</VirtualHost>






<VirtualHost 127.0.0.1:443>

ServerAdmin charith079@gmail.com
DocumentRoot /usr/local/apache2/htdocs/ssl
ServerName .........
ServerAlias ............
ErrorLog /usr/local/apache2/logs/server2log

       SSLEngine On


   # Here, I am allowing only "high" and "medium" security key lengths.
SSLCipherSuite HIGH:MEDIUM

# Here I am allowing SSLv3 and TLSv1, I am NOT allowing the old SSLv2.
SSLProtocol all -SSLv2

#   Server Certificate:
SSLCertificateFile /usr/local/apache2/secure.com.crt

#   Server Private Key:
SSLCertificateKeyFile /usr/local/apache2/conf/secure.com.key

#   Server Certificate Chain:
SSLCertificateChainFile /usr/local/apache2/conf/my-ca.crt

#   Certificate Authority (CA):
SSLCACertificateFile /usr/local/apache2/conf/my-ca.crt

# This is needed so that you can use auto-indexing for some directories in the 
# /var/www/SSL directory branch.  This can be handy if you would like to have 
# a list of sensitive files for people to download.
<Directory "/var/www/SSL">
        Options Indexes
        AllowOverride None
        Allow from from all
        Order allow,deny
</Directory>

     
</VirtualHost> 


```**following information may help you **

sudo a2enmod ssl
```
root@charith-desktop:/usr/local/apache2/bin# sudo a2enmod ssl
Module ssl already enabled
root@charith-desktop:/usr/local/apache2/bin# 

```
Thank you very much for your valuable time this is big help for me because I wast lot of time for this but couldn't get answer please help me:lol:

---

