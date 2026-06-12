---
title: "Apache2: Problem setting up ServerName"
date: 2010-07-22
forum: Server Platforms
---

### Post by maitrebart on 2010-07-22
I managed to setup apache2. The web site works on my lan if I use an address line like this:

```
http://localhost/mywebsitedir/
```

in my browser. I have a symlink (mywebsitedir) in /var/www/ which leads to a mounted fs (/mnt/mywebsitedir).

In that directory I have an index.php for which apache2 manages to parse it with php so that the browsers receive an html file. The basic stuff. :)

However if I use an address line such as this:

```
http://mywebsite/
```

the browser receives the php source file (application/x-httpd-php) and ask me to save it... :confused:

My apache2 virtual host description file is:

```
<VirtualHost *:80>
        ServerAdmin me@mywebsite

        DocumentRoot /mnt/mywebsitedir

        ServerName mywebsite
        
        <Directory /mnt/mywebsitedir/>
                Options -Indexes +FollowSymLinks +MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
</VirtualHost>
```

My /etc/hosts file has a line like this:

```
127.0.0.1 localhost mywebsite
```

Note: I'm just interested to make it run over my lan for the moment.

Can someone help me make this work with [http://mywebsite/](http://mywebsite/) please?

Btw, when I restart apache2, I get the following message:

```
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.0.104 for ServerName
[Thu Jul 22 21:57:17 2010] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
```

though the service responds with [ OK ]. I don't know if this has anything to do with my problem?

---

### Post by Sanjeevtrip on 2010-07-23
did you add php Handler
it should be similar like

```

# Use for PHP 4.x:
#LoadModule php4_module        modules/libphp4.so
#AddHandler php-script   php

# Use for PHP 5.x:
LoadModule php5_module        modules/libphp5.so
AddHandler php5-script php 

# Add index.php to your DirectoryIndex line:
DirectoryIndex index.html index.php

AddType text/html       php

```

---

### Post by haydenh on 2010-07-23
> **maitrebart said:**
> 

Btw, when I restart apache2, I get the following message:

```
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.0.104 for ServerName
[Thu Jul 22 21:57:17 2010] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
```though the service responds with [ OK ]. I don't know if this has anything to do with my problem?

Are you behind a router? If so, you need to open port 80 up. I had a similar problem and once I opened this port up on my local server ip, it worked like a charm.

---

### Post by maitrebart on 2010-07-23
> **Sanjeevtrip said:**
> did you add php Handler
it should be similar like
[...]

I did not have the AddHandler. I added it but without success.

I think I can live with using subdomains after all!

Thank you.

---

### Post by maitrebart on 2010-07-23
> **haydenh said:**
> Are you behind a router? If so, you need to open port 80 up. I had a similar problem and once I opened this port up on my local server ip, it worked like a charm.

No, I access my server from within my lan. However I fixed both errors by adding "ServerName homer" (my host name) and commenting out "NameVirtualHost *" in 000-default.

Thanks.

---

