---
title: "Ubuntu Server"
date: 2011-02-19
forum: Server Platforms
---

### Post by falcon1620 on 2011-02-19
Hi, I have a question about .htaccess on my server. I am using Ubuntu 10.10. Generally the .htaccess file works as expected and the directory is password protected EXCEPT when I use https:// in the address, then the directories are not protected... :confused: So I am not sure how to correct this issue with out disabling https. Basically I want a way to protect files on here that other users have with out giving them access to the web server configuration. Thanks :)

 
My .htaccess file looks like this
```

:/var/htpasswd# cat .htaccess
AuthName "Password Required: Dev"
AuthType Basic
AuthUserFile /var/htpasswd/.htpasswd-users
Require valid-user

```

and I have modified the Apache config as such: 
```

# cat /etc/apache2/sites-enabled/000-default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
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

```
:lolflag:

---

### Post by rudelgurke on 2011-02-20
How does the configuration for your SSL Vhost looks ?

---

### Post by falcon1620 on 2011-02-22
Wow there you go right in front of me :KS Thanks ):P

That would do it. You can see that I am still learning Ubuntu and Debian LOL  Thanks!

---

