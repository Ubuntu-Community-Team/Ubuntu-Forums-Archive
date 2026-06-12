---
title: "apache with multiple sites"
date: 2011-11-01
forum: Server Platforms
---

### Post by ZenMasta on 2011-11-01
I'm a little confused about setting up a server with multiple sites. 

I have a default site configured
/etc/apache2/sites-available/default
```
<VirtualHost myip:80>
        ServerName genericdomain.com
        ServerAdmin webmaster@localhost
 
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
```  

I also have a 2nd site setup and here is that file
/etc/apache2/sites-available/mytestsite
```
<VirtualHost myip:80>
ServerAdmin webmaster@adomain.com
ServerName test.mydomain.com
DocumentRoot /home/robbieb/html/
ErrorLog /home/robbieb/logs/error.log
CustomLog /home/robbieb/logs/access.log combined
</VirtualHost>
```

I wanted to create a 3rd site so I basically copied the 2nd site and simply changed the directory.
/etc/apache2/sites-available/newtestsite
```
<VirtualHost myip:80>
ServerAdmin webmaster@adomain.com
ServerName test.myotherdomain.com
DocumentRoot /home/robbieb2/html/
ErrorLog /home/robbieb2/logs/error.log
CustomLog /home/robbieb2/logs/access.log combined
</VirtualHost>
```


After I enabled the site and attempted to reload apache I got a warning
a2ensite newtestsite

/etc/init.d/apache2 reload
 * Reloading web server config apache2                                          [Tue Nov 01 13:13:59 2011] [warn] VirtualHost myip:80 overlaps with VirtualHost myip:80, the first has precedence, perhaps you need a NameVirtualHost directive
[Tue Nov 01 13:13:59 2011] [warn] NameVirtualHost 205.186.134.223:80 has no VirtualHosts


I'm not even sure where the 205 ip comes from as its not in my default or other config files.

Also, the default and the original test site both work side by side without any problems even though they have the same ip (just different domains). So now I don't understand why I get this warning about overlapping IP when I created the 3rd site.

Thanks.

---

### Post by Wej on 2011-11-01
Try adding this above your <VirtualHost> opening tags in each file:
```

NameVirtualHost yourip:80
```
[http://httpd.apache.org/docs/2.0/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/2.0/mod/core.html#namevirtualhost)
*The NameVirtualHost directive is a required directive if you want to configure name-based virtual hosts.*

---

### Post by ZenMasta on 2011-11-01
Thank you :)

---

### Post by ZenMasta on 2011-11-03
Well, I attempted to add a 4th site. reloaded apache etc. Except when I try to visit the domain (dns already updated) it shows the files of the 3rd site. 

I checked the config file and the paths are infact changed, so not sure what's going on here.

---

### Post by vasile002 on 2011-11-04
Ensure that the ServerName and ServerAlias directives are correct and that the site is pointed to the correct IP address the VirtualHost is assigned to.

---

