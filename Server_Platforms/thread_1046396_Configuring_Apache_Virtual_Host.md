---
title: "Configuring Apache Virtual Host"
date: 2009-01-21
forum: Server Platforms
---

### Post by cmnorton on 2009-01-21
I am running Kubuntu 8.04. I want define a virtual host, so I can separate regular port 80 traffic. This configuration 

Listen 9285

<VirtualHost _default_:9285>

DocumentRoot "/var/www/arlington_donate/html"

<Directory "/var/www/arlington_donate/html">
    Options +Includes
</Directory>

ScriptAlias /arlington_donate "/var/www/arlington_donate"

<Directory "/var/www/arlington_donate">
    AllowOverride None
    Options ExecCGI FollowSymLinks
    Order allow,deny
    Allow from all
</Directory>

</VirtualHost>

is producing this error.

[error] VirtualHost _default_:9285 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
   ...done.

What am I missing about configuring this? This works on Red Hat EL 4..

---

### Post by mahalie on 2009-03-20
I am having the same error. I am new to Apache configuration, used to using shared web hosting. Have read many docs, can someone point to a good thread or tutorial on setting up virutal host correctly for local dev?

---

### Post by dacorr on 2009-03-20
try

NameVirtualHost foo:9285

<VirtualHost foo:9285>
servername foo
DocumentRoot /var/www/arlington_donate/html

<Directory /var/www/arlington_donate/html>
Options +Includes
</Directory>

ScriptAlias /arlington_donate "/var/www/arlington_donate"

<Directory /var/www/arlington_donate>
AllowOverride None
Options ExecCGI FollowSymLinks
Order allow,deny
Allow from all
</Directory>


</VirtualHost>

---

