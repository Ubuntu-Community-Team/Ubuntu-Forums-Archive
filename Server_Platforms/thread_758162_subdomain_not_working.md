---
title: "subdomain not working"
date: 2008-04-17
forum: Server Platforms
---

### Post by cocotu on 2008-04-17
we are trying to set up a subdomain: uandi.megatron in out local LAN. It was working for a moment, but now it redirects to megatron.  Is this a DNS issue, do I need to point the subdomain to a different IP? any suggestions? thanks

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
                AllowOverride All
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

<VirtualHost *>
        DocumentRoot "/var/www/uandi/"
        ServerName uandi.megatron
        ErrorLog /var/log/apache2/uandi.log

        <Directory /var/www/uandi/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

---

### Post by AlphaWu on 2008-04-18
You need change DNS point uandi.megatron to the server's IP.

---

### Post by cocotu on 2008-04-18
there is an entry at the DNS server:
uandi.megatron             172.27.0.57
megatron                       172.27.0.57

they're both in the same server.  Everytime I go to [http://uandi.megatron](http://uandi.megatron) it takes me to [http://megatron](http://megatron).  How do you tell apache or the DNS server these are two different pages? thanks.

---

### Post by cocotu on 2008-04-18
I now in IIS you assign a different IP to the different websites.  How do you do this in apache? thanks

---

### Post by Oldsoldier2003 on 2008-04-18
Separate the sites, i.e. make a separate conf for the second site and then use a2ensite <site_conf> to enable the second site. make sure you have the servername tag on both sites. then restart apache.

---

### Post by cocotu on 2008-04-18
thanks Old, Following this link: [http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/](http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/)
gave me the answer.  We should have a HOW-TO (for Ubuntu users) here at the forums or somewhere else. Or do we have that? thanks

---

### Post by MJN on 2008-04-18
What was the problem in the end?

Mathew

---

