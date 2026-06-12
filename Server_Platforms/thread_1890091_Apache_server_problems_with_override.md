---
title: "Apache server problems with override"
date: 2011-12-02
forum: Server Platforms
---

### Post by Kadorrna on 2011-12-02
Hi,

I am new with server administration, I work with php but always in localhost and when I have to deploy, somebody else was in charge of it. So this is my real first time with all this.

I have my server in rackspace, I have installed ubuntu 11.04 and now I put a web page just for trying all this new world.

The page files are located at /var/www
I have just an html, css and gif.

Now My problem is that when I go to the site I can reach to it even through:
[www.cocreativa.com.ar](www.cocreativa.com.ar) AND cocreativa.com.ar (Google doesn't like this)

I have done an .htacces at /var/www to redirect cocreativa.com.ar to [www.cocreativa.com.ar](www.cocreativa.com.ar)
```

RewriteEngine On
RewriteCond %{HTTP_HOST} !^www\.
RewriteRule ^(.*)$ http://www.%{HTTP_HOST}/$1 [R=301,L]

```

After this I went to /etc/apache2/sites-availables and edit default file:
```

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

```

after this I tried apache restart and apache reload, but still doesn't redirects

what I am Missing?

Thanks in advance.

---

