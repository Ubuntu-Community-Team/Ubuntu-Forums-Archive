---
title: "Redirection using vhost config file to internal ip"
date: 2015-07-13
forum: Server Platforms
---

### Post by ssbattousai on 2015-07-13
Hello,

I configured the the vhost config using proxypass that grabs traffic to a proxy server whenever the url pointing to /wordpress is appended to the server name. 


So mysite.ca -> goes to the first server
and from my proxy setting mysite.ca/wordpress/ -> goes to other server

Original site works fine, mysite.ca


The redirect to the second site is ok at first, mysite.ca/wordpress but the links within them don't seem to work, I've read I need to either change the internal server's links to absolute paths or add more proxypass and proxyreverse for css etc..


Been trying a few different configurations, such as enabling perservehost or rewrite engine, but I seem to be stuck, online resources have gotten me really confused...


Any ideas how to solve this?

Below is my vhost configuration file. 

Server version: Apache/2.2.14 (Ubuntu)


```
ServerName mysite.ca
<VirtualHost *:80>
        ServerAdmin webmaster@localhost


        DocumentRoot /var/www/wordpress
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/wordpress/>
                DirectoryIndex index.php index.html
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>


        Alias /wiki "/var/www/mediawiki"
        <Directory /var/www/mediawiki/>
                DirectoryIndex index.php
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
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
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>




   <IfModule proxy_module>
         <IfModule proxy_http_module>


             # Put this in the main section of your configuration (or desired virtual host, if using Apache virtual hosts)
             ProxyRequests Off
             ProxyPreserveHost On


             <Proxy *>
                   Order deny,allow
                   Allow from all
             </Proxy>


             ProxyPass "/wordpress" "http://192.168.0.104/"
             ProxyPassReverse "/wordpress" "http://192.168.0.104/"






             <Location /wordpress>
                   Order allow,deny
                   Allow from all


                   Require all granted
                   Satisfy Any
                   #Require all granted
                   #Order allow,deny
                   #Allow from all
             </Location>


         </IfModule>
   </IfModule>
</VirtualHost>



```

---

### Post by volkswagner on 2015-07-13
Wordpress expects a certain url and path. Most all links in Wordpress are full http urls, so if you are passing site.com/wordpress
that needs to be configured on wordpress general settings.

So you'll either need to change your document root to /var/www or explicity change the url path in wordpress settings.

Be careful with this. You can easily lock yourself out of the Wordpress gui, so you'll want to have  ssh access to the server.

---

### Post by ssbattousai on 2015-07-14
I tried changing the url path explicitly in the wordpress settings, but it removes all the stylesheets.

I don't think I want to do it this way... right now I can access wordpress fine in localhost, and via my proxy, I think I just have to change a few things in the vhost config...

---

### Post by ssbattousai on 2015-07-14
I edited my xampp vhost back to default




```
 
# Configuring virtual hosts, note that the first declared host is 
# used for all requests that do not match a ##ServerName or 
# ##ServerAlias in any <VirtualHost> block.
 
# let the localhost point to the XAMPP administration webpage


<VirtualHost *:80>
  ServerName localhost
  DocumentRoot "C:/xampp/htdocs"
</VirtualHost>




<VirtualHost *:80>
  ServerName localhost/wordpress
  DocumentRoot "C:/xampp/apps/wordpress/htdocs"
</VirtualHost>

```


 but now I get the error


```

This webpage has a redirect loop


ERR_TOO_MANY_REDIRECTS
ReloadHide details
The webpage at http://mysite.ca/wordpress/sample-page/ has resulted in too many redirects. Clearing your cookies for this site or allowing third-party cookies may fix the problem. If not, it is possibly a server configuration issue and not a problem with your computer.
Learn more about this problem.

```


[http://mysite.ca/wordpress](http://mysite.ca/wordpress) redirects fine however... 


Anyone know how do I should solve this?

---

