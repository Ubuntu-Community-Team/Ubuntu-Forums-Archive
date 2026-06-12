---
title: "Domains And Subdomains"
date: 2009-11-23
forum: Server Platforms
---

### Post by LaicaNuru on 2009-11-23
Hello

I started a local server to my personal website, with Ubuntu 8.4 Server. I tried to properly configure the Apache2 server, but apparently I made a mistake ...

In the sites-available directory, I have three files, domain.org, otherdomain.org subdomain.domain.org and, with the following configuration:

domain.org
```

NameVirtualHost domain.org
<VirtualHost domain.org>
        DocumentRoot /var/www/
        ServerAdmin admin@domain.org
        ServerAlias www.domain.org

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
        ...
</VirtualHost>

```
subdomain.domain.org
```

<VirtualHost subdomain.domain.org>
        DocumentRoot /home/user/web
        ServerAdmin admin@domain.org

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /home/user/web/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        ...

```
otherdomain.org
```

<VirtualHost otherdomain.org>
        DocumentRoot /home/user/web
        ServerAdmin admin@domain.org
        servername otherdomain.org
        ServerAlias www.otherdomain.org

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /home/user/web/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        ...

```
In resume, tried to get that my domain points to the root server and a subdomain, and another domain, points to a folder in the user directory. But as a result, visiting it from local network by any of the three directions, the server always point to the user folder, never to my root directory.

can someone help me with this?

---

### Post by cdenley on 2009-11-23
1. You shouldn't use domains in VirtualHost tags. You only need domains for ServerName and ServerAlias.
```

NameVirtualHost *:80
<VirtualHost *:80>

```

2. subdomain.domain.org has no ServerName defined, so it will never be used.

3. You should have a default site named "default". Without a default site, the first one alphabetically is used as default. If there is no site defined (ServerName or ServerAlias) for a requested domain, the default is used.

---

### Post by LaicaNuru on 2009-11-23
Hi!

Thank you for responding so quickly. I change what you say and I already work perfectly, at least from within the local network. Tonight I will try from external network.

Thank you very much

---

