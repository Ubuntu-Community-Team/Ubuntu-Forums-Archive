---
title: "Apache-redirect http to https"
date: 2013-05-07
forum: Server Platforms
---

### Post by atm123 on 2013-05-07
hi,
   i have apache2 running.  and i wanted to enable https and redirect all http traffic to https completely.i have pasted my default file config below.
now https seems to be working fine. but http also works. can anyone help me block/redirect it. thanks a lot.

<VirtualHost *.80>
       RewriteEngine on
       RewriteCond %{SERVER_PORT} !^443$
       RewriteRule ^/(.*) https://%{HTTP_HOST}/$1 [NC,R,L]
</VirtualHost>


<VirtualHost *:443>
        ServerAdmin webmaster@localhost
        ServerName  192.168.10.28:443


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


        ErrorLog ${APACHE_LOG_DIR}/error.log


        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn


        CustomLog ${APACHE_LOG_DIR}/access.log combined


    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.crt
        SSLCertificateKeyFile /etc/apache2/ssl/apache.key
</VirtualHost>

---

### Post by SeijiSensei on 2013-05-07
Don't use rewrites; use a simple redirect instead.

```

<VirtualHost *:80>
ServerName  www.example.com
Redirect / https://secure.example.com/
</VirtualHost>

```

---

### Post by atm123 on 2013-05-08
thanks for the quick reply. i did the above what you said. now the site is only accessible via https. but the subfolders like in the path - //192.168.10.28/subfolder/subfolder are still using both http and https. is there a way to redirect all these to https? please help.

---

### Post by SeijiSensei on 2013-05-08
Do you have a VirtualHost definition for port 80 that points to those directories?  

Essentially there should be no other references to port 80 other than the one that leads to the Redirect.  You should have one VirtualHost definition for port 80 that redirects, and one for port 443 that provides the actual content via HTTPS.

---

### Post by atm123 on 2013-05-11
thanks. let me check and get back soon.

---

