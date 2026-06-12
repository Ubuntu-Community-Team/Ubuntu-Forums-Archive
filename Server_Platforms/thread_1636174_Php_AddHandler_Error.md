---
title: "Php AddHandler Error"
date: 2010-12-02
forum: Server Platforms
---

### Post by poulshichone on 2010-12-02
Hi Everyone,
I'am currently trying to create my own httpd file to set up a web server.
I'am struggling with the error and i can't find out how to resolve it :
```
syntax error on line 6 of /etc/httpd/conf/extra/php5_module.conf:
Invalid command 'AddHandler', perhaps misspelled or defined by a module not included in the server configuration
```
This is my httpd.conf file :
```
User http
Group http
LockFile /etc/httpd/apache2.lock
PidFile /var/run/apache2.pid
Listen *:80
Timeout 30
MaxClients 200
MaxRequestsPerChild 0
StartServers 5
MinSpareServers 5
MaxSpareServers 10
ServerRoot "/etc/httpd/"
ServerAdmin [email]Xy@gmail.con[/email]
ServerName [www.Xy.org](www.Xy.org)
ServerSignature Email
<Location />
    Options -Indexes
</Location>
LoadModule alias_module modules/mod_alias.so
LoadModule autoindex_module modules/mod_autoindex.so
LoadModule dir_module modules/mod_dir.so
LoadModule rewrite_module modules/mod_rewrite.so
LoadModule unique_id_module modules/mod_unique_id.so
LoadModule php5_module modules/libphp5.so
Include conf/extra/php5_module.conf
DirectoryIndex index.html index.php
DocumentRoot "/srv/http"
```
And the file php5_module.conf :
```
<IfModule dir_module>
    <IfModule php5_module>
        DirectoryIndex index.php index.html
        AddHandler application/x-httpd-php .php
        AddHandler application/x-httpd-php-source .phps
    </IfModule>
</IfModule>
```
Thank you
Have a nice day

---

### Post by SeijiSensei on 2010-12-02
OK, I'll ask the dumb question first.  Did you install php5?

---

### Post by Ryan Dwyer on 2010-12-03
It's SetHandler, not AddHandler.

---

### Post by SeijiSensei on 2010-12-03
> **Ryan Dwyer said:**
> It's SetHandler, not AddHandler.

[http://httpd.apache.org/docs/2.2/mod/mod_mime.html#addhandler](http://httpd.apache.org/docs/2.2/mod/mod_mime.html#addhandler)

---

### Post by Ryan Dwyer on 2010-12-03
Oh, my bad. I looked in my /etc/apache2/mods-available/php5.conf and found this:

```

    <FilesMatch "\.ph(p3?|tml)$">
	SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.phps$">
	SetHandler application/x-httpd-php-source
    </FilesMatch>

```

But that's different because it's not specifying the file extension in the directive itself.

It looks like you need to load mod_mime.

---

