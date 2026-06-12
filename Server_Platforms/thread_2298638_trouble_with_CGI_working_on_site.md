---
title: "trouble with CGI working on site"
date: 2015-10-12
forum: Server Platforms
---

### Post by micahpage on 2015-10-12
in my /etc/apache2/apache2.conf i added:
```
ScriptAlias "/cgi-bin/" "/var/www/html/cgi-bin"<Directory "/var/www/html/cgi-bin">
    AllowOverride None
    Options +ExecCGI +MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
    Allow from all
    AddHandler cgi-script .py
    AddHandler cgi-script .cgi
    AddHandler wsgi-script .wsgi




</Directory>



```

permissions:
```
metulburr /var/www/html/cgi-bin $ ls -ltotal 16
-rwxr-xr-x 1 root root 1397 Oct  2 00:25 portingguide.py
-rwxr-xr-x 1 root root 8410 Oct  2 00:25 versiondiff.py



```

and the url i am trying to go to is
[http://python-gaming.com/cgi-bin/portingguide.py](http://python-gaming.com/cgi-bin/portingguide.py)

However i just get the usual non-existant page of database connection error. IS there a step that i am missing?


EDIT:
there error log shows
```
[Mon Oct 12 17:29:25.859291 2015] [mpm_prefork:notice] [pid 25616] AH00169: caught SIGTERM, shutting down[Mon Oct 12 17:29:26.638422 2015] [mpm_prefork:notice] [pid 26755] AH00163: Apache/2.4.7 (Ubuntu) mod_fcgid/2.3.9 PHP/5.5.9-1ubuntu4.13 mod_wsgi/3.4 Python/2.7.6 configured -- resuming normal operations
[Mon Oct 12 17:29:26.638526 2015] [core:notice] [pid 26755] AH00094: Command line: '/usr/sbin/apache2'
```

I loaded the cgi module
```
[COLOR=#111111][FONT=Consolas]sudo a2enmod cgi[/FONT][/COLOR]
```
and then restarted apache, but it still does not work.

---

### Post by micahpage on 2015-10-12
i noticed this text regarding cgi when restarting apache. I am not really sure what it means?
```
metulburr /etc/apache2/mods-available $ sudo service apache2 restart * Restarting web server apache2
[Mon Oct 12 17:43:27.082479 2015] [alias:warn] [pid 29090] AH00671: The ScriptAlias directive in /etc/apache2/conf-enabled/serve-cgi-bin.conf at line 11 will probably never match because it overlaps an earlier ScriptAlias.
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
   ...done.



```

I edited this file to have the same path
/etc/apache2/conf-enabled/serve-cgi-bin.conf
```
<IfModule mod_alias.c>    <IfModule mod_cgi.c>
        Define ENABLE_USR_LIB_CGI_BIN
    </IfModule>


    <IfModule mod_cgid.c>
        Define ENABLE_USR_LIB_CGI_BIN
    </IfModule>


    <IfDefine ENABLE_USR_LIB_CGI_BIN>
        ScriptAlias /cgi-bin/ /var/www/html/cgi-bin/
        <Directory "/var/www/html/cgi-bin">
            AllowOverride None
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Require all granted
        </Directory>
    </IfDefine>
</IfModule>



```
but that did not seem to work either i still get the same message when restarting apache

---

