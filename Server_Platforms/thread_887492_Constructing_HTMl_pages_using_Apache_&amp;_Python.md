---
title: "Constructing HTMl pages using Apache &amp; Python"
date: 2008-08-12
forum: Server Platforms
---

### Post by ranjithmurugan on 2008-08-12
Hi

I am trying to write a front for a Deployment solution. I have setup an LAMP server.

Have put all my python scripts in /var/www/

In the Index file I call a python script, 

OS: Ubuntu 8.04

Eg:
<html>
<head>
<title>Deployment Lab</title>
<link rel="stylesheet" type="text/css" href="style.css" />
</head>
<body>
<iframe src="lab.py/showForm" width="100%" height="100%"></iframe>
</table>
</body>
</html

[http://localhost/index.html](http://localhost/index.html) constructs an page.

Now the problem starts here. I have a few Links in this page. On clicking the link it has to execute another python script in /var/www/ directory. 

Error :The link is constructed in a way that it includes the script in the index.html file as a directory

[http://localhost/lab.py/login.py](http://localhost/lab.py/login.py)

It should be [http://localhost/login.py](http://localhost/login.py) , looks like there is nothing wrong in the scripts since I have deployed the same scripts on RedHat. 

Can someone help me figure out how to solve issues with the configuration.

httpd.conf:

NameVirtualHost *
<VirtualHost *>
ServerAdmin [email]rmurgan@vmware.com[/email]

DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
<Directory "/var/www/">
Options ExecCGI FollowSymLinks Includes IncludesNOEXEC Indexes MultiViews SymLinksIfOwnerMatch
AllowOverride FileInfo Indexes Limit Options
order allow,deny
allow from all
AddHandler mod_python .py
                PythonHandler mod_python.publisher
                PythonDebug On
</Directory>

ScriptAlias /cgi-bin/ "/usr/lib/cgi-bin/"
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
</Directory>

ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
LogLevel debug

ServerSignature On

Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
HostNameLookups on
Options ExecCGI FollowSymLinks Includes IncludesNOEXEC Indexes MultiViews SymLinksIfOwnerMatch
CustomLog /var/log/apache2/access.log "combined"
ServerName eng-km-ds

</VirtualHost>

---

### Post by StickyStyle on 2008-08-13
Perhaps a <base> tag would be in order.

[http://www.w3schools.com/TAGS/tag_base.asp](http://www.w3schools.com/TAGS/tag_base.asp)

---

