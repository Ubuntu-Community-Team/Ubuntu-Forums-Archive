---
title: "Apache2 Subdomain configuration"
date: 2011-07-20
forum: Server Platforms
---

### Post by lord_raptor on 2011-07-20
Hello,
I need a little help with configuring my webserver.

The thing is, I want that if someone tries to reach a subdomain that does'nt exist, that the server simply answers with the main domain, therefor I added the ServerAlias *.example.com to my example.com.conf (I have/want a seperate .conf file for each domain or subdomain). Now the problem is, that subdomains only work, if their conf file is first in alphabetical order, because of the order the files are read in. Now, I'm pretty sure, that I'm not doing this correctly. What's the correct way to get the behaviour I want?

Greetings
Raptor


example.com.conf
```

<VirtualHost *:80>
DocumentRoot "/var/www/example.com/htdocs/"
ServerName example.com
ServerAlias *.example.com
<Directory "/var/www/example.com/htdocs">
allow from all
AllowOverride All
Options FollowSymLinks -Indexes MultiViews
</Directory>
</VirtualHost>

```

bla.example.com.conf
```

<VirtualHost *:80>
DocumentRoot "<path>/<to>/<location>"
ServerName bla.example.com
ServerAlias *.bla.example.com bla.*
<Directory "<path>/<to>/<location>">
allow from all
AllowOverride None
Options FollowSymLinks +Indexes MultiViews
</Directory>
</VirtualHost>
```

---

### Post by ruffEdgz on 2011-07-20
Try this:
example.com.conf
```
<VirtualHost example.com:80>
DocumentRoot "/var/www/example.com/htdocs/"
ServerName example.com
ServerAlias *.example.com
<Directory "/var/www/example.com/htdocs">
allow from all
AllowOverride All
Options FollowSymLinks -Indexes MultiViews
</Directory>
</VirtualHost>
```
bla.example.com.conf
```

<VirtualHost bla.example.com:80>
DocumentRoot "<path>/<to>/<location>"
ServerName bla.example.com
ServerAlias *.bla.example.com bla.*
<Directory "<path>/<to>/<location>">
allow from all
AllowOverride None
Options FollowSymLinks +Indexes MultiViews
</Directory>
</VirtualHost>

```
Have two config file with the wildcard (*) in the VirtualHost will not work if you want subdomains to work. 

You could probably place the 'example.com.conf' with that wildcard but you will want to make sure in the /etc/apache2/sites-enabled/ section its the last one since the order does matter (thats why the default symlink in there was set to 001-default).

Cheers!

---

