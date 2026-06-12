---
title: "Second domain loading wrong path?"
date: 2012-07-15
forum: Server Platforms
---

### Post by LiftedTurbo on 2012-07-15
So, I was finally able to setup my first domain on my apache2/bind9 Ubuntu server. Now, when I tried setting up a second one it keeps loading the first domain's site.

Both have completely separate directory paths.

First domain: /var/thefirstdomain.com
Second domain: /home/second/public_html

> <VirtualHost *:80>
        ServerAdmin [email]myemail@myemail.com[/email]
        ServerName Houston

        DocumentRoot /home/second/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /home/second/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride All
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
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by SeijiSensei on 2012-07-15
Read these:

[http://ubuntuforums.org/showthread.php?p=11922324#post11922324](http://ubuntuforums.org/showthread.php?p=11922324#post11922324)

[https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html)

[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

---

### Post by LiftedTurbo on 2012-07-15
I updated the server name to be unique for both, I forgot to symlink the sites-enabled file so I removed the old one and did the symlink. Ran the command to enable the site, no errors. Then restarted Apache, domain is still loading the first site though when visiting the second one.

---

### Post by SeijiSensei on 2012-07-15
Are you sure the server name in the URL *exactly* matches the ServerName in the virtualhost definition?  You might need a couple of ServerAlias entries.

---

### Post by LiftedTurbo on 2012-07-15
Servername in the URL? how would I check that?

---

### Post by LiftedTurbo on 2012-07-17
Anyone? After searching a lot I have still been unable to resolve this issue.

---

### Post by volkswagner on 2012-07-17
> **LiftedTurbo said:**
> Servername in the URL? how would I check that?

As in [http://Houston](http://Houston) notice the capital 'H' as this is the only ServerName listed with no alias.

I sounds like NamVirtualHosts is not working/enabled.

Do you have the following in /etc/apache2/ports.conf?
```
NameVirtualHost *:80
```

The above will enable name based virtual hosts.  If you make the above edit, you'll need to restart Apache2 and clear the browser cache on the machine you are testing from.

---

### Post by LiftedTurbo on 2012-07-17
> 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

I have just been putting random server names, not sure what needs to go there if that's the case.

As for the ports.conf I sure do have that line in there already.

---

### Post by LiftedTurbo on 2012-07-18
Sorry for the bump, still no resolution. :/

---

### Post by sandyd on 2012-07-18
Try this
```

ServerName houston.local

```

```

sudo nano /etc/hosts

```
add this on a new line on the bottom
```

#Local site aliases.
127.0.0.1 houston.local

```

[http://houston.local](http://houston.local)

---

### Post by LiftedTurbo on 2012-07-19
No luck, :/

I did
127.0.0.1 mydomain1.com

127.0.0.1 mydomain2.com

---

### Post by LiftedTurbo on 2012-07-19
Also, it appears that I'm missing an A record for both of the domains. www. works but without it it will not load.

---

### Post by LiftedTurbo on 2012-07-20
The big bump.

---

