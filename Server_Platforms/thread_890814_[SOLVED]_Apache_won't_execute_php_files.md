---
title: "[SOLVED] Apache won't execute php files"
date: 2008-08-15
forum: Server Platforms
---

### Post by jumping_snake on 2008-08-15
I'm in the same situation many people have been in before:
I've setup an Apache 2 virtual server that I'm trying to get php files to execute (read: actually work instead of either displaying the source code or having Firefox ask which program I want to open the file with/save it somewhere). My php files are stored outside of the Apache web directory root directory.

I’ve tried a buch of the fixes posted on sites/forums, but still to no avail.

I've made sure the php files are set to run in /etc/mime.types
Here’s part of my virtual host of my /etc/apache2/sites-available file:

        <Directory "full path to files">
                Options FollowSymLinks IncludesNOEXEC
                AllowOverride None
                Order allow,deny
                Allow from all
                AddType application/x-http-php .php
                AddType application/xml .xml
        </Directory>

I can run a test.php which contains just the code to run the phpinfo function and that runs, but even other php files in the same directory won’t execute.

Any other ideas? Any help would be appreciated as I’m trying to get this working ASAP.

Server Details:
**OS**
Ubuntu 8.04 Server
**Apache**
Server version: Apache/2.2.8 (Ubuntu)
Server built:   Jun 25 2008 13:54:13
**PHP**
Version 5.2.4-2ubuntu5.3 w/Suhosin patch

---

### Post by sillyxone on 2008-08-15
if you can actually see the phpinfo() in a browser from test.php but see the source code/Firefox ask for other .php files, try to figure out the difference between them. 

Given the fact that test.php can run, I think there's nothing wrong with your server settings. 

I know, my answer is pretty useless. In this case, it's useful to be able to interact with the server directly to try a few tests to pin point the problem.

Don't forget to restart Apache with every changes to be on the safe side.

My /etc/apache2/mods-enabled/php5.conf, notice "httpd" instead of "http", could it be the problem?

```

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

---

### Post by jumping_snake on 2008-08-15
omg....the fix was the simple addition of the "d" on httpd.....

Thanks for the close look and input!!

---

### Post by yashkelkar on 2011-07-17
I can't execute a .php file on my apache server. It says the requested url was not found. We need the .php file in the apache2 folder right? But i can't save it or paste in the server folder in etc.

---

### Post by Wim Sturkenboom on 2011-07-18
> **yashkelkar said:**
> I can't execute a .php file on my apache server. It says the requested url was not found. We need the .php file in the apache2 folder right? But i can't save it or paste in the server folder in etc.
The PHP file needs to be in the web root (in a standard Ubuntu setup it's /var/www). And you need to sort out the permissions to be able to write in that directory.

PS This thread is nearly 3 years old

---

