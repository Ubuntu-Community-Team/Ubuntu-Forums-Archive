---
title: "another virtual hosting apache2 troubled guy"
date: 2005-12-14
forum: Server Platforms
---

### Post by nephish on 2005-12-14
lo there !

i have been trying for hours, a dozen forum threads, and still cannot get virtual hosting to work on apache 2

i created two files in the apache2/sites-avalable directory ( got rid of the default )
 they look like this 
```

<VirtualHost *>
        ServerAdmin nephish@xit.net
        ServerName www.mysite.com
        ServerAlias mysite.com
        DocumentRoot /var/www/mysite/web_root/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/mysite/web_root>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /var/www/mysite/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        LogLevel warn

        ErrorLog /var/www/mysite/web_root/othersite-error_log
        CustomLog /var/www/mysite/web_root/othersite-access_log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
```

i did the a2ensite mysite and it seems to have worked.

but when i tried to add another one (much simpler , i used the default as a template for the above 

like this 
```

<VirtualHost *>
        ServerAdmin nephish@xit.net
        ServerName www.othersite.com
        ServerAlias othersite.com
        DocumentRoot /var/www/othersite/web_root/

        ScriptAlias /cgi-bin/ /var/www/othersite/cgi-bin/

        ErrorLog /var/www/othersite/web_root/othersite-error_log
        CustomLog /var/www/othersite/web_root/othersite-access_log combined

</VirtualHost>

```

when i did the a2ensite it again created a symlink, and when i restarter apache2 again it seemed ok (no errors)

but when i go to either site in a browser, it takes me to the first site that i did.

i am using name based virtual hosting and zoneedit does the dns.

any idea where to start ?

oh, by the  way, is the http.conf file in /etc/apache/ even looked at ? why do we need apache and apache2 ?

ok, thanks for any help

---

