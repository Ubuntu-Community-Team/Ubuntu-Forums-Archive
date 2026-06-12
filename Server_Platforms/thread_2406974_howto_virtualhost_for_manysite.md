---
title: "howto virtualhost for manysite"
date: 2018-11-28
forum: Server Platforms
---

### Post by jahstation on 2018-11-28
I need a very simple configuration for apache2 on ubuntu server machine, but thats drive me crazy, because i cannot find any info about a simple thing that in many case works as default!I've a server without a name, just ip, and now is configured that if im visit the ip is served the homepage of site1.I'd like to have something like:
[list]-ip/site1
[/list]

[list]-ip/site2
[/list]

[list]...
[/list]

[list]ip/siteN
[/list]
how is called organize a site like that? i cannot find it on apache docs!actually on sites-aviable there is "site1.conf":   ```
     ServerAdmin webmaster@localhost    DocumentRoot /var/www/html/federlegno/public            AllowOverride All        ErrorLog ${APACHE_LOG_DIR}/error.log    CustomLog ${APACHE_LOG_DIR}/access.log combined
```

---

### Post by xubuntu84 on 2018-11-28
Since your DocumentRoot is [COLOR=#000000][FONT=&quot]/var/www/html/federlegno/public[/FONT][/COLOR], have you placed an index.html within that directory with www-data:www-data (644 permissions)? 

What errors are you seeing when you visit http://<ip address>/site1 ?
What happens when you go to http://<ip address> ?

---

### Post by volkswagner on 2018-11-28
What you are trying to do, is default behavior for Apache2.

If you simply put your sites as sub directories of the default location /var/www/html/site1, /var/www/html/site2, etc
your plan will work.

Please show us your current setup:
```
ls -l /etc/apache2/sites-available
```
```
cat /etc/apache2/sites-available/000-default
```

Is your server local on your LAN or public on the internet?
If you want the setup to work using your description, you'll want to be sure
to use relative hyperlinks in your website code. This may not work well for
things like Wordpress which always uses fully qualified links.

There are ways around not having a domain name to point to your server.
If you tell us more about your setup, reasons for hosting sites, and who and where
your content will be served, it will help us point you in a sane direction.

---

### Post by jahstation on 2018-11-29
> **xubuntu84 said:**
> Since your DocumentRoot is [COLOR=#000000]/var/www/html/federlegno/public[/COLOR], have you placed an index.html within that directory with www-data:www-data (644 permissions)? 

What errors are you seeing when you visit http://<ip address>/site1 ?
What happens when you go to http://<ip address> ?


[LIST]
[*]yes, in federlegno/public is placed an index.php, and .htaccess that define how my framework (laravel) serve the site
[*]if visit http://<ip address>/site1  (federlegno actually) i see a redirection to  http://<ip address> that show me the site1 homepage.
[*]as I said above  http://<ip address> show me the homepage of federlegno...then i can navigate without problem in the form  http://<ip address>/page1Site1 etc.
[/LIST]


> **volkswagner said:**
> What you are trying to do, is default behavior for Apache2.

If you simply put your sites as sub directories of the default location /var/www/html/site1, /var/www/html/site2, etc
your plan will work.

Please show us your current setup:
```
ls -l /etc/apache2/sites-available
```
```
cat /etc/apache2/sites-available/000-default
```

Is your server local on your LAN or public on the internet?
If you want the setup to work using your description, you'll want to be sure
to use relative hyperlinks in your website code. This may not work well for
things like Wordpress which always uses fully qualified links.

There are ways around not having a domain name to point to your server.
If you tell us more about your setup, reasons for hosting sites, and who and where
your content will be served, it will help us point you in a sane direction.

this thing drive me crazy... so im trying to config the default apache2 behavoir... lool thanks for this little basical tip!

thats a deploy machine, an ovh vpn machine where id like to test and deploy my web apps... so yes is public, but i keep it private. just about few user that will test apps eventually...no big trafic, but yes is on internet!

```
ls -l /etc/apache2/sites-available
```

root@vps503154:~# ls -l /etc/apache2/sites-available
total 20
-rw-r--r-- 1 root root 1332 Jul 27  2017 000-default.conf
-rw-r--r-- 1 root root 6338 Jul 27  2017 default-ssl.conf
-rw-r--r-- 1 root root  300 Nov 28 16:55 laravel.conf
-rw-r--r-- 1 root root  329 Nov 28 16:55 laravel.conf_back

```
cat /etc/apache2/sites-available/000-default
```

root@vps503154:~# cat /etc/apache2/sites-available/000-default.conf 
<VirtualHost *:80>
    # The ServerName directive sets the request scheme, hostname and port that
    # the server uses to identify itself. This is used when creating
    # redirection URLs. In the context of virtual hosts, the ServerName
    # specifies what hostname must appear in the request's Host: header to
    # match this virtual host. For the default virtual host (this file) this
    # value is not decisive as it is used as a last resort host regardless.
    # However, you must set it for any further virtual host explicitly.
    #ServerName [www.example.com]("http://www.example.com")

    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html

    # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
    # error, crit, alert, emerg.
    # It is also possible to configure the loglevel for particular
    # modules, e.g.
    #LogLevel info ssl:warn

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    # For most configuration files from conf-available/, which are
    # enabled or disabled at a global level, it is possible to
    # include a line for only one particular virtual host. For example the
    # following line enables the CGI configuration for this host only
    # after it has been globally disabled with "a2disconf".
    #Include conf-available/serve-cgi-bin.conf
</VirtualHost>


but i think is more usefull:
root@vps503154:~# cat /etc/apache2/sites-available/laravel.conf


<VirtualHost *:80>


    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html/federlegno/public


    <Directory /var/www/html/federlegno>
        AllowOverride All
    </Directory>


    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

---

### Post by volkswagner on 2018-11-29
If you don't want to use name based virtual hosts, there's no need for more than one .conf file. You have multiple conf files but no way for Apache to distinguish. You either need to use hosname directive (name based virtual hosts) or use unique in and/or ports.

You simply need to disable all sites except default. Then you can access you site like [http://ip-address/federlegno/public](http://ip-address/federlegno/public).

In my opinion moving to name based hosts is more robust and simple. Even if you don't own a domain you can modify your client machine's history file to simulate/spoof a DNS entry.

I suggest you read up on name based vHosts vs IP based vHosts and directory based sites.

---

