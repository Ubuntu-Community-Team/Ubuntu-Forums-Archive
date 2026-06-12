---
title: "Can’t change the cgi-bin path in Apache"
date: 2010-08-11
forum: Server Platforms
---

### Post by amanjsingh on 2010-08-11
Installed Apache and the default web root was /var/www I wanted to change the cgi-bin to somewhere within the /var/www but I cannot. It only works at /usr/lib/cgi-bin. I am trying to work out the Python CGI to be precise. It works at /usr/lib/cgi-bin but gives a 404 at other places like /home/aj/public_html/cgi-bin or /var/www/cgi-bin. 

I even tried it with putting a webroot directory in my home directory with a cgi-bin in it and made the changes accordingly in the conf. but the only way it works is when cgi-bin settings point to /usr/lib/cgi-bin otherwise it gives 404.

VirualHost looks like this:

```

<VirtualHost *:80>
   ServerAdmin webmaster@localhost

    #DocumentRoot /var/www
    DocumentRoot /home/aj/public_html

    <Directory />
            Options FollowSymLinks
            AllowOverride None
    </Directory>
    #<Directory /var/www/>
    <Directory /home/aj/public_html/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from all  
            AddHandler mod_python .py
            PythonHandler mod_python.publisher
            PythonDebug On
    </Directory>

    ScriptAlias /cgi-bin/ /home/aj/public_html/cgi-bin/
    #ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    #<Directory /usr/lib/cgi-bin/>
    <Directory /home/aj/public_html/cgi-bin/>
            AllowOverride None
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Order allow,deny
            Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel debug

    CustomLog /var/log/apache2/access.log combined

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


Apache log has this error:

```
script not found or unable to stat: /home/aj/public_html/cgi-bin
```

Thanks a lot for helping.

---

### Post by amanjsingh on 2010-08-11
So, python is not working as CGI anywhere except its original default:

```
/usr/lib/cgi-bin
```

---

### Post by amanjsingh on 2010-08-11
Got it!

```
    PythonHandler mod_python.publisher 

```
needs to be 

```
    PythonHandler mod_python.cgihandler

```
Then you can run Python as CGI.

---

