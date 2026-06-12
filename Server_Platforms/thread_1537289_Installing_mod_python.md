---
title: "Installing mod_python"
date: 2010-07-23
forum: Server Platforms
---

### Post by Moptop650 on 2010-07-23
Hey guys,

I'm trying to install mod_python on my Ubuntu 9.10 32 bit apache2 server. I have the module installed (via apt-get) and I know the module is loaded because the following appears in my log when I restart apache:


```
[Fri Jul 23 15:00:51 2010] [notice] Graceful restart requested, doing restart
PHP Deprecated: *Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Deprecated: *Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/ming.ini on line 1 in Unknown on line 0
[Fri Jul 23 15:00:51 2010] [notice] mod_python: Creating 8 session mutexes based on 40 max processes and 0 max threads.
[Fri Jul 23 15:00:51 2010] [notice] mod_python: using mutex_directory /tmp
[Fri Jul 23 15:00:51 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4 with Suhosin-Patch mod_python/3.3.1 Python/2.6.5 mod_perl/2.0.4 Perl/v5.10.1 configured -- resuming normal operations
```


Anyways, it's not working. I've added this into the config file for the site I want python on (/etc/apache2/sites-available/default)

```
<Directory /home/www/webroot/>
 Options Indexes FollowSymLinks MultiViews +ExecCGI
 AllowOverride ALL
 Order allow,deny
 allow from all
 AddHandler mod_python .py
 PythonDebug On
</Directory>
```

But no dice. It just download the [python file](http://vps.xmop.org/test.py). Also, [http://vps.xmop.org/mpinfo](http://vps.xmop.org/mpinfo)

Edit: I've also tried
```
<Files ~ "\.(py|pyc)$">
 SetHandler mod_python
 PythonDebug On
 </Files>

```

---

### Post by javierrivera on 2010-07-23
I don't really understand apache configuration but this is how I did it  on a site that I manage too long ago to remember the why's or the how's.

```
    
<Location ~ "xxxxxx">
SetHandler python-program
PythonPath "['/home/javier/django'] + sys.path"
SetEnv DJANGO_SETTINGS_MODULE gacelaweb.settings
PythonHandler django.core.handlers.modpython
PythonDebug On
</Location>

```

The PythonPath, SetEnv and PythonHandler are Django specific or site specific. It's running on Hardy (8.04 LTS), so maybe something have changed.

Hope that it's useful.

---

### Post by javierrivera on 2010-07-23
BTW, mod_python is obsolete and deprecated. You should be using mod_wsgi for a new installation wherever it's possible.

---

### Post by Moptop650 on 2010-07-23
Would wsgi let me use python on apache the same way mod_perl does for perl? IE anything printed out goes to the client.

---

