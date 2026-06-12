---
title: "Apache Virtual Hosting"
date: 2007-08-20
forum: Server Platforms
---

### Post by gspathoulas on 2007-08-20
Hello,

I try to setup virtual hosting on UBUNTU Server and I run into an undefined problem.

I have created a file mydomain in sites-available directory (shown below)

I have run the command "a2ensite mydomain"

I have restarted apache by running "/etc/init.d/apache2 reload"

But when I try to access my new site I get the default one.

Somethings that mau be wrong are the <VirtualHost *> tag

or the missing NameVirtualHost at the beggining

Could you please help me ??

The mydomain file is 

<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName mydomain
        DocumentRoot /var/www/mydir
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/mydir>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
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
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by southernman on 2007-08-20
```
sudo a2dissite default
```

---

### Post by gspathoulas on 2007-08-21
Should I disable the default site in order for the second one to work??

---

### Post by gspathoulas on 2007-08-21
Thank you...

It worked

---

### Post by MJN on 2007-08-21
If you've disabled your default site then you're not really doing virtual hosting hence may as well put all your 'virtual' config into the default container.
 
Mathew

---

### Post by southernman on 2007-08-21
> **MJN said:**
> If you've disabled your default site then you're not really doing virtual hosting hence may as well put all your 'virtual' config into the default container.
 
Mathew

True... but they asked about virtual host. I figure they had their reason for going this route. Otherwise I would have suggested just making a backup of the default file and then modify till content... :)

---

