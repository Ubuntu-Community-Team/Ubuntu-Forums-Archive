---
title: "Apache redirect oddity"
date: 2010-08-30
forum: Server Platforms
---

### Post by bg11 on 2010-08-30
I'm running an Apache/2.2.16 test server and am having trouble redirecting, eg example.com/hello.php to [www.example.com/hello.php](www.example.com/hello.php).

I created a .htaccess file and placed it in /var/www.  When it contained the directive **RewriteRule ^/(.*) http://www.example.com/$1** and the condition RewriteCond %{HTTP_HOST} !^www\.example\.com, as recommended by the apache wiki, I got no redirection at all.

Now, if I set the directive to **RewriteRule ^(.*) http://www.example.com/$1**, then firefox redirects me to [http://www.example.com/example.com/cgi/hello.php](http://www.example.com/example.com/cgi/hello.php).
It's as if it confuses $1 with %1/$1.  I can't find much help on this particular oddity using google.

Here is my apache config under /etc/apache2/sites-enabled/example.com:

```

<VirtualHost *:80>
  DocumentRoot "/var/www/example.com"
  ServerName www.example.com
  ServerAlias example.com

  <Directory /var/www/example.com>
    AllowOverride All
    Order Deny,Allow
    Allow from all
  </Directory>

</VirtualHost>

```

and here is my .htaccess file:

```

Options +FollowSymLinks
RewriteEngine on
RewriteCond %{HTTP_HOST}   !^www\.example\.com [NC]
RewriteCond %{HTTP_HOST}   !=""
RewriteRule ^(.*)         http://www.example.com/$1 [L,R=301]

```

---

### Post by arrrghhh on 2010-08-30
I thought your hosting provider had to do this for you...  I could be wrong tho.

---

### Post by bg11 on 2010-08-30
> **arrrghhh said:**
> I thought your hosting provider had to do this for you...  I could be wrong tho.

It's a test server that I'm running.  Like a sandbox, or a training ground.

---

