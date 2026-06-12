---
title: "MAAS + Lanscape"
date: 2017-04-20
forum: Ubuntu Cloud and Juju
---

### Post by krisclarkdev on 2017-04-20
Can Landscape be installed on the same machine as MAAS?  I installed landscape on 16.04 LTS without issue.  After which I've installed MAAS and something seems to not want these two on the same machine because HOSTNAME:80 no longer brings me to Landscape but the default Apache page.

16.04 Server LTS x64
Fresh install, nothing else except landscape and MAAS

---

### Post by krisclarkdev on 2017-04-20
MAAS's conf-enabled entry was overriding Landscapes sites-enabled entry

The following [COLOR=#33BBC8][FONT=Menlo]/etc/apache2/conf-enabled/[/FONT][/COLOR]maas-http.conf fixed the issue```
#<IfModule mod_ssl.c>
#    <VirtualHost *:443>
#        SSLEngine On
#        # Do not rely on these certificates, generate your own.
#        SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
#        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
#    </VirtualHost>
#</IfModule>


<IfModule mod_expires.c>
    <Location /MAAS/>
        ExpiresActive On
        ExpiresByType text/javascript "access plus 1 hours"
        ExpiresByType application/javascript "access plus 1 hours"
        ExpiresByType application/x-javascript "access plus 1 hours"
        ExpiresByType text/css "access plus 1 hours"
        ExpiresByType image/gif "access plus 1 hours"
        ExpiresByType image/jpeg "access plus 1 hours"
        ExpiresByType image/png "access plus 1 hours"
    </Location>
</IfModule>


<IfModule alias_module>
    Alias /MAAS/static/ /usr/share/maas/web/static/
</IfModule>


<IfModule proxy_module>
    ProxyPreserveHost on
    ProxyPass /MAAS/ws "ws://localhost:5240/MAAS/ws"
    ProxyPass /MAAS/static/ !
    ProxyPass /MAAS/ [http://localhost:5240/MAAS/](http://localhost:5240/MAAS/)
    ProxyPass /MAAS [http://localhost:5240/MAAS/](http://localhost:5240/MAAS/)
</IfModule>


<IfModule rewrite_module>
    RewriteEngine On
    # Redirect (permanently) requests for /MAAS to /MAAS/.
    RewriteRule ^/MAAS$ %{REQUEST_URI}/ [R=301,L]
</IfModule>
```

---

