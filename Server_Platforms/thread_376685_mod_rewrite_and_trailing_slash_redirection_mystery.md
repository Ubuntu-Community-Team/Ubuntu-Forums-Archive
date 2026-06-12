---
title: "mod_rewrite and trailing slash redirection mystery"
date: 2007-03-05
forum: Server Platforms
---

### Post by depi on 2007-03-05
Hi guys,
I have the following mod_rewrite rules in my .htaccess:
```

RewriteEngine On

#check if file or directory real exists:
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d

#do the rule only if the address has no extension:
RewriteCond %{REQUEST_URI} !\.[[:alnum:]]+$
#replace /whatever to /whatever/, not apply to whatever/!
RewriteRule ^(.+[^/])$ /$1/ [R=301]

#do the rule only if the address ends with trailing slash:
RewriteCond %{REQUEST_URI} ^.*/$
#if the rule ends with trailing slash then redirect to index.php..
RewriteRule ^(.*)/$ /index.php?p=$1 [L]


```

When I wan to access mysite.com/admin/style - it should redirect it to mysite.com/admin/style/, but it rathers open the style.css (no redirection). I wonder how it can guess that I have there a style.css, if I write only style in the URL.
I tried this on my hosting - there it worked as I wanted - it did the redirection well.

So now I don't know what I'm doing bad. I have created a virtual server on my Ubuntu machine, here is the /etc/apache/sites-avaliable/fanklub.desmod file:
```

<VirtualHost *>
        ServerAdmin webmaster@localhost

        ServerName fanklub.desmod
        DocumentRoot /home/depi/www/fanklub.desmod.sk
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/depi/www/fanklub.desmod.sk>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
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

</VirtualHost>

```

And /etc/hosts:
```
127.0.0.1 localhost fanklub.desmod
```

Is there something wrong with it? I'm accessing the pages through [http://fanklub.desmod](http://fanklub.desmod)

---

### Post by deuce868 on 2007-03-05
there's a feature of apache that I can't think of the name of right now that will try to guess what you're trying to open. So since you typed style, and there's a style.css file in there it does a best guess and gives you that. Try to go through the main config files, not your virtual host, and see if you can turn it off.

---

