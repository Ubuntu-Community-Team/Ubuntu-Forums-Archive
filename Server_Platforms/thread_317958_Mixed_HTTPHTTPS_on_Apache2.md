---
title: "Mixed HTTP/HTTPS on Apache2"
date: 2006-12-13
forum: Server Platforms
---

### Post by dlouwers on 2006-12-13
Hi,

I have recently installed the last LTS Server release including Apache2 and SSL_MOD. When following the server guide pdf in setting up SSL on my system I can no longer access the documents served from /var/www/ using plain http. I want my whole site to be accessible using https AND http. Is this possible and what should I change to make this work, considering I exactly followed the directives in the documentation?

Regards,

Dirk Louwers

---

### Post by MJN on 2006-12-13
It is indeed possible. Trivially so in fact.
 
If you post your config (that from /etc/apache2/sites-available/ - others can come later if required) we'll be able to see where you've slipped up.
 
Mathew

---

### Post by dlouwers on 2006-12-13
First of all, thank you for the quick reply. The contents of the configuration file requested are:

```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin xxxx@xxxx.com

        DocumentRoot /var/www
        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
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

```

Thanks in advance,

Dirk Louwers

---

### Post by MJN on 2006-12-14
Sorry for the slow follow-up....
 
Your best bet would be to split (copy) your current config into two sections, one for http (on port 80) and the other for https (on port 443).
 
Hence you would have:
 
```

<VirtualHost ***:443**>
        ServerAdmin xxxx@xxxx.com
 
        DocumentRoot /var/www
        SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire
        SSLCertificateFile /etc/ssl/certs/server.crt
        SSLCertificateKeyFile /etc/ssl/private/server.key
        <Directory />
                Options FollowSymLinks
*..etc etc*
</VirtualHost>
 
<VirtualHost ***:80**>
        ServerAdmin xxxx@xxxx.com
 
        DocumentRoot /var/www
*Remove the SSL lines but keep everything else...* 
       <Directory />
                Options FollowSymLinks
*..etc etc*
</VirtualHost>

```
 
This isn't the only way to skin the cat, however it's the simplest IMHO (you could have just the one container and manipulate the server behaviour in response to how the client has connected however it's not worth the hassle here).
 
Now you have two seperate containers, each delivering the same content but one on port 80 (in the clear) and the other over port 443 (with SSL). Note that you may also need to ensure that your /etc/apache2/ports.conf file has both Listen 80 and Listen 443 in it (I don't know what your HowTo said to do there).
 
I must ask why it is you want to do this though? It is quite unusual to allow connectivity both in the clear and encrypted - if you require the latter then it's more normal to forbid the former....
 
Mathew

---

### Post by dlouwers on 2006-12-14
> I must ask why it is you want to do this though? It is quite unusual to allow connectivity both in the clear and encrypted - if you require the latter then it's more normal to forbid the former....

The reason is that I am going to run a web application that I want to be able to connect to over https when I want to do administrative tasks, but is also going to stream audio files. Apparently this streaming doesn't work (nor seems desirable) over https so I have to have an option to access the site's content over plain http.

It would probably be more correct to only allow the use of plain http for certain mime types but allowing http site wide is second best.

Regards,

Dirk Louwers

---

### Post by MJN on 2006-12-14
Okay, I see. Sounds reasonable.
 
You could even tighten things up by having a ReWrite rule in the :80 container that redirects the browser to the 'restricted' parts of the site over SSL/443.
 
But if the admin side of things will be done by you (and not just anyone) then there's arguably little need for such enforcement.
 
Mathew

---

### Post by theonlyandy on 2006-12-14
Greetings.

We got the same problem at the moment.

It seems your solution with the *:443 and *:80 is not allowed anymore in Apache:

```
[Thu Dec 14 18:11:30 2006] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Thu Dec 14 18:11:30 2006] [error] VirtualHost *:443 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

```

Or did I do anything wrong there?
Which other possibilities are there?

Thanks for your answers in advance.

---

### Post by MJN on 2006-12-14
And what's your config? Do you have a **ServerName  **directive defined? Try putting one in with the port 80 config (e.g. **ServerName [www.name.of.your.server](www.name.of.your.server)**) , and change the **<VirtualHost *:443>** line to [B]<VirtualHost _default_:443>

[/B] Mathew

---

