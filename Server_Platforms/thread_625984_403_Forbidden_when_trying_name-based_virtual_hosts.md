---
title: "403 Forbidden when trying name-based virtual hosts"
date: 2007-11-28
forum: Server Platforms
---

### Post by whitethunder922 on 2007-11-28
I am trying to run several name-based virtual hosts on apache2, v2.2.6, on Gutsy Gibbon. I keep getting a 403 Forbidden when I try to visit one of my hosts. What could be keeping me out? Permissions/owner of /var/www/newdomain are apache:apache and 755. If I access the site with [www.mydomain.com/newdomain](www.mydomain.com/newdomain) it loads just fine. Any ideas? Here are my configurations:

In apache2.conf (with a bunch of other mostly default stuff):
User apache
Group apache

In /etc/apache2/sites-available/default:
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

In /etc/apache2/sites-available/newdomain:
<VirtualHost *>
        ServerName newdomain.mydomain.com
        DocumentRoot /var/www/newdomainl
        ErrorLog /var/log/apache2/newdomainl-error.log
</VirtualHost>

---

### Post by MJN on 2007-11-28
What does the error log say?

It could be that you need a <Directory /var/www/newdomain> container inside your newdomain virtual host container - the 'parent' <Directory /var/www> section does not cover it given it is inside a different virtual host.

Mathew

---

### Post by whitethunder922 on 2007-11-29
That did it! Thanks!

---

### Post by rybaxs on 2008-05-07
I've got a problem fixing my virtual host/server at var/www/
everything on it is 403 Forbidden error even when I change chmod 777. 

Before the error occured, I've followed tutorials on this site
[http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/](http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/)

need help please.. my boss will kill me.

---

