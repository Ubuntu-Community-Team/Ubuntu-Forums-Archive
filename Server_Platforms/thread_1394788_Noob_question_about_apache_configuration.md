---
title: "Noob question about apache configuration"
date: 2010-01-31
forum: Server Platforms
---

### Post by undecim on 2010-01-31
I need to make an apache location point to a file location (i.e. [http://hostname/foo](http://hostname/foo) needs to serve pages from /var/bar). I've tried doing this with symlinks, but always get a 403.

I know there is some way to do this with httpd.conf, but I don't remember how, and can't find it in the docs. If someone would enlighten me, I would appreciate it.

---

### Post by FuturePilot on 2010-01-31
Add something like this to /etc/apache2/sites-enabled/000-default

```
Alias /foo/ "/var/bar/"
    <Directory "/var/bar">
        Options Indexes FollowSymLinks MultiViews
        DirectoryIndex index.html
        AllowOverride Options
        Order allow,deny
        allow from all
     </Directory>
```

Be sure to add it inside </VirtualHost>

---

### Post by Barriehie on 2010-01-31
You can point the server to the directory via the DocumentRoot directive in the sites config file, note this doesn't use the trailing slash.

```
DocumentRoot /var/www/local
```

I've got that line in my .conf file and local is a symlink to the real folder location.

HTH,
Barrie

---

### Post by undecim on 2010-01-31
That did it FuturePilot, thanks

---

