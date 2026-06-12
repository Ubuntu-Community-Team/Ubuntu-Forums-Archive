---
title: "Virtual Host Problem"
date: 2011-03-13
forum: Server Platforms
---

### Post by EpicKris on 2011-03-13
This is what I'm attempting to achieve:
example.com > site
www.example.com > site

I've created the site as a virtual host:
/etc/apache2/sites-available/example
```
<VirtualHost *:80>
        ServerAdmin me@example.com
        ServerName example.com
        ServerAlias *.example.org.uk
        DocumentRoot /home/me/Sites/example/www
        <Directory /home/me/Sites/example/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>
```

Visitting the sites shows:
http://example.com/ > Server page
http://www.example.com/ > Example page

Any suggestions please?

---

### Post by volkswagner on 2011-03-13
Aliases can be a space separated list.

*.example.org.uk will not accept [www.example.com](www.example.com) requests.

You line should be something like

```
ServerAlias *.example.org.uk *.example.com *.example.org *.example.uk

```

I have never used the wild card "*", but I'm guessing it should work.

I usually just list out the actual subdomains, since I may need additional subdomains for other sites.

like
```
ServerAlias www.example.org.uk www.example.com 
```

---

### Post by EpicKris on 2011-03-13
It worked! Thanks!

---

