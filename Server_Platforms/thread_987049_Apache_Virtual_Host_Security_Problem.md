---
title: "Apache Virtual Host Security Problem"
date: 2008-11-19
forum: Server Platforms
---

### Post by xoroz on 2008-11-19
I have a apache server running a site that authenticates with login.php
Basicaly it allows to edit the address and jump to folder browsing!
Problem:
[http://10.10.10.1/wwwroot/QA/acceso/login.php?accesscheck=%2Fwwwroot%2FJP%2Facceso%2Findex.php](http://10.10.10.1/wwwroot/QA/acceso/login.php?accesscheck=%2Fwwwroot%2FJP%2Facceso%2Findex.php)
That brings up the login.php page

But I can easly avoid it by typing:
[http://10.10.10.1/wwwroot/QA](http://10.10.10.1/wwwroot/QA)
Now I can BROWSE ALL FOLDERS!!!

I must fix this security problem.Please help me out.
My apache2 is using virtual hosts and I got the default config like this:

```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
#               Options FollowSymLinks
                AllowOverride None
        </Directory>

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log
 # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel notice

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

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
*edit
I just saw that under /var/www/index.php redirects to 
/wwwroot/QA/acceso/login.php

Shuold I be using Directory Alias ?
How can I deny folder browsing, without messing with the application?
The problem I see is that if I define Document root to
the location of login.php the other files are in a folder under...
ex:
/wwwroot/QA/acceso/login.php
Files locations
/wwwroot/QA/files/
/wwwroot/QA/morefiles/

hope I was clear enough, any advice is welcome.

---

### Post by hyper_ch on 2008-11-19
you want to require everyone to authenticate themselves?

---

### Post by xoroz on 2008-11-19
well, the application should handle that.
I dont want apache to authenticate, just want to deny folder browsing...
I reconfigured using 
Direcory alias and its better, but still I can browse folders 
If I know what the names..

---

### Post by hyper_ch on 2008-11-19
Well, this is
```

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews

```
enables indexing... you would have to just disallow it...

---

### Post by daboroe on 2008-11-19
```
<Directory /var/www/>
                Options FollowSymLinks MultiViews
...

```

is what he is talking about in post before mine.

---

### Post by xoroz on 2008-11-19
Thanks for the replies
Tried that but I can still browse the /ftp folder
I removed the Virtual Host and setup it like this in apache2.conf

```

#New Config

DocumentRoot /storage/wwwroot

<IfModule alias_module>
    Alias /JP  /storage/wwwroot/JP
    <Directory "/storage/wwwroot/JP">
        Options  FollowSymLinks MultiViews
         AllowOverride None
         #AllowOverride All
         order allow,deny
     </Directory>  

#FTP- PROBLEM SHOULD NOT BE ABLE TO BROWE                           
    Alias /ftp  /storage/wwwroot/ftp
    <Directory "/storage/wwwroot/ftp">
        Order deny,allow
        Deny from all
     </Directory>

<IfModule alias_module>

```

Bu still I can browse FTP, any ideas??
edited*
Hum.. I could try seting up a index.php that redirects to authentication page, is that a good solution?

---

