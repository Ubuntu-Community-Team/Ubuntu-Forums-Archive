---
title: "Apache permissions ExecCGI help"
date: 2008-07-01
forum: Server Platforms
---

### Post by strife303 on 2008-07-01
Thanks for looking at this. If there's a forum that would be better suited for this question please let me know.

Problem:

I'm running apache2 and am trying to have perl scripts that use binaries owned by root consistently run in public_html. When I try to have these scripts run the browser tries to download the script's source, but even after downloading the source the file is blank. I am able to execute simple perl scripts that don't use binaries (for example, a hello script works fine). 

None of my scripts have bugs, they are set to 755, and the directory is set to 755 - and I am able to use them on servers that aren't my own and they run in terminal with no problems. I'm not using mod-perl.

What didn't work:
```

chown www-data:www-data myscript.pl
chown -R www-data:www-data public_html

```
The top part of my sites-enabled file:
```

NameVirtualHost *
<VirtualHost *>

        ServerAdmin Me
        AddHandler cgi-script .cgi .pl .pm
        DocumentRoot /home/me/public_html

        <Directory />
                Options FollowSymLinks +ExecCGI
                AllowOverride None
                Order allow,deny
                Allow from all

        </Directory>

        <Directory /home/me/public_html>
                Options Indexes FollowSymLinks MultiViews +ExecCGI 
                AddHandler cgi-script .cgi .pl .pm
                AllowOverride None
                Order allow,deny
                Allow from all
                Include /etc/apache2/mods-available/cgid.load
                Include /etc/apache2/mods-available/suexec.load
        </Directory>


```

---

