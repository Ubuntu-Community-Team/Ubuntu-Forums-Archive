---
title: "Virtual Host with Proxy Problem"
date: 2008-11-15
forum: Server Platforms
---

### Post by Black Mage on 2008-11-15
I am trying to make virtual host where I can create a virtual host that uses another web server on the network. My current set up looks like

```

<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName db.servername.com
        DocumentRoot /var/www/phpmyadmin/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/phpmyadmin/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>


ProxyRequests Off

</VirtualHost>

#<proxy>
 #         Order deny,allow
 #
#          Allow from all
#</proxy>
#
#ProxyPass / http://192.168.1.201/
#ProxyPassReverse / http://192.168.1.201/


```

The problem arises when I uncomment the proxy information, all the host then go to the other server, instead of the one virtual host. Does anyone have any suggestions?

Thanks

---

