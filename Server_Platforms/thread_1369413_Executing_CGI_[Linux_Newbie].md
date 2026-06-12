---
title: "Executing CGI [Linux Newbie]"
date: 2009-12-31
forum: Server Platforms
---

### Post by Skidbladniir on 2009-12-31
I'm an EXTREME newbie to Ubuntu.  How would I make my server execute PHP and Perl scripts?  (I'm going to be working with both)

I have PHP5 and the latest Perl installed, and my installation is fresh.

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options +ExecCGI FollowSymLinks MultiViews
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
                                                              12,3-17       All

```

---

### Post by Skidbladniir on 2010-01-01
Nevermind!

Figured it out.

---

