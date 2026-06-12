---
title: "Wordpress multisite takes over ;-)"
date: 2016-12-10
forum: Server Platforms
---

### Post by ELMIT on 2016-12-10
I was the impresson that wild card dns could destinguish between set hosts and wild card.

I got now example.com as my word press site. With multisite I have site1.example.com and site2.example.com
However, I had a (non wordpress) virtual site as support.example.com. Thats now in the wordpress multisite included.

Besides to use another domain name for static sites, do I have another option to get this done? Maybe in the apache files for example.com.conf and support.example.com.conf ? or in the .htaccess file of wordpress to exclude these hosts?

---

### Post by cariboo on 2016-12-10
Moved to server platforms, you may get help quicker here.

---

### Post by SeijiSensei on 2016-12-10
I can't tell from your description what the problem is.  It sounds like you have multiple Apache virtual hosts.  You need configurations for each ServerName.  

```

<Virtualhost *:80>
ServerName site1.example.com
DocumentRoot /path/to/site1
[stuff]
</VirtualHost>

<Virtualhost *:80>
ServerName site2.example.com
DocumentRoot /path/to/site1
[stuff]
</VirtualHost>

<Virtualhost *:80>
ServerName support.example.com
DocumentRoot /path/to/support
[stuff]
</VirtualHost>

```
Do you have a configuration that looks something like this?

What specifically is the problem?

---

### Post by ELMIT on 2016-12-11
I have config files for support.example.com, ... and for example.com

example.com.conf should cover EVERYTHING, that has not a specific config file.


support.example.com.conf includes the lines:

```
<VirtualHost *:80>
# Admin email, Server Name (domain name) and any aliases
ServerAdmin webmaster@support.example.com
ServerName support.example.com
ServerAlias www.support.example.com

# Index file and Document Root (where the public files are located)
DirectoryIndex index.php
DocumentRoot /var/www/support.example.com/

# Custom log file locations
LogLevel warn
ErrorLog ${APACHE_LOG_DIR}/support.example.com-error.log
CustomLog ${APACHE_LOG_DIR}/support.example.com-access.log combined
</VirtualHost>

```


and example.com.conf

```
<VirtualHost *:80>
# Admin email, Server Name (domain name) and any aliases
ServerAdmin webmaster@elmit.com
ServerName example.com
ServerAlias *.example.com

# Index file and Document Root (where the public files are located)
DirectoryIndex index.php
DocumentRoot /var/www/example.com

<Directory /var/www/example.com>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
</Directory>

# Custom log file locations
LogLevel warn
ErrorLog ${APACHE_LOG_DIR}/example.com-error.log
CustomLog ${APACHE_LOG_DIR}/example.com-access.log combined
</VirtualHost>

```


I was hoping that apache2 will find the priority support.example.com.conf higher than example.com.conf

---

### Post by SeijiSensei on 2016-12-11
There are no priorities.  Apache matches the server part of a URL against the various ServerName and ServerAlias entries.  

I've never used wildcards in aliases.  I like to specify exactly what should happen for every server name.  So I don't know how Apache will handle the situation where there is a definition for support.example.com and another one for *.example.com.  If you get rid of the wildcard and create configurations for each possible ServerName you shouldn't have any problems.

On Ubuntu, the 000-default.conf file is supposed to handle all requests that do not match an ServerName/Alias.  What did you do with that file?

---

### Post by Graham_Willis on 2016-12-11
> There are no priorities. Apache matches the server part of a URL against the various ServerName and ServerAlias entries.

There are - [https://httpd.apache.org/docs/2.4/vhosts/name-based.html](https://httpd.apache.org/docs/2.4/vhosts/name-based.html) :

Name-based virtual hosts for the best-matching set of [<virtualhost>]("https://httpd.apache.org/docs/2.4/mod/core.html#virtualhost")s are processed in the order they appear in the configuration. The first matching [ServerName]("https://httpd.apache.org/docs/2.4/mod/core.html#servername") or [ServerAlias]("https://httpd.apache.org/docs/2.4/mod/core.html#serveralias") is used, with no different precedence for wildcards (nor for ServerName vs. ServerAlias).

---

### Post by volkswagner on 2016-12-12
As Graham_Willis pointed out the Apache vhosts are loaded in order.

You will want to change the name of the config file support.example.com.conf so it comes alfa-numerically before example.com.conf.
This will allow Apache to load requests for support subdomain before honoring the wildcard entry in example.com.conf.

This is why the Apache default config is named 000-default (so it loads first).

---

