---
title: "[Apache] 2 Django instalations - 1 Server - 1 IP - 2 Ports"
date: 2011-04-24
forum: Server Platforms
---

### Post by Pyro.699 on 2011-04-24
Hey,

So im currently working on 2 django websites right now and have been able to properly get one of the instalations working with apache. Before i go further ill post my */etc/apache2/httpd.conf* and */etc/apache2/sites-available/default*

_/etc/apache2/httpd.conf_
```

 <Location "/">
        SetHandler python-program
        PythonHandler django.core.handlers.modpython
        SetEnv DJANGO_SETTINGS_MODULE mysiteA.settings
        PythonDebug On
        PythonPath "['/path/to/', '/var/'] + sys.path"
</Location>

<Location "/static/admin">
        SetHandler None
</Location>

<Location "/static">
        SetHandler None
</Location>

<Location "/phpmyadmin">
        SetHandler None
</Location>

Alias /static/admin /usr/local/lib/python2.6/dist-packages/django/contrib/admin/media
Alias /static /path/going/to/static

```_/etc/apache2/sites-available/default_
```

<VirtualHost *:80>
        ServerAdmin <email removed>
        ServerName mysiteA

        SetEnv DJANGO_SETTINGS_MODULE mysiteA.settings

        ErrorLog ${APACHE_LOG_DIR}/error_mysiteA.log
        CustomLog ${APACHE_LOG_DIR}/access_mysiteA.log combined

        # Possible values include: debug, info, notice, warn, error, crit, alert, emerg.
        LogLevel debug
</VirtualHost>

<VirtualHost *:8080>
        ServerAdmin <email removed>
        SetEnv DJANGO_SETTINGS_MODULE mysiteB.settings
        ServerName mysiteB

        ErrorLog ${APACHE_LOG_DIR}/error_mysiteB.log
        CustomLog ${APACHE_LOG_DIR}/access_mysiteB.log combined

        # Possible values include: debug, info, notice, warn, error, crit, alert, emerg.
        LogLevel debug
</VirtualHost>

```As you can probably see from me already starting the second site config in the file above id like this to happen:

[LIST]
[*][http://127.0.0.1/](http://127.0.0.1/) -> Will go to the site located at /path/to/myiteA
[*][http://127.0.0.1:8080/](http://127.0.0.1:8080/) -> Will go to the site located at /var/mysiteB/
[/LIST]
Im not sure how to edit the httpd.conf file to specify what port the files will be served on.

Anyways, if you need more details i can do my best :)

Thanks
~Cody Woolaver

---

