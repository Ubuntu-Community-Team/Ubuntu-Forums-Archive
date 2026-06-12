---
title: "Problem with Apache Virtual Named Host"
date: 2010-03-21
forum: Server Platforms
---

### Post by gyzer on 2010-03-21
First off, I'm a total noob when it comes to html and apache.

I have a few problems here

I am running a Ubuntu 9.1 server with Webmin. I was able to setup a simple website that was just listing pictures in directories using Apache's default index. After I renamed the directories within the root directory of the virtual host I was working in, they would no longer show up when I went to the website. I tried several things to fix this, and I even deleted the virtual host and recreated it, but no luck. 

So my first question is, why would those directories disappear when I renamed them?

Now onto my second problem, which might relate to the first.

I have 3 seperate virtual hosts: default, server, and *.homeftp.net (the * is to replace the real name that goes there). When I go to [http://server](http://server) or if I go to [http://*.homeftp.net](http://*.homeftp.net) I get just an empty directory. If I go to [http://server/torrentflux](http://server/torrentflux) (I am running torrent flux on this server, and its directory is under the "server" virtual host) it goes to the login page for torrentf flux, but if I go to [http://*.homeftp.net/torrentflux](http://*.homeftp.net/torrentflux) it also goes to the torrent flux login page. The torrent flux directory is not in the "*.homeftp.net" virtual host. 

So to me, it seems that the named virtual host settings in apache aren't working correctly, or the webmin module for apache isn't working properly. I have found a few instances where Webmin didn't write the correct data to the .conf files. 

Here are some copies of my conf files


**"Server" Named Virtual Host**
```
    ServerAdmin webmaster@localhost

DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
<Directory "/var/www/">
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

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order allow,deny
        Allow from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
ServerName server
```**"*.homeftp.net" Named Virtual Host**
```
ServerName goldsteinfamily.homeftp.net
DocumentRoot /homemedia/www

<Directory /homemedia/www>
     Options +Indexes
     AllowOverride None
     Order allow,deny
     allow from all
</Directory>
```

Any help would be appreciated.

---

### Post by KB1JWQ on 2010-03-22
Check permissions on the directories in your first problem.

For the second one, check the httpd access log and see what it's translating things as; you may need to adjust your config based upon what you find there.

---

