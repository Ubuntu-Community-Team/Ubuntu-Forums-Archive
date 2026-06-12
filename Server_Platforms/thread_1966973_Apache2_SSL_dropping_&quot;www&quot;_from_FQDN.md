---
title: "Apache2 SSL dropping &quot;www&quot; from FQDN"
date: 2012-04-27
forum: Server Platforms
---

### Post by ekinnee on 2012-04-27
So, I have a site. [www.kinnee.net](www.kinnee.net) that I'm trying to get SSL setup on. SSL is working, but it's complaining about the cert because the host name doesn't match. If I hit [http://www.kinnee.net](http://www.kinnee.net) it's redirecting to https as it's supposed to but it's going to [https://kinnee.net](https://kinnee.net) NOT [https://www.kinnee.net](https://www.kinnee.net) like I want it to.

000-default

[HTML]
<VirtualHost *:80>
        DocumentRoot /var/www/

        RewriteEngine On
        RewriteCond %{HTTPS} off
        RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}
</VirtualHost>
<VirtualHost *:443>
        ServerAdmin [email]erick@kinnee.net[/email]

        DocumentRoot /var/www/
        SSLEngine on
        SSLOptions +StrictRequire
        SSLCertificateChainFile /etc/ssl/kinnee.net.ca-bundle
        <Directory />
                Options FollowSymLinks
                AllowOverride None
                SSLRequireSSL
        </Directory>
        SSLProtocol -all +TLSv1 +SSLv3
        SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM

        SSLSessionCacheTimeout 600

        SSLCertificateFile /etc/ssl/kinnee.net.crt
        SSLCertificateKeyFile /etc/ssl/kinnee.net.key

        SSLVerifyClient none
        SSLProxyEngine off

        <IfModule mime.c>
                AddType application/x-x509-ca-cert      .crt
                AddType application/x-pkcs7-crl         .crl
        </IfModule>

        SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown downgrade-1.0 force-response-1.0
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
[/HTML]

---

### Post by ekinnee on 2012-04-27
Ok, I just fixed it. Seems it was a setting within WordPress. Had to change the server address there to [www.kinnee.net](www.kinnee.net).

---

### Post by josephmills on 2012-04-27
** EDIT **

Thanks for marking as solved 
&& 
Glad to see you worked it out


Thanks 
:KS

---

