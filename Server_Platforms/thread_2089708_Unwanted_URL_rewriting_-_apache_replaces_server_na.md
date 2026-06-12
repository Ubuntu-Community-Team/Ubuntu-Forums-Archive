---
title: "Unwanted URL rewriting - apache replaces server name with ip in address bar"
date: 2012-11-30
forum: Server Platforms
---

### Post by topche on 2012-11-30
I have a problem with one of my servers; When I enter 
[http://www.myserver.com](http://www.myserver.com) in address bar (IE & Firefox), apache replaces the 
server name (e.g. [www.myserver.com](www.myserver.com)) with an ip address. 
What I miss in my configuration:
```

<VirtualHost *:80>
        ServerAdmin administrator@my.domain.com
        ServerAlias hers.is.my.hostname
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options -Indexes FollowSymLinks -MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


```
```

cat apache2.conf |grep -v ^#



LockFile ${APACHE_LOCK_DIR}/accept.lock

PidFile ${APACHE_PID_FILE}

Timeout 300

KeepAlive On

MaxKeepAliveRequests 100

KeepAliveTimeout 5


<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}


AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

DefaultType None


HostnameLookups Off

ErrorLog ${APACHE_LOG_DIR}/error.log

LogLevel warn

Include mods-enabled/*.load
Include mods-enabled/*.conf

Include httpd.conf

Include ports.conf

LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent


Include conf.d/

Include sites-enabled/


```

---

