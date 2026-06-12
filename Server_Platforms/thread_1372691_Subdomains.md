---
title: "Subdomains"
date: 2010-01-04
forum: Server Platforms
---

### Post by Skidbladniir on 2010-01-04
I am a newbie to Ubuntu server, and Apache, and was wondering how I might create a subdomain.  I use zone records and have a CNAME for the subdomain 'admin.mysite.com' pointing to my server.  What now?  My current config just forwards it to /var/www...

/etc/apache2/sites-available/default
```

NameVirtualHost *:80

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options ExecCGI FollowSymLinks MultiViews
                AllowOverride None
                AddHandler cgi-script cgi pl
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

        <Directory "/var/www/download">
                AllowOverride None
                Options -ExecCGI +Indexes
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName admin.localhost
        ServerAlias admin.localhost

        DocumentRoot /var/admin
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/admin>
                Options ExecCGI FollowSymLinks MultiViews
                AllowOverride None
                AddHandler cgi-script cgi pl
                Order deny,allow
                deny from all
                allow from localhost
                allow from 70.112.152.206
        </Directory>

        Errorlog /var/log/apache2/error.log
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

```

---

### Post by Skidbladniir on 2010-01-04
Also, when I try to start Apache, I get a no virtual hosts error....

```

/etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                                                               [Mon Jan 04 19:26:00 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Mon Jan 04 19:26:00 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Mon Jan 04 19:26:01 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Mon Jan 04 19:26:01 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                                                                                                        [ OK ]

```

---

### Post by munky99999 on 2010-01-04
```
        ServerName admi.localhost
        ServerAlias admi.localhost
```

Should be admin.mysite.com. I think anyway. Personally I cant use virtual hosts as I have to use SSL. Which afaik isnt functionable.


Also since it's the same server. Your virtual host for the original site should be above the admin.mysite.com; as above is what is default used.

---

### Post by HighCommander540 on 2010-01-04
> **munky99999 said:**
> ```
        ServerName admi.localhost
        ServerAlias admi.localhost
```

Should be admin.mysite.com. I think anyway. Personally I cant use virtual hosts as I have to use SSL. Which afaik isnt functionable.


Also since it's the same server. Your virtual host for the original site should be above the admin.mysite.com; as above is what is default used.

You can still use virtual hosts. Just not more than one SSL virtual host. You can still have others.

---

### Post by Skidbladniir on 2010-01-04
> **munky99999 said:**
> ```
        ServerName admi.localhost
        ServerAlias admi.localhost
```Should be admin.mysite.com. I think anyway. Personally I cant use virtual hosts as I have to use SSL. Which afaik isnt functionable.


Also since it's the same server. Your virtual host for the original site should be above the admin.mysite.com; as above is what is default used.
It is.  I was testing something (trying to see if it was a simple configuration error), and I forgot to change it back before I posted it.  Also, the www site is the first one, followed by the admin.mysite

---

### Post by Vegan on 2010-01-04
I have my machine setup far differently but the domain concepts are the same. I can post my setup files on my site when I get time and I am going to make lots of new pages too this winter and into spring.

---

### Post by BkkBonanza on 2010-01-05
You can have as many SSL virtual hosts as you need - you just need to create an IP for each one and specifiy the IP in the VirtualHost directive. Since the http layer info is encrypted it cannot be used to match virtual host name - so it has to be directed to a specific IP address.

The problem for most admins is that they have to buy a (public) IP address for each SSL site. But you can run test sites on private IPs easily enough without cost.

OP: just check your syntax carefully again. You are likely missing some small detail as it looks ok in general.

---

