---
title: "[SOLVED] Apache2: How to redirect all requests for www.mydomain.com to mydomain.com"
date: 2008-11-23
forum: Server Platforms
---

### Post by rituraj_tiwari on 2008-11-23
I have read various posts that seem to make this work, but for some reason, my site is not able to redirect browsers from www to non-www site. Any help will be greatly appreciated.

Here is my configuration:
Apache2 on Ubuntu 8.04. I have disabled the default apache site and my sites-enabled has only one file: mydomain. Here are its contents:

```
NameVirtualHost *:443
<VirtualHost *:443>
        ServerName mydomain.com
        ServerAlias www.mydomain.com

        <Location ~ "/SharOn(/|$)">
            # Raj: ProxyPass needs to point to your JBoss server
            ProxyPass http://localhost:8080/SharOn
            ProxyPassReverse https://mydomain.com/SharOn
        </Location>
        <Files yadis-xri.xrdf>
            # Make sure that Apache serves the YADIS services document as the
            # correct content-type.
            ForceType application/xrds+xml
        </Files>
        DocumentRoot /var/www/
        ## Raj: Begin SSL changes
        SSLEngine on

        #SSLOptions +StrictRequire
        SSLCertificateFile /etc/ssl/certs/mydomain.com.crt
        SSLCertificateChainFile /etc/ssl/certs/gd_bundle.crt
        SSLCertificateKeyFile /etc/ssl/private/mydomain.key
        ## Raj: End SSL changes
        LogLevel warn
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>
NameVirtualHost *:80
<VirtualHost *:80>
        ServerName mydomain.com
        ServerAlias www.mydomain.com
        DocumentRoot /var/www/
        <Location ~ "/SharOn(/|$)">
            # Raj: ProxyPass needs to point to your JBoss server
            ProxyPass http://localhost:8080/SharOn
            ProxyPassReverse http://mydomain.com/SharOn
        </Location>
        <Files yadis-xri.xrdf>
            # Make sure that Apache serves the YADIS services document as the
            # correct content-type.
            ForceType application/xrds+xml
        </Files>
        <Directory /SharOn/>
            allow from all
        </Directory>
        LogLevel warn
        ErrorLog /var/log/apache2/error.log
        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

```
I am also using mod-rewrite which was supposed to handle the redirection. Here are the contents of mods-enabled/rewrite.conf:
```
RewriteEngine on
RewriteCond %{HTTP_HOST}   !^$
RewriteCond %{HTTP_HOST}   ^www.(.+)$ [NC]
RewriteRule ^/(.*)         http://%1/$1 [L,R=301]
```

Any ideas, folks?

-Raj

---

### Post by RealPSL on 2008-11-24
The easiest way I have found to solve problems like this is really taking a look at the rewrite logs. That has helped me significantly in the past. You can enable the logs by first adding a line to specify where the log is written.
```
RewriteLog "/var/apache/logs/rewrite.log"
```
Then enable logging with the proper level to be able to decipher why things are not working with
```
RewriteLogLevel 4
```
If you cannot figure it out after looking at the log please post it and I will try to help further.

---

### Post by rituraj_tiwari on 2008-11-24
Thanks a lot for your response. After enabling rewrite logging, I visited [www.mydomain.com](www.mydomain.com). I see absolutely nothing written to my rewrite log file. The file is created by apache, but it is empty.

Since the log file got created after I added those lines, I am sure apache is loading my rewrite.conf file under mods-enabled.

Any more insights as to why I am not triggering the rewrite rules?

Once again, thank you for responding.
-Raj

---

### Post by RealPSL on 2008-11-26
I agree that your rewrite.conf is getting loaded but I think it your rewrite rules are only being loaded for the default web site not the virtual hosts you want it loaded for. I could be wrong but try moving the rewrite rules within the VirtualHost directives and see if you get log entries in the file. I have not done this in a while so it is a little foggy.

---

### Post by rituraj_tiwari on 2008-12-02
That did the trick. Thanks!

---

