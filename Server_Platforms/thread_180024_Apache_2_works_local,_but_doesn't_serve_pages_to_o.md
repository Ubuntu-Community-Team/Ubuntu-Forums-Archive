---
title: "Apache 2 works local, but doesn't serve pages to other machines"
date: 2006-05-21
forum: Server Platforms
---

### Post by businger on 2006-05-21
Hi everybody,

I just recently switched from debian to ubuntu (5.1) and installed apache2 with php5 ssl etc. via Synaptic. I copied my "old" apache2 configuration-files from my debian machine to the ubuntu machine and fine-tuned the config to match the new environment.

After restarting apache (and even rebooting) I get the following strange behavioure.

from apache serves all my pages localy when I enter localhost or 127.0.0.1 or 192.168.0.3 or even myserver.mydomain as url, without any problems or errors.

whenever I try to access one of these pages from an other machine, i only get a file-not-found error message and apache logs 
"[Sun May 21 12:44:39 2006] [error] [client 192.168.0.10] File does not exist: /htdocs" in the /var/log/apache2/error.log

the error message shown in the remote browser is a different one than the 404-page shown when I try to get a non-existing page from localhost.

has anyone got an idea what the problem could be? Thanx a lot for any help!!

Dominik

PS here's one of my VHost config files. the other are pretty much the same.

```
NameVirtualHost bender
<VirtualHost bender>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/bender
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/bender/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from 192.168.0
                allow from 127.0.0.1
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

    Alias /phpMyAdmin /var/www/phpMyAdmin/
    <Directory "/var/www/phpMyAdmin/">
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from 192.168.0
            allow from 127.0.0.1
    </Directory>
</VirtualHost>
```

---

### Post by cilynx on 2006-05-21
Sounds like a DNS error to me.  Are you absolutely positive that you're pointing at the same machine from inside and outside?  What's the server string on the two different 404 pages?

Just so you know what you're looking for, mine is:  
Apache/2.0.55 (Debian) PHP/4.4.2-1+b1

---

### Post by businger on 2006-05-21
hi, 

I'm 100% sure that it is the same machine. If I create a symlink "/htdocs" which points to some directory, the content of that directory get's shown for request from outside. from inside my normal home page is still being shown. => def. the same machine.

the local 404-page shows:
```

Not Found

The requested URL /no-such-file was not found on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.2 mod_ssl/2.0.54 
OpenSSL/0.9.7g Server at bender Port 80

```

the remote browser shows for the same url:

```

Not Found

The requested URL /no-such-file was not found on this server.

```

I'm completly lost!

---

### Post by businger on 2006-05-24
hi all,

I was just able to solve my problem. Apparently it was no "file-not-found" or "access-denied" problem, but an error in my vhost configuration.

on [http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html) I found the error.

my vhost configurations all had the same config
```

NameVirtualHost bender
<VirtualHost bender>
ServerName bender
...
</VirtualHost>
<VirtualHost other>
ServerName other
...
</VirtualHost>"

instead of

"NameVirtualHost *
<VirtualHost *>
ServerName bender
...
</VirtualHost>
<VirtualHost *>
ServerName other
...
</VirtualHost>
....

```
hope this helps anyone having the same problem.

cheers, dominik

---

