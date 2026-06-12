---
title: "Apache VirtualHost problem"
date: 2008-11-08
forum: Server Platforms
---

### Post by Visko on 2008-11-08
Yesterday I have upgraded to intrepid, and I switched the apache configuration files to the new ones, and now I can't access my virtualhosts. 

When I start apache I get the following warning:

```

[warn] NameVirtualHost *:80 has no VirtualHosts

```

Directives in ports.conf:
```

Listen 80
NameVirtualHost *:80

```

Directives in httpd.conf:
```

ServerName 192.168.1.99

```

Directives in /sites-enabled/000-default:
```

<VirtualHost *>
    DocumentRoot /srv/www
    ServerName public.pandora.local
    <Directory /srv/www>
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>

<VirtualHost *>
    DocumentRoot /srv/dota/htdocs
    ServerName dota.pandora.local
    <Directory /srv/dota/htdocs>
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>


```

Whenever I try to access the pages I always get the default virtualhost (the first one defined, /srv/www). 

I have my hosts file setup as:
```

192.168.1.99	dota.pandora.local
192.168.1.99	public.pandora.local

```

Any ideas?

---

### Post by mbeach on 2008-11-08
create another file /etc/apache2/sites-available/pandora-dota
[name it whatever you like instead of 'pandora-dota']

cut from 000-default to pandora-dota:
```

<VirtualHost *>
    DocumentRoot /srv/dota/htdocs
    ServerName dota.pandora.local
    <Directory /srv/dota/htdocs>
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>

```

then run ```
sudo a2ensite pandora-dota
sudo /etc/init.d/apache2 reload
```

I'm not sure if its actually necessary to have the separate files per virtual host, but its what works for me.

I'd also recommend dropping the ServerName directive in httpd.conf (I think that file should really be empty and is there for backwards compatibility only)

---

### Post by Visko on 2008-11-09
I figured it out, I had "NameVirtualHost *:80" in my ports.conf,
but I had "VirtualHost *" in my virtual host blocks, and that was why it couldn't find any matching virtualhosts.

Thanks for the reply.

---

