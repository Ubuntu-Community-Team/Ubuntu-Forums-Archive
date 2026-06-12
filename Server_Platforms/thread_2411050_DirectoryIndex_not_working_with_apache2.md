---
title: "DirectoryIndex not working with apache2"
date: 2019-01-24
forum: Server Platforms
---

### Post by karmicwarri0r on 2019-01-24
Hi Everyone!

We are on Ubuntu 16.04 and have installed apache2 webserver. We are facing an issue with respect to URLs in that the URLs ending with directory name are not displaying the contained index.html file "only in case of secure URLs". The non-secure urls work perfectly fine.

So
[http://domainname.com/landingpage/](http://domainname.com/landingpage/)   (works and displays the containing index.html file)
http[COLOR=#ff0000]**s**[/COLOR]://domainname.com/landingpage/ (broken, with forbidden 403 error)

Also, if on https I try to access the direct url of the index.html file, the browser redirects to a url that has document root suffixed to the primary domain.

[https://domainname.com/landingpage/index.html](https://domainname.com/landingpage/index.html)
redirects to
[https://domainname.com/var/www/html](https://domainname.com/var/www/html)

I take it that this is a misconfiguration and having tried a number of ways, I seek help/suggestions on how this can be resolved.

Thank you.

---

### Post by howefield on 2019-01-24
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by LHammonds on 2019-01-24
Yes, this is a misconfiguration so please post both of your site configs in CODE tags.

LHammonds

---

### Post by SeijiSensei on 2019-01-24
What errors do you see in /var/log/apache2/error.log?

Does anything work correctly in the https site?

---

### Post by karmicwarri0r on 2019-01-25
The site otherwise works fine on ssl. Here is one relevant error in logs;

AH01630: client denied by server configuration: /var/www/html/site_main/kr/lp/award-winning/.html

---

### Post by karmicwarri0r on 2019-01-25
Here you go:

```

<VirtualHost *:80>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName REDACTED.com
        ServerAlias www.REDACTED.com


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html/bbm_main


         <Directory /var/www/html/bbm_main>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
        Require all granted
        </Directory>


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf


        #RewriteEngine on
        #RewriteCond %{SERVER_NAME} =REDACTED.com [OR]
        #RewriteCond %{SERVER_NAME} =www.REDACTED.com
        #RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]


</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet



```


and this....

```

<IfModule mod_ssl.c>
<VirtualHost *:443>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        ServerName REDACTED.com
        ServerAlias www.REDACTED.com


        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html/bbm_main


        <Directory /var/www/html/bbm_main>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        #Order allow,deny
        #allow from all
        Require all granted
        </Directory>


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf        
Include /etc/letsencrypt/options-ssl-apache.conf
SSLCertificateFile /etc/letsencrypt/live/REDACTED.com/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/REDACTED.com/privkey.pem
</VirtualHost>
</IfModule>


```

---

### Post by karmicwarri0r on 2019-01-25
Here is an update..

I was mistaken. It is not the index.html that is required to be displayed but the file with same directory name with .html extension. 

So,
[https://domainname.com/en/landingpage]("https://domainname.com/landingpage/index.html")
[COLOR=#000000] should display
[/COLOR][https://domainname.com/en/landingpage.html]("https://domainname.com/var/www/html")

I have been able to make it work even on https but for some reason, the url with trailing slash does not work. 

[https://domainname.com/en/landingpage/]("https://domainname.com/landingpage/index.html")
[COLOR=#000000][/COLOR]
does not works. I have also tried removing trailing slashes using the following code in htaccess but it doesnt work.

```
[COLOR=#000000]# remove trailing slash
[/COLOR][COLOR=#000000]RewriteRule ^(.*)/$ /$1 [L,R=301][/COLOR]
``` 

Sorry about the confusion, guys!

---

