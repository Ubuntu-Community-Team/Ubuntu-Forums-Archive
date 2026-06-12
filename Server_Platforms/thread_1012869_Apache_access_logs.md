---
title: "Apache access logs"
date: 2008-12-16
forum: Server Platforms
---

### Post by habl on 2008-12-16
Hi,

I have a problem on Ubuntu 8.04 Server with apache. It almost log nothing to /var/log/apache2/access.log. The only thing it logs is:

```

127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"
127.0.0.1 - - [16/Dec/2008:15:48:25 +0100] "OPTIONS * HTTP/1.0" 200 - "-" "Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch (internal dummy connection)"

```

And a lot more identical lines. 

/etc/apache2/sites-enabled/000-default says:

```

NameVirtualHost 192.168.1.8:80
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/ >
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

```

Changed the file attributes to chmod 777. Restarted the apache server a couple of times. The The error logs are working fine. I can't seem to find what causes the problem. Anybody with some advice?

---

### Post by asommer on 2008-12-16
What are the permissions of you /var/log/apache2 directory?  Mine are:

>  drwxr-x--- 2 root   adm     4096 2008-12-17 04:28 apache2

---

### Post by habl on 2008-12-17
Tnx for your reply, the permissions are exactly the same here:

```

drwxr-x--- 2 root   adm    4096 2008-12-16 16:17 apache2

```

I don't think the file permissions are the problem anyway because the file isn't completely empty. It is writing something to it, but no web connections.

---

### Post by habl on 2008-12-18
Anyone else?

---

### Post by sdnelson on 2008-12-18
Try changing your <VirtualHost *> to <VirtualHost "your hosts ip address"> and see if that works. All of your 127.0.0.1 traffic is working fine. What you want to see is all of the traffic on your host ip address. Or try add this in between your NameVirtualHost and  <VirtualHost *> entry:

CustomLog /var/log/apache2/YourSite.log combined

If that doesn't work, create a new file called 001-vhosts and add an entry like this:

<VirtualHost 192.168.1.4:80>
    ServerName "your host name"
    ServerAlias "your host aliases"
    CustomLog /var/log/apache2/yourlog.log common
    <Directory />
        Options None +FollowSymLinks
        AllowOverride None
        Order allow,deny
        Allow from all
    </Directory>
    DocumentRoot /var/www/hosts/yourwebpages
</VirtualHost>

 Restart Apache..

---

### Post by habl on 2008-12-18
Tnx m8!


Adding "CustomLog /var/log/apache2/YourSite.log combined" before the virtualhost block did the trick :)

---

