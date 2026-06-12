---
title: "VirtualHost responding to all subdomains"
date: 2006-09-22
forum: Server Platforms
---

### Post by MystaMax on 2006-09-22
Hello, I have a ubuntu apache server setup w/ the FQDN of webdev.MYDOMAIN.com. I copied the default vhost file (in /etc/apache2/sites-available/) and renamed it to ktdms (I basically followed the ubuntu server guide). I altered the file so that dms.MYDOMAIN.com would go to /var/www/ktdms. All is good, but [apache was reporting errors]("http://ubuntuforums.org/showthread.php?t=260267") when I was restarting apache. **After making changes again, all request to this webdev.MYDOMAIN.com go directory to the vhost ktdms**. I want webdev.MYDOMAIN.com to go to the root listing.

 I also have a DNS entry for knowledgetree.MYDOMAIN.com and even that goes to dms.MYDOMAIN.com, but no vhost is setup for that address. So I was hoping someone could help. I'll post both my default and ktdms vhost files

[SIZE=4]This is my default vhost file[/SIZE]
```

NameVirtualHost webdev.MYDOMAIN.com
<VirtualHost webdev.MYDOMAIN.com>
        ServerAdmin webmaster@localhost
        ServerName webdev.MYDOMAIN.com
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
```[SIZE=4]This is the dms vhost file[/SIZE]
```
<VirtualHost dms.MYDOMAIN.com:80>
        ServerAdmin ktdms_admin@MYDOMAIN.com
        ServerName dms.MYDOMAIN.com
        ServerAlias dms.MYDOMAIN.com
        DocumentRoot /var/www/ktdms

        <Directory /var/www/ktdms/>
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

        ErrorLog /var/log/apache2/ktdms.error.log

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
```I'm really not sure whats going on. I'm not sure if NameVirtualHost is needed everytime a vhost is created? I

---

### Post by compunuts on 2006-09-23
> 
NameVirtualHost webdev.MYDOMAIN.com
<VirtualHost webdev.MYDOMAIN.com>
        ServerAdmin webmaster@localhost
        ServerName webdev.MYDOMAIN.com

This setting is wrong. It should be something like
```

NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName webdev.MYDOMAIN.com

```

And then;
```

NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName dms.MYDOMAIN.com

```

If you need basic setup. check it out [here](http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux).

---

### Post by compunuts on 2006-09-23
And also your dir structure should be

```

/var/www/webdev
               /index.html
        /dms
            /index.html

```

And in /etc/apache2/sites-available
```

/etc/apache2/sites-available/webdev
                            /dms

```

and use a2ensite <your-site-name> to enable sites. The above link I gave you also explain this in a little more details.

HTH ..

---

### Post by MystaMax on 2006-09-24
Compunuts, Thanks for taking the time to look @ this.

After making the changes, when i restart apache (sudo apache2ctl graceful) Apache reports errors:

```

[Fri Sep 22 16:13:29 2006] [warn] module php4_module is already loaded, skipping
[Fri Sep 22 16:13:29 2006] [warn] NameVirtualHost *:80 has no VirtualHosts

```

I'm concerned what the second, *NameVirtualHost *:80 has no VirtualHosts*.  Since this is @ the beginning of both files, I can't tell which is reporting an error. I don't even know what the error means. Can someone explain that error? It seems so simple, but I can't grasp the idea behind it. Thanks.

---

