---
title: "How to change the path of my index.html website?"
date: 2006-08-07
forum: Server Platforms
---

### Post by cocotu on 2006-08-07
Hi friends, I installed a LAMP server here at work the other day. I'm using Ubuntu. I just installed a CMS and everything is running fine. The question is how do I tell Apache not to look for the index.html /var/www and to look for it in this path: 

10.0.3.107/Jupiter1.1.5/index.php

As you can see I installed the Jupiter CMS here at work, we wanted something like this for posting messages in our Intranet.
I'm very new to Apache, and Apache to me.

Thanks for the help....

---

### Post by chrisfay on 2006-08-07
If you have a domaine name, just create a virtual host in sites-available and make /var/www/Jupiter1.1.5 the default root. Put this in your "sites-enabled/000-deafult" config file:

<VirtualHost *>
DocumentRoot "/var/www/Jupiter1.1.5"
ServerName "yourdomainname.tld"
ServerAlias "www.domainname.tld"
<Directory "/var/www/Jupiter1.1.5">
allow from all
</Directory>
</VirtualHost>

Anyone who types in your domain name will be routed to /var/www/Jupiter1.1.5. You can set index.php as the default instead of index.html in apache2.conf. Or just make sure there is no "index.html" file in the folder and it will default to .php if its listed.

---

### Post by cocotu on 2006-08-08
chrisfay I did those changes, but I still don't get anything. This is my 000-default looks like:

NameVirtualHost *
<VirtualHost *>
        ServerAdmin 

        DocumentRoot /var/www/Jupiter1.1.5
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

<VirtualHost*>
DocumentRoot "/var/www/Jupiter1.1.5"
ServerName "10.0.3.107"
ServerAlias "10.0.3.107"
<Directory "/var/www/Jupiter1.1.5">
allow from all
</Directory>

</VirtualHost>

Do I have to restart Apache? If yes, what is the command for that?
Thanks...

---

### Post by compunuts on 2006-08-08
sudo apache2ctl restart

---

### Post by cocotu on 2006-08-08
I did that and I get this: 

Syntax error on line 55 of /etc/apache2/sites-entabled/000-default:
Expected </VirtualHost*> but saw </VirtualHost>

What is this??

Thanks....

---

### Post by hogman23 on 2006-08-08
Here you go, try this:

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

