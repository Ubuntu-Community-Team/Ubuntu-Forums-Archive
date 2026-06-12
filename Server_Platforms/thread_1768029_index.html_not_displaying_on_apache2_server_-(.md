---
title: "index.html not displaying on apache2 server :-("
date: 2011-05-26
forum: Server Platforms
---

### Post by koshiuk on 2011-05-26
Hi,  I'm having a bit of trouble getting my index.html to display. when i use [http://www.proxy-service.de](http://www.proxy-service.de) and type in my dyndns url i just get "index of /" and not the index.html page

ive got a index.html in var/www and home/gav/public_html  and set chmod -R 755 to the index.html 

and still no joy....

gav@lapfrog:/etc/apache2$ gksudo gedit httpd.conf

Userdir public_html
Options +Indexes
Options All

ServerName localhost

<Directory "/home/gav/public_html/">
Order allow,deny
Allow from all
AllowOverride All
</Directory> 


Please help!!

---

### Post by ruffEdgz on 2011-05-26
Did you try editing the /etc/apache2/sites-available/default file to make your new directory of '/home/gav/public_html/' the new document root? The information below can be updated in the default file.
```

DocumentRoot /home/gav/public_html/
ServerName localhost

<Directory "/home/gav/public_html/">
Order allow,deny
Allow from all
AllowOverride All
</Directory> 

```

Hope this helps.

---

### Post by koshiuk on 2011-05-26
Many thanks for that, definatly on the right track but getting the error:

[I]The requested resource could not be loaded because the server returned an error:
   **403 Forbidden** (?).   [/I] 

apologies for the questions, this is my 1st attempt of creating a webserver!  so close but so far :-o

so guess this is a permissions issue?

[SIZE=3]**my default is now:**[/SIZE]
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /home/gav/public_html

<Directory /home/gav/public_html/>
    Order allow,deny
    Allow from all
    AllowOverride All
</Directory>
    <Directory /home/gav/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>



[SIZE=3]**and ive also changed the "mysites" to:**[/SIZE]
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/gav/public_html/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory  /home/gav/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by ruffEdgz on 2011-05-26
I don't think you need both a default and mysites if you like but I would like to keep an eye on your default file for now:

See this section of code:
```

<Directory /home/gav/public_html/>
Order allow,deny
Allow from all
AllowOverride All
</Directory>
<Directory /home/gav/public_html/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

```
You don't need them both, you can probably just use the below section of code instead:
```

<Directory /home/gav/public_html/>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

```
You will also want to place into the default file below your DocumentRoot this line of code:
```

<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

```

Lets see how that goes in solving your issue.

---

### Post by koshiuk on 2011-05-26
Thanks, ive cleaned the default file up and still getting that forbidden error;

i've gone into /home/gav/public_html and the permission are as follows:

-rwxr-xr-x 1 gav gav 236 2011-05-18 19:02 index.html

appreciate your help....

---

### Post by koshiuk on 2011-05-26
and my /etc/apache2$ gksudo gedit httpd.conf

permissions:
-rw-r--r-- 1 root root   173 2011-05-26 22:01 httpd.conf


Userdir public_html
Options +Indexes
Options All

ServerName localhost

<Directory "/home/gav/public_html/">
Order allow,deny
Allow from all
AllowOverride All
</Directory>

----------------

thought id check the apach2.conf file (so many!)

#ServerRoot "/etc/apache2"

should i take the hash out?

---

### Post by ruffEdgz on 2011-05-26
I don't have a very complicated apache web server and saying that, on my apache2.conf, I have the ServerRoot "/etc/apache2" **NOT** commented out so you could try uncommenting that so it can look into that directory to grab the configuration files.

Try and clean up the httpd.conf file since your default file you updated from the previous post will hand the rest of your configuration needs.

---

### Post by koshiuk on 2011-05-26
yeh im trying to keep things simple really as quite new to apache2 config... Mmm ok will do some more research and tweaking... things can only get better as they say :-)

thanks

---

