---
title: "Webdav 405 Method Not Allowed"
date: 2011-05-06
forum: Server Platforms
---

### Post by Jake.Debord on 2011-05-06
Trying to setup WebDav on Ubuntu server. Stuck on the last few steps of the setup. Trying to test the setup with cadaver, but reach this error:
 
cadaver [http://10.0.6.103/webdav](http://10.0.6.103/webdav)

Could not access /webdav/ (not WebDAV-enabled?):
405 Method Not Allowed
Connection to `10.0.6.103' closed.

-----------------------------------------------------------------------------------------------------------

**This is my sites-available file contents:**


<VirtualHost *:50495>
    ServerAdmin webmaster@localhost

DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
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
ServerName Sugar

</VirtualHost>

#NameVirtualHost *:80
<VirtualHost *:80>
DocumentRoot /var/www/web1/web
ServerAdmin webmaster@localhost
<Directory /var/www/web1/web/>
Options Indexes MultiViews
AllowOverride None
Order allow,deny
Allow from all
</Directory>

        Alias /webdav /var/www/web1/web

        <Location /webdav>
           DAV On
           AuthType Basic
           AuthName "webdav"
           AuthUserFile /var/www/web1/passwd.dav
           Require valid-user
       </Location>
</VirtualHost>

---

### Post by Jake.Debord on 2011-05-06
Okay, so In this file I switched the order around of the virtual servers... When I put the Webdav above the other on, then Webdav works but the other doesn't... 

What do I need to do to be able to make these two servers play nice???

---

### Post by Jake.Debord on 2011-05-06
Fixed it by changing the permissions of the /var/www/web1 folder from www-data to root

so user & group both = root

also,

had to change this: 

<VirtualHost *:50495>

to say this:


<VirtualHost 10.0.6.103:50495>


and had to edit this:

#NameVirtualHost *:80
<VirtualHost *:80>

to say this:

NameVirtualHost *
<VirtualHost 10.0.6.103:80>

---

