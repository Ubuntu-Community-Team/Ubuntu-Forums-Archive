---
title: "apache2 and webmin config"
date: 2012-01-10
forum: Server Platforms
---

### Post by dbecker on 2012-01-10
using webmin to manage apache2

created 3 virtual virtual hosts in webmin for: 
domain.com
sub.domain.com
sub2.domain.com

created 3 A-records in DNS:
@ - PUB-IP
sub - PUB-IP
sub2 - PUB-IP

All 3 sites resolve fine and the correct pages are loaded, however, when someone enters [http://PUB-IP](http://PUB-IP) into a browser, sub.domain.com is loaded. 

How do I change it so that [http://PUB-IP](http://PUB-IP) will just throw a 404 error, or go to Apache's default var/www/index.html ? 

thanks!

---

### Post by SeijiSensei on 2012-01-10
If you followed the standard practice of putting virtual sites into separate configuration files in the directory /etc/apache2/sites-enabled, then the first site alphabetically in that directory will handle all requests for sites that do not have a specified definition.  If you look in that directory, you'll see that the file that defines the default site is called 000-default.  It should load ahead of any name-based virtual hosts and handle the default requests.  Since that isn't happening for you, I'm guessing you defined the virtual hosts somewhere else.  Try moving all the <VirtualHost> containers into separate files in sites-enabled and make sure they sort below 000-default.

---

### Post by dbecker on 2012-01-10
> **SeijiSensei said:**
> If you followed the standard practice of putting virtual sites into separate configuration files in the directory /etc/apache2/sites-enabled, then the first site alphabetically in that directory will handle all requests for sites that do not have a specified definition.  If you look in that directory, you'll see that the file that defines the default site is called 000-default.  It should load ahead of any name-based virtual hosts and handle the default requests.  Since that isn't happening for you, I'm guessing you defined the virtual hosts somewhere else.  Try moving all the <VirtualHost> containers into separate files in sites-enabled and make sure they sort below 000-default.

thanks for the reply. 

sure enough, the first config file in /etc/apache2/sites-available is sub.domain.com, which does indeed handle un-specified requests, such as [http://PUB-IP](http://PUB-IP)

I do see the 000-default config. in /sites-enabled, but it points to a blank /sites-available/default file. Could I simply fill /sites-available/default with the following?: 

```
DocumentRoot "/usr/www"
DirectoryIndex index.html
<Directory "/usr/www">
allow from all
Options +Indexes
</Directory>
```

---

### Post by SeijiSensei on 2012-01-11
That's strange; the sites-available/default file on all the Ubuntu servers I've looked at has these contents:

```

<VirtualHost *:80>
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

</VirtualHost>

```

You can safely exclude the definition for /usr/share/doc/.

---

