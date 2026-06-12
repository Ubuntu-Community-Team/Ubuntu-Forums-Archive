---
title: "APache2, SSL and Init: Private key not found"
date: 2007-07-28
forum: Server Platforms
---

### Post by PgR on 2007-07-28
Hi folks,

I have apache2 running quite happily on 7.04. I'm trying to set up ssl without much luck.
Before anyone points me to the helpful-looking howto over at [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL) I've been there, done that, and still no luck.

I've obtained .key and .crt files from startcom, and copied them to /etc/apache2/ssl/ (which didn't exist until I created it manually) and /etc/ssl/certs & /etc/ssl/private as instructed on different howto's,

I've created /sites-available/ssl 
```
NameVirtualHost *:443
<VirtualHost *:443>
Alias /squirrelmail /usr/share/squirrelmail
DocumentRoot /usr/share/squirrelmail
        SSLEngine On
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        SSLCertificateFile /etc/ssl/certs/ssl.crt
        SSLCertificateKeyFile /etc/ssl/private/ssl.key
#       SSLCertificateChainFile /etc/apache2/ssl/sub.class1.server.ca.crt
#       SSLCACertificateFile /etc/apache2/ssl/ca.crt
#       SSLProtocol all
#       SSLCipherSuite HIGH:MEDIUM
<Directory /usr/share/squirrelmail>
  Options Indexes FollowSymLinks
  <IfModule mod_php4.c>
    php_flag register_globals off
  </IfModule>
  <IfModule mod_php5.c>
    php_flag register_globals off
  </IfModule>
  <IfModule mod_dir.c>
    DirectoryIndex index.php
  </IfModule>

  # access to configtest is limited by default to prevent information leak
  <Files configtest.php>
    order deny,allow
    deny from all
    allow from 192.168.70.2
  </Files>
</Directory>
</VirtualHost>
# users will prefer a simple URL like http://webmail.example.com
#<VirtualHost 192.168.70.200:443>
#  DocumentRoot /usr/share/squirrelmail
#  ServerName webmail.example.com
#</VirtualHost>

# redirect to https when available (thanks omen@descolada.dartmouth.edu)
#
#  Note: There are multiple ways to do this, and which one is suitable for
#  your site's configuration depends. Consult the apache documentation if
#  you're unsure, as this example might not work everywhere.
#
#<IfModule mod_rewrite.c>
#  <IfModule mod_ssl.c>
#    <Location /squirrelmail>
#      RewriteEngine on
#      RewriteCond %{HTTPS} !^on$ [NC]
#      RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
#    </Location>
#  </IfModule>
#</IfModule>

```

When I try to start apache ( /etc/init.d/apache2 start )  /var/log/apache2/error.log shows 

```
[Sat Jul 28 23:16:38 2007] [error] Init: Private key not found
[Sat Jul 28 23:16:38 2007] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Sat Jul 28 23:16:38 2007] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Sat Jul 28 23:16:38 2007] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Sat Jul 28 23:16:38 2007] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
```

I've tried (out of sheer desperation) chmod 777 (it's not a publicly available server yet!) but that doesn't make any difference. If only the "Private key not found" line was a little more helpful.

Any ideas?

---

