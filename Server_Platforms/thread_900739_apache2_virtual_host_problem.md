---
title: "apache2 virtual host problem"
date: 2008-08-25
forum: Server Platforms
---

### Post by eamonnf on 2008-08-25
I have three hosts.  

host 1
```
NameVirtualHost a.bar.co.uk
<VirtualHost a.bar.co.uk>
        ServerAdmin webmaster@localhost
        ServerAlias a

        DocumentRoot /var/www/
        <Directory /var/www/>
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
        LogLevel warn
        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

</VirtualHost>

```

host2
```
NameVirtualHost b.bar.co.uk
<VirtualHost b.bar.co.uk>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/lib/mediawiki
        <Directory /var/lib/mediawiki/>
                Options +FollowSymLinks
                AllowOverride All
                order allow,deny
                allow from all
        </Directory>

        <Directory /var/lib/mediawiki/config>
                Options -FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /var/lib/mediawiki/upload>
                Options -FollowSymLinks
                AllowOverride None
        </Directory>

        ErrorLog /var/log/apache2/error.log

        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

</VirtualHost>

```

host3
```
NameVirtualHost www.foo.co.uk
<VirtualHost www.foo.co.uk>
        ServerAlias foo.co.uk
        ServerAdmin eamonn@c.co.uk

        DocumentRoot /home/services/sites/foo.co.uk/www/

        <Directory /home/services/sites/foo.co.uk/www/ >
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /home/services/sites/foo.co.uk/logs/error.log
        CustomLog /home/services/sites/foo.co.uk/logs/access.log combined
        LogLevel warn
        ServerSignature On

</VirtualHost>

```

When i restart apache i get  [warn] NameVirtualHost bar.co.uk:0 has no VirtualHosts

When i go to bar.co.uk it serves files from the host foo.co.uk and writes to foo.co.uk's logs.

any ideas what i am doing wrong? I have all of these in my /etc/hosts file.

---

### Post by mbeach on 2008-08-25
I've never named my virtual hosts like that, but I'll look into that.

Normally I'd do:
```

       <VirtualHost *>
           ServerName www.foo.co.uk

```

I don't see any ServerName Directives in your virtual host files.  Add them and see if it makes a difference.

---

### Post by eamonnf on 2008-08-26
that worked a treat.  i changed the conf to read VirtualHost * and added the servername.  i think it was the server name that did it though.

I am used to having the NameVirtualHost declared for ips so i can change it quickly if i split the sites out onto multiple boxes but it isnt really needed here.

cheers mate!!

---

