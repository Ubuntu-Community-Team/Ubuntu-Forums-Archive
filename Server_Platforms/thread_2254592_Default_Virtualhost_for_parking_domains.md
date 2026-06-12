---
title: "Default Virtualhost for parking domains"
date: 2014-11-28
forum: Server Platforms
---

### Post by fc400ef7 on 2014-11-28
I have many parked domain names and I've created each a domain.conf file and ultimately point each to a /var/www/parking directory while disabling 000-defualt.conf.  I've had to take this approach because when I enable 000-default.conf in apache I get erratic results.  By erratic results I mean some sites enabled or not will still go to parking.

What I would like to do is have any domain name that doesn't have an apache configuration enabled to go to a particular site exmple.com/parking.

---

### Post by nerdtron on 2014-11-28
You can try posting here your vhosts configs both the default one and for the parking domain so that other experts can get a clearer picture on what is happening.

---

### Post by fc400ef7 on 2014-11-28
**000-default.conf**
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/parking/html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


**example.com.conf**
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName example.com
        DocumentRoot /var/www/example.com/html
        LogLevel warn
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # Mod rw
        RewriteEngine   on
        #RewriteCond     %{SERVER_PORT} ^80$
        #RewriteRule     ^(.*)$ https://%{SERVER_NAME}$1 [L,R]

       <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
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


        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

---

