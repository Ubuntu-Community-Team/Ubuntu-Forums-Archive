---
title: "Basic Configuration To Execute PHP Under Apache"
date: 2011-04-07
forum: Server Platforms
---

### Post by cmnorton on 2011-04-07
On Ubuntu 10.04 with Apache and PHP installed, I can execute a test.php file  

```
<?php
print_r (phpinfo());
?>

```

if I specify it on my Apache web server ```
http://localhost/index.php
```

However, I am not able to configure the web site to execute index.php automatically.

These are the settings I have. 

```
<VirtualHost *:80>
    ServerAdmin dbadmin@town.arlington.ma.us 

    DocumentRoot /var/www
    
    #php_value include_path ".:/var/www/html"

    <Directory /var/www/html/>
        Options Indexes FollowSymLinks MultiViews ExecCgi
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
.
.
.
AddType application/x-httpd-php .php

AddType text/html       php

# To use CGI scripts outside of ScriptAliased directories:
# (You will also need to add "ExecCGI" to the "Options" directive.)
#
#AddHandler cgi-script .cgi
AddHandler php5-script php
#

```

What am I missing? Thanks. cmn

---

### Post by Fire_Chief on 2011-04-07
Looks like you need to have the DirectoryIndex defined.
From [https://help.ubuntu.com/10.10/serverguide/C/httpd.html]("https://help.ubuntu.com/10.10/serverguide/C/httpd.html")

> The DirectoryIndex is the default page served by the server when a user requests an index of a directory by specifying a forward slash (/) at the end of the directory name.

For example, when a user requests the page [http://www.example.com/this_directory/](http://www.example.com/this_directory/), he or she will get either the DirectoryIndex page if it exists, a server-generated directory list if it does not and the Indexes option is specified, or a Permission Denied page if neither is true. The server will try to find one of the files listed in the DirectoryIndex directive and will return the first one it finds. If it does not find any of these files and if Options Indexes is set for that directory, the server will generate and return a list, in HTML format, of the subdirectories and files in the directory. The default value, found in /etc/apache2/mods-available/dir.conf is "index.html index.cgi index.pl index.php index.xhtml index.htm". Thus, if Apache2 finds a file in a requested directory matching any of these names, the first will be displayed.


You'll want to change the order of the index files listed or just remove the ones you don't want it to look for.

Cheers!

---

### Post by cmnorton on 2011-04-07
Many Thanks. I added a DirectoryIndex to the sites-available/default, in addition to mods-available/dir.conf.
That fixed the problem.

> **Fire_Chief said:**
> Looks like you need to have the DirectoryIndex defined.
From [https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)



You'll want to change the order of the index files listed or just remove the ones you don't want it to look for.

Cheers!

---

