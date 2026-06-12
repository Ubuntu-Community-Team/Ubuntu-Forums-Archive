---
title: "ubuntu14.04 apache multi website"
date: 2015-01-14
forum: Server Platforms
---

### Post by selvapandian2 on 2015-01-14
platform: 
os:ubuntu14.04 server x64
weserver: Apache/2.4.10 (Ubuntu) & PHP Version 5.5.12-2ubuntu4.1

i have web sites site1(html) & site2(php) i want access both site via same IP.
like www.<ipaddress>/site1/index.html & www.<ipaddress>/site2/index.php

below my configuration:

root dir: /var/www/websites/site1/index.html
root dir: /var/www/websites/site2/index.php

---------------------------------

access given to root dir: /var/www/websites/

----\site-available\site1.config
<VirtualHost *:80>
    
ServerAdmin webmaster@localhost
    
DocumentRoot /var/www/websites/site1/
</VirtualHost>


----\site-available\site2.config

<VirtualHost *:80>
    
ServerAdmin webmaster@localhost
    
DocumentRoot /var/www/websites/site2/
</VirtualHost>

>a2ensite site1.config
>a2ensite site2.config


error: could not found web page on server

please help

---

### Post by slickymaster on 2015-01-14
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by cyclobs on 2015-01-15
for virtual servers you must specify the server name for each

```

<VirtualHost *:80>
  ServerName <ipaddress here> (or DNS name 'domain1.com')
  DocumentRoot /var/www/site1
</VirtualHost>

<VirtualHost *:80>
  ServerName <ipaddress here> (or DNS name 'domain2.com')
  DocumentRoot /var/www/site2
</VirtualHost>

```

---

### Post by volkswagner on 2015-01-15
You can do this with one vhost file. What you are trying to accomplish is basic folder-based site structure.

You can use the default.vhost file and change root directory to /var/www/websites

This will allow you to enter [http://ipofserver/site1](http://ipofserver/site1) or [http://ipofserver/site2](http://ipofserver/site2) to access either site, provided you have an index.html or index.php page in each directory.

You can also add a simple index.html file with links to each of the above sites in the /var/www/websites directory.
Create the simple index.html file as "links to my websites" using relative links  
```
<a href="site1/index.html">Site One</a>
<a href="site2/index.php">Site Two</a>
``` 

Then you can simply enter the ip address of the server in the url and choose one of the links.

---

