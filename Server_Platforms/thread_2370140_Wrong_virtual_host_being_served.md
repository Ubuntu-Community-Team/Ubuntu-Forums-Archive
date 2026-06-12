---
title: "Wrong virtual host being served"
date: 2017-08-31
forum: Server Platforms
---

### Post by bushsolo on 2017-08-31
I've been building Linux servers for a long time but am stumped by this. Three virtual hosts, one for the IP (blank page served), second for the main site and third for file downloads. When going to downloads.example.net you get served the example.net virtual host on either HTTP or HTTPS. Checking syntax and displaying virtual hosts show no errors. I've spent too long on this, it should be simple but it is not working.

I'm using self signed certs as the server is behind CloudFlare which adds its own cert when served to users, crypto support on CloudFlare is set to Full so it connects to my server on SSL as opposed to Flexible where it connects on HTTP but serves on HTTPS.

```
    <VirtualHost *:80>
        ServerName 111.222.233.244
        ServerAdmin support@localhost
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>

    <VirtualHost *:80>
        ServerName downloads.example.net
        ServerAlias downloads.example.info
        ServerAdmin support@example.net
        DocumentRoot /var/www/downloads

        ErrorLog ${APACHE_LOG_DIR}/downloaderror.log
        CustomLog ${APACHE_LOG_DIR}/downloadaccess.log combined
    </VirtualHost>

    <VirtualHost *:80>
        ServerName www.example.net
        ServerAlias example.net
        ServerAdmin support@example.net
        DocumentRoot /var/www/wordpress

        ErrorLog ${APACHE_LOG_DIR}/exampleerror.log
        CustomLog ${APACHE_LOG_DIR}/exampleaccess.log combined
    </VirtualHost>

    <IfModule mod_ssl.c>
      <VirtualHost *:443>
        ServerName 111.222.233.244
        ServerAdmin support@localhost
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/example.crt
        SSLCertificateKeyFile /etc/apache2/ssl/example.key

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
        </Directory>
        BrowserMatch "MSIE [2-6]" \
                        nokeepalive ssl-unclean-shutdown \
                        downgrade-1.0 force-response-1.0
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
      </VirtualHost>

      <VirtualHost *:443>
        ServerName downloads.example.net
        ServerAlias downloads.example.info
        ServerAdmin support@example.net
        DocumentRoot /var/www/downloads

        ErrorLog ${APACHE_LOG_DIR}/downloaderror.log
        CustomLog ${APACHE_LOG_DIR}/downloadaccess.log combined

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/example.crt
        SSLCertificateKeyFile /etc/apache2/ssl/example.key

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
        </Directory>

        BrowserMatch "MSIE [2-6]" \
                        nokeepalive ssl-unclean-shutdown \
                        downgrade-1.0 force-response-1.0
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
      </VirtualHost>

      <VirtualHost *:443>
        ServerName www.example.net
        ServerAlias example.net
        ServerAlias www.example.info
        ServerAlias example.info
        ServerAdmin support@example.net
        DocumentRoot /var/www/wordpress

        ErrorLog ${APACHE_LOG_DIR}/exampleerror.log
        CustomLog ${APACHE_LOG_DIR}/exampleaccess.log combined

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/example.crt
        SSLCertificateKeyFile /etc/apache2/ssl/example.key

        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                        SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                        SSLOptions +StdEnvVars
        </Directory>

        BrowserMatch "MSIE [2-6]" \
                        nokeepalive ssl-unclean-shutdown \
                        downgrade-1.0 force-response-1.0
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
      </VirtualHost>
    </IfModule>
```

Results from debugging.

```
    apache2ctl -t    Syntax OK

    apache2ctl -S
    VirtualHost configuration:
    *:80                   is a NameVirtualHost
         default server 111.222.233.244 (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost 111.222.233.244 (/etc/apache2/sites-enabled/000-default.conf:1)
         port 80 namevhost downloads.example.net (/etc/apache2/sites-enabled/000-default.conf:10)
         port 80 namevhost www.example.net (/etc/apache2/sites-enabled/000-default.conf:25)
                 alias example.net
    *:443                  is a NameVirtualHost
         default server 111.222.233.244 (/etc/apache2/sites-enabled/000-default.conf:43)
         port 443 namevhost 111.222.233.244 (/etc/apache2/sites-enabled/000-default.conf:43)
         port 443 namevhost downloads.example.net (/etc/apache2/sites-enabled/000-default.conf:67)
         port 443 namevhost www.example.net (/etc/apache2/sites-enabled/000-default.conf:93)
                 alias example.net
    ServerRoot: "/etc/apache2"
    Main DocumentRoot: "/var/www/html"
    Main ErrorLog: "/var/log/apache2/error.log"
    Mutex rewrite-map: using_defaults
    Mutex ssl-stapling-refresh: using_defaults
    Mutex ssl-stapling: using_defaults
    Mutex ssl-cache: using_defaults
    Mutex default: dir="/var/lock/apache2" mechanism=fcntl
    Mutex mpm-accept: using_defaults
    Mutex watchdog-callback: using_defaults
    PidFile: "/var/run/apache2/apache2.pid"
    Define: DUMP_VHOSTS
    Define: DUMP_RUN_CFG
    User: name="www-data" id=33
    Group: name="www-data" id=33

```

---

### Post by bushsolo on 2017-08-31
Tried this configuration for HTTP only, no SSL. just two entries. downloads.example.net gets sent to example.net. This is now a very simple configuration and I cannot see a reason why it would not work.

```
<VirtualHost *:80>        ServerName downloads.example.net
        ServerAdmin support@example.net
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

<VirtualHost *:80>
        ServerName example.net
        ServerAlias www.example.net
        ServerAdmin support@example.net
        DocumentRoot /var/www/wordpress

        ErrorLog ${APACHE_LOG_DIR}/ufoerror.log
        CustomLog ${APACHE_LOG_DIR}/ufoaccess.log combined
</VirtualHost>
```

---

### Post by LHammonds on 2017-08-31
> **bushsolo said:**
> Tried this configuration for HTTP only, no SSL. just two entries. downloads.example.net gets sent to example.net. This is now a very simple configuration and I cannot see a reason why it would not work.

```
<VirtualHost *:80>        ServerName downloads.example.net
        ServerAdmin support@example.net
        DocumentRoot /var/www/html

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

<VirtualHost *:80>
        ServerName example.net
        ServerAlias www.example.net
        ServerAdmin support@example.net
        DocumentRoot /var/www/wordpress

        ErrorLog ${APACHE_LOG_DIR}/ufoerror.log
        CustomLog ${APACHE_LOG_DIR}/ufoaccess.log combined
</VirtualHost>
```

That config worked for me.

Make sure your domain name resolution is pointing both of them to the same IP as your web server.

I made a custom "index.php" in both root folders so I could see which page was being displayed.

I  then made sure to edit my local host file on my PC so that when I ping  "downloads.example.net" or "www.example.net" I would get the IP of my  server.

I then loaded up Firefox and typed in each of those two domain names and they each displayed the correct/expected web page.

Tested on Ubuntu Server 16.04.3 LTS, Apache 2.4.18, PHP 7.0.22

LHammonds

---

### Post by johnerin22 on 2017-09-02
you're on the right config, try to read the access log!
or try to remove [COLOR=#000000][FONT=&quot]VirtualHost for [/FONT][/COLOR][COLOR=#000000][FONT=&quot]example.net
just to debug it.[/FONT][/COLOR]

---

