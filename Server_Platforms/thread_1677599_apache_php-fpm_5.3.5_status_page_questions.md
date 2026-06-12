---
title: "apache php-fpm 5.3.5 status page questions"
date: 2011-01-29
forum: Server Platforms
---

### Post by michaeld003 on 2011-01-29
I am setting up a virtual host on my webservers to show important information for apache and php-fpm.  I have it all working except the php-fpm status page.  I always get a 404 for the directory not being present.  Doesn't look like it is correctly being handled by php-fpm.  All other pages like /server-status for apache and php pages function correctly.  Any ideas on how to have apache and php-fpm handle it correctly to view the php-fpm status page?  Here is my apache virtualhost .conf file

```
NameVirtualHost 10.10.10.101:80

<Virtualhost 10.10.10.101:80>

        ServerName test-server
        DocumentRoot /app/web/admin

        <IfModule mod_fastcgi.c>
                AddHandler php5-fcgi .php
                Action php5-fcgi /cgi-bin/php5.admin
                <Location "/cgi-bin/php5.admin">
                        Order Deny,Allow
                        Deny from All
                        Allow from env=REDIRECT_STATUS
                        Options ExecCGI
                        SetHandler fastcgi-script
                </Location>

        </IfModule>

        # Fast CGI + FPM
        FastCgiExternalServer /app/web/cgi-bin/php5.admin  -socket /tmp/php-fpm.sock
        Alias /cgi-bin/ /app/web/cgi-bin/


        <Directory /app/web/admin>
                DirectoryIndex index.html
                Order allow,deny
                Allow from all

        </Directory>

        <Location /server-status>
                SetHandler server-status
                Order allow,deny
                Allow from all
        </Location>

        <Location /server-info>
                SetHandler server-info
                Order allow,deny
                Allow from all
        </Location>


        <Location /fpm-status>
                SetHandler fastcgi-script
                Order allow,deny
                Allow from all
        </Location>

</Virtualhost>
```

Thanks for any and all help!

---

