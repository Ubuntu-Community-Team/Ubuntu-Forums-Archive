---
title: "redirect to other vhost site without domain name"
date: 2016-09-21
forum: Server Platforms
---

### Post by micahpage on 2016-09-21
Is there a way to redirect to another site from from another vhost site.

By what i mean....

i have 2 sites virtually hosted on the same server

/var/www/site1
/var/www/site2

site1's domain ran out and site2 domain is fine. However if i put the IP address in i go to site2. So without the domain, i cant get to site1. IS there a way i can at least access site1 through the web through site2?

I tried a redirection via php but fails

in /var/www/site2/redirector.php
```
<?phpheader('Location: ../site1');                 
?>
~       
```

---

### Post by SeijiSensei on 2016-09-21
Try an Alias in Apache:
```
Alias /site1 /path/to/the/site1/documentroot
```
Now you should be able to use "http://site2/site1" to get to site1's files.

---

### Post by micahpage on 2016-09-21
I get alias not found

```
metulburr /var/www/python-forum.io/inc/plugins $ Alias /var/www/html /var/www/metulburr.com
Alias: command not found
metulburr /var/www/python-forum.io/inc/plugins $ alias /var/www/html /var/www/metulburr.com              
-bash: alias: /var/www/html: not found
-bash: alias: /var/www/metulburr.com: not found
metulburr /var/www/python-forum.io/inc/plugins $
```

oh whoops you said in Apache.

Is that in the config file? And will this disable site1 domain from getting to the original files?

---

### Post by SeijiSensei on 2016-09-21
Yes, it needs to be in the Apache configuration file for site2, and no, it won't affect being able to get to site1.  That will still work as [http://site1/](http://site1/).

---

### Post by micahpage on 2016-09-21
so i changed that in the config file and restarted apache and im not sure why it is not working. [COLOR=#000000]http://site2/site1 path did not appear to work. 

[/COLOR]SO ill  give exact files, and path, etc.

I have a symlink from /var/www/python-forum.io to /var/www/metulburr.com

my vhost files
> metulburr / $ python codepad.py etc/apache2/sites-enabled/python-forum.io.conf 
The link:  [http://codepad.org/gK4FmNm4](http://codepad.org/gK4FmNm4)
metulburr / $ python codepad.py etc/apache2/sites-enabled/python-gaming.com.conf 
The link:  [http://codepad.org/t2W3O4uo](http://codepad.org/t2W3O4uo)




where python-forum.io is going to the path /var/www/metulburrr.com
and python-gaming.com is going to the path /var/www/html 

I am not going to pay for python-gaming.com domain and want that directory of /var/www/html to be viewable under python-forum.io

What url is exactly suppose to get to it?
[http://python-forum.io/html](http://python-forum.io/html)

---

### Post by SeijiSensei on 2016-09-22
Show us the complete Apache configuration(s).

What do you see in the logs at /var/log/apache2, particularly error.log, when you try the [http://site2/site1/](http://site2/site1/) style URL?  "site1" should match whatever string you used in the Alias command.

---

### Post by micahpage on 2016-09-22
I dont get any errors from 
```
sudo tail -f  /var/log/apache2/error.log

```

when going to
[http://python-forum.io/html/index.html](http://python-forum.io/html/index.html)
or
[http://python-forum.io/html/]("http://python-forum.io/html/index.html")

All i get is a 404 

/etc/apache2/apaceh2.conf
[http://codepad.org/C3ETqA8e](http://codepad.org/C3ETqA8e)

```
metulburr /etc/apache2 $ lsapache2.conf    conf-enabled  magic           mods-enabled  sites-available
conf-available  envvars       mods-available  ports.conf    sites-enabled
metulburr /etc/apache2 $ cd sites-enabled/
metulburr /etc/apache2/sites-enabled $ ls
python-forum.io.conf  python-forum.net.conf  python-gaming.com.conf
metulburr /etc/apache2/sites-enabled $ 



```

---

### Post by SeijiSensei on 2016-09-23
apache2.conf doesn't matter unless you're using a non-standard configuration.  What's in the configuration files for site1 and site2?

And please post the results here, not on some other site.

---

### Post by micahpage on 2016-09-23
/etc/apache2/sites-enabled/python-forum.io.conf 
```
[TABLE="width: 100%"]
[TR]
[TD][TABLE="width: 100%"]
[TR]
[TD="width: 100%"]<VirtualHost *:80>
    ServerAlias www.python-forum.io
    ServerAdmin webmaster[COLOR=#888888]@localhost[/COLOR]
    DocumentRoot /var/www/metulburr.com
    ServerName python-forum.io
    Alias /var/www/html /var/www/python-forum.io
    <Directory /var/www/metulburr.com>
        Order allow,deny
        Allow from [COLOR=#00AAAA]all[/COLOR]
    </Directory>

    
    [COLOR=#669933]*# The ServerName directive sets the request scheme, hostname and port that*[/COLOR]
    [COLOR=#669933]*# the server uses to identify itself. This is used when creating*[/COLOR]
    [COLOR=#669933]*# redirection URLs. In the context of virtual hosts, the ServerName*[/COLOR]
    [COLOR=#669933]*# specifies what hostname must appear in the request's Host: header to*[/COLOR]
    [COLOR=#669933]*# match this virtual host. For th`e default virtual host (this file) this*[/COLOR]
    [COLOR=#669933]*# value is not decisive as it is used as a last resort host regardless.*[/COLOR]
    [COLOR=#669933]*# However, you must set it for any further virtual host explicitly.*[/COLOR]
    [COLOR=#669933]*#ServerName www.example.com*[/COLOR]


    [COLOR=#669933]*# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,*[/COLOR]
    [COLOR=#669933]*# error, crit, alert, emerg.*[/COLOR]
    [COLOR=#669933]*# It is also possible to configure the loglevel for particular*[/COLOR]
    [COLOR=#669933]*# modules, e.g.*[/COLOR]
    [COLOR=#669933]*#LogLevel info ssl:warn*[/COLOR]

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    [COLOR=#669933]*# For most configuration files from conf-available/, which are*[/COLOR]
    [COLOR=#669933]*# enabled or disabled at a global level, it is possible to*[/COLOR]
    [COLOR=#669933]*# include a line for only one particular virtual host. For example the*[/COLOR]
    [COLOR=#669933]*# following line enables the CGI configuration for this host only*[/COLOR]
    [COLOR=#669933]*# after it has been globally disabled with "a2disconf".*[/COLOR]
    [COLOR=#669933]*#Include conf-available/serve-cgi-bin.conf*[/COLOR]
</VirtualHost>

[COLOR=#669933]*# vim: syntax=apache ts=4 sw=4 sts=4 sr noet*[/COLOR]
[COLOR=#669933][/COLOR]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

/etc/apache2/sites-enabled/python-gaming.com.conf 
```
[COLOR=#000000]<[/COLOR][COLOR=#000000]VirtualHost[/COLOR][COLOR=#000000]*[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#000000]80[/COLOR][COLOR=#000000]>[/COLOR]    ServerAdmin webmaster[COLOR=#888888]@localhost[/COLOR]
    DocumentRoot /var/www/html
    ServerName python-gaming.com
    ServerAlias www.python-gaming.com
[COLOR=#669933]*#    <Directory /var/www/html>*[/COLOR]
[COLOR=#669933]*#        Order allow,deny*[/COLOR]
[COLOR=#669933]*#        Allow from all*[/COLOR]
[COLOR=#669933]*#    </Directory>*[/COLOR]

<Directory /var/www/html/>
     Options FollowSymLinks
     AllowOverride All
     Require [COLOR=#00AAAA]all[/COLOR] granted

    Options +ExecCGI +Indexes +FollowSymLinks +MultiViews +Includes
[COLOR=#669933]*#    AllowOverride None*[/COLOR]
[COLOR=#669933]*#    Order allow,deny*[/COLOR]
[COLOR=#669933]*#    allow from all*[/COLOR]
    AddHandler cgi-script .py
    AddHandler cgi-script .cgi
    AddHandler wsgi-script .wsgi
    AddHandler default-handler .html .htm
    AddType text/html .shtml
    AddHandler server-parsed .html
    AddHandler server-parsed .shtml
[COLOR=#669933]*#    DirectoryIndex index.shtml index.html*[/COLOR]
    AddOutputFilter INCLUDES .shtml
    AddHandler php5-script php
</Directory>


    
    [COLOR=#669933]*# The ServerName directive sets the request scheme, hostname and port that*[/COLOR]
    [COLOR=#669933]*# the server uses to identify itself. This is used when creating*[/COLOR]
    [COLOR=#669933]*# redirection URLs. In the context of virtual hosts, the ServerName*[/COLOR]
    [COLOR=#669933]*# specifies what hostname must appear in the request's Host: header to*[/COLOR]
    [COLOR=#669933]*# match this virtual host. For the default virtual host (this file) this*[/COLOR]
    [COLOR=#669933]*# value is not decisive as it is used as a last resort host regardless.*[/COLOR]
    [COLOR=#669933]*# However, you must set it for any further virtual host explicitly.*[/COLOR]
    [COLOR=#669933]*#ServerName www.example.com*[/COLOR]

    ServerAdmin webmaster[COLOR=#888888]@localhost[/COLOR]
    DocumentRoot /var/www/html

    [COLOR=#669933]*# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,*[/COLOR]
    [COLOR=#669933]*# error, crit, alert, emerg.*[/COLOR]
    [COLOR=#669933]*# It is also possible to configure the loglevel for particular*[/COLOR]
    [COLOR=#669933]*# modules, e.g.*[/COLOR]
    [COLOR=#669933]*#LogLevel info ssl:warn*[/COLOR]

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    [COLOR=#669933]*# For most configuration files from conf-available/, which are*[/COLOR]
    [COLOR=#669933]*# enabled or disabled at a global level, it is possible to*[/COLOR]
    [COLOR=#669933]*# include a line for only one particular virtual host. For example the*[/COLOR]
    [COLOR=#669933]*# following line enables the CGI configuration for this host only*[/COLOR]
    [COLOR=#669933]*# after it has been globally disabled with "a2disconf".*[/COLOR]
    [COLOR=#669933]*#Include conf-available/serve-cgi-bin.conf*[/COLOR]
</VirtualHost>
 [COLOR=#669933]*# vim: syntax=apache ts=4 sw=4 sts=4 sr noet*[/COLOR]
```

and if its confusing...i renamed the domain metulburr.com -> python-forum.io while making a sym link of /var/www/python-froum.io -> /var/www/metulburr.com because the forum software already pointed to that location and would of had problems if renamed.

---

### Post by SeijiSensei on 2016-09-23
duplicate; see below

---

### Post by SeijiSensei on 2016-09-23
> Alias /var/www/html /var/www/python-forum.io
The Alias directive points a URI to a directory, not one directory to another.  Did you read the [documentation]("https://httpd.apache.org/docs/current/mod/mod_alias.html#alias") for the Alias command at the Apache site?  That should always be your first resource when it comes to configuring Apache.

So you could use 
```
Alias /gaming /var/www/html
```
in the configuration file for python-forum.  That would enable URLs of the form [http://www.python-forum.io/gaming](http://www.python-forum.io/gaming) to reach the old site.  You should remove the configuration file for the defunct python-gaming site.

---

### Post by micahpage on 2016-09-23
> [COLOR=#000000][FONT=&quot]Alias /gaming /var/www/html[/FONT][/COLOR]
oh i was thinking it was Alias Directory1 Directory2

Thanks for the link and info.....and help :)

---

