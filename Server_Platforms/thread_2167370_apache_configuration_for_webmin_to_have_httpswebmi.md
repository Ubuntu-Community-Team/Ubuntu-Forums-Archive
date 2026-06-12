---
title: "apache configuration for webmin to have https://webmin.mondomain.com"
date: 2013-08-13
forum: Server Platforms
---

### Post by jmduno on 2013-08-13
Hello,
i wanted to be able to visit webmin on my server with an address who looks like : [https://webmin.*mondomain.com*]("https://webmin.mondomain.com")
(only 80 and 443 are allowed on my company)
I read a lot of tutos for having webmin.mondomain.com but not with https ... It tooks me a couple of hours and i wanted to share.

So the steps to be able to do it :

I assume you have already webmin installed and runnig. (see [http://linuxg.net/how-to-install-webmin-1-6-3-on-ubuntu-13-04-12-10-12-04-debian-wheezy-squeeze/](http://linuxg.net/how-to-install-webmin-1-6-3-on-ubuntu-13-04-12-10-12-04-debian-wheezy-squeeze/))

1)with your domain provider or your local DNS server add a redirect to webmin.*mondomain.com* to you server IP 

2) edit /etc/apacche2/ports.conf and add 
NameVirtualHost *:443

```
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
**    NameVirtualHost *:443**
    Listen 443
</IfModule>


<IfModule mod_gnutls.c>
**    NameVirtualHost *:443**
    Listen 443
</IfModule>
```

Because sometimes you read the comments in some files 
>     # If you add NameVirtualHost *:443 here, you will also have to change    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>

3) Edit :  /etc/apache2/sites-available/default-ssl
and Change 
```
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
```
to 
```
<IfModule mod_ssl.c>
<VirtualHost *:443>

```

So now my default-ssl looks like :
```
<IfModule mod_ssl.c><VirtualHost *:443>
    ServerAdmin webmaster@localhost


    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
...
```



4) Copy /etc/apache2/sites-available/default-ssl to /etc/apache2/sites-available/webmin-ssl

Remove the documentRoot, <Directory /> and <Directory /var/www/>
add 
```
ServerName webmin.mondomain.com

  ProxyRequests Off
  ProxyVia Block

  sslproxyengine On 
  <Proxy *>
    Order deny,allow
    Allow from All
  </Proxy>
  ProxyPass / https://127.0.0.1:10000/
  ProxyPassReverse / https://127.0.0.1:10000/
```

so finally i have :webmin-ssl
```
<IfModule mod_ssl.c><VirtualHost *:443>
    ServerAdmin webmaster@localhost

[B]  ServerName webmin.mondomain.com

  ProxyRequests Off
  ProxyVia Block

  sslproxyengine On 
  <Proxy *>
    Order deny,allow
    Allow from All
  </Proxy>
  ProxyPass / https://127.0.0.1:10000/
  ProxyPassReverse / https://127.0.0.1:10000/[/B]




    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
....

```


5) edit the webmin config : /etc/webmin/config
add ```
product=webmin
referers=127.0.0.1 webmin.mondomain.com
```

and restart webmin
```
sudo service webmin restart
```


6)
enable the mod and site to apache2
```
sudo a2enmod proxy proxy_http proxy_html
sudo a2ensite [COLOR=#000000]webmin-ssl
[/COLOR]sudo service apache2 restart 

```

go to [https://webmin.mondomain.com](https://webmin.mondomain.com) should be ok now.

7) to enable redirection from [http://webmin.mondomain.com](http://webmin.mondomain.com) to [https://webmin.mondomain.com](https://webmin.mondomain.com)
create /etc/apache2/sites-available/webmin
with :
```
<VirtualHost *:80>  ServerName webmin.*mondomain.com*
  redirect permanent / https://webmin.*mondomain.com*
</VirtualHost>
```

activate the redirection and reload apache2
```
sudo a2ensite [COLOR=#000000]webmin
[/COLOR]sudo service apache2 reload
```

Please, feel free to comment. I'm pretty a noob in apache, so i'm scared to have open security hole.

---

### Post by newbie-user on 2013-08-13
Maybe a shortcut to enable ssl on apache:
```
sudo a2enmod ssl
sudo service apache2 restart
```

---

