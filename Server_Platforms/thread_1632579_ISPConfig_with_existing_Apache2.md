---
title: "ISPConfig with existing Apache2"
date: 2010-11-28
forum: Server Platforms
---

### Post by megabuffen on 2010-11-28
I would like to install ISPConfig 3 on my Ubuntu 10.04 server. However, when I tried doing this according to the "[perfect server]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3")" instructions at HowtoForge, all my virtual hosts would suddenly return a 403 error whenever i tried to access them. The stange thing is that all my virtual host configurations where still in place and enabled. I do understand that ISPConfig automatically configures Apache2, but is there any way to install it without ruining the existing configuration?

---

### Post by James78 on 2010-11-28
Do you have any files to serve in your Virtualhosts document root?

At the moment, I don't know if it's possible to have it "not ruin your configuration". Maybe if you post the messed up config I can see if there's a problem?

---

### Post by megabuffen on 2010-11-28
Yep, my virtualhosts are all serving files. One of them is PHPMyAdmin. These are the config files after installing ISPConfig - i have removed comments:

/etc/apache2/apache2.conf
```

ServerName megabuffen.dyndns.org

ServerRoot "/etc/apache2"

#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

PidFile ${APACHE_PID_FILE}

Timeout 300

KeepAlive On

MaxKeepAliveRequests 100

KeepAliveTimeout 15

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
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
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

DefaultType text/plain

HostnameLookups Off

ErrorLog /var/log/apache2/error.log

LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf

%{X-Forwarded-For}i

LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/
Include /etc/phpmyadmin/apache.conf

```/etc/apache2/httpd.conf
```

Options -ExecCGI
AddDefaultCharset UTF-8
NameVirtualHost *

```/etc/apache2/ports.conf
```

Listen 80

<IfModule mod_ssl.c>
Listen 443
</IfModule>

<IfModule mod_gnutls.c>
Listen 443
</IfModule>

```/etc/apache2/conf.d/javascript-common.conf
 ```

 Alias /javascript /usr/share/javascript/

<Directory "/usr/share/javascript/">
    Options FollowSymLinks MultiViews
</Directory>

```/etc/apache2/conf.d/virtual.conf
  ```

  NameVirtualHost *:80
NameVirtualHost *:443
 
```These virtualhost configs are symlinked in the sites-enable directory.

/etc/apache2/sites-available/ispconfig.conf
   ```

   LogFormat "%v %h %l %u %t \"%r\" %>s %B \"%{Referer}i\" \"%{User-Agent}i\"" combined_ispconfig
CustomLog "| /usr/local/ispconfig/server/scripts/vlogger -s access.log -t \"%Y%m%d-access.log\" -d \"/etc/vlogger-dbi.conf\" /var/log/ispconfig/httpd" combined_ispconfig

<Directory /var/www/clients>
    AllowOverride None
    Order Deny,Allow
    Deny from all
</Directory>

# Do not allow access to the root file system of the server for security reasons
<Directory />
       AllowOverride None
       Order Deny,Allow
       Deny from all
</Directory>

# Except of the following directories that contain website scripts
<Directory /usr/share/phpmyadmin>
        Order allow,deny
        Allow from all
</Directory>

<Directory /usr/share/phpMyAdmin>
        Order allow,deny
        Allow from all
</Directory>

<Directory /usr/share/squirrelmail>
        Order allow,deny
        Allow from all
</Directory>

# allow path to awstats and alias for awstats icons
<Directory /usr/share/awstats>
        Order allow,deny
        Allow from all
</Directory>
Alias /awstats-icon "/usr/share/awstats/icon"
  
```/etc/apache2/sites-available/apps.vhost
    ```

      Listen 8081
# NameVirtualHost *:8081

<VirtualHost _default_:8081>
  ServerAdmin webmaster@localhost
  
  
  <IfModule mod_fcgid.c>
    DocumentRoot /var/www/apps
    SuexecUserGroup ispapps ispapps
    <Directory /var/www/apps>
      Options Indexes FollowSymLinks MultiViews +ExecCGI
      AllowOverride AuthConfig Indexes Limit Options FileInfo
      AddHandler fcgid-script .php
      FCGIWrapper /var/www/php-fcgi-scripts/apps/.php-fcgi-starter .php
      Order allow,deny
      Allow from all
    </Directory>
  </IfModule>
  
  <IfModule mod_php5.c>
    DocumentRoot /var/www/apps
    AddType application/x-httpd-php .php
    <Directory /var/www/apps>
      Options FollowSymLinks
      AllowOverride None
      Order allow,deny
      Allow from all
    </Directory>
  </IfModule>
  
  ServerSignature Off

</VirtualHost>
   
```/etc/apache2/sites-available/default
    ```

    NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@eneroth.dyndns.org
    AssignUserId www-default www-default
        # Indexes + Directory Root.
        DirectoryIndex index.php
        DocumentRoot /var/www/default/htdocs/
        # Logfiles
        ErrorLog  /var/www/default/logs/error.log
        CustomLog /var/www/default/logs/access.log combined
</VirtualHost>
   
```

The virtualhosts are same as default with NameVirtualHost *:80 removed, ServerName/ServerAlias added and using different user accounts. Considering it was a 403 error I tried chmod 777 on /var/www and subfolders, but without success.

---

### Post by megabuffen on 2010-11-28
I found the problem. It was a "Deny from all" entry withing <Directory></Directory> in ispconfig.conf.

---

