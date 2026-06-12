---
title: "Apache2 VirtualHost setup in 12.04 Server"
date: 2012-08-14
forum: Server Platforms
---

### Post by haldrik on 2012-08-14
I have 12.04 running on a cloud server setup with a single IP address. I currently have two separate domain names pointing to this address. The first one, mysite.net has SSL access (not forced) and the second, myothersite.org, does not have SSL configured. As it stands right now, both sites work fine, and there are no errors reported when Apache starts or restarts. What I am trying to do is to add a few subdomains to the main site (eg: tools.mysite.net), none of which needs SSL access. I've added a short config file (see below) to /etc/apache2/sites-available and run a2ensite and restarted as directed, but I still get a "not found" error when I try to reach the subdomain. (I can still reach mysite.net/tools, but not tools.mysite.net.) 

I have gone through several tutorials and help sites, but nothing seems to work. Below I show the contents of all the relevant files in the hopes that someone will notice the error that prevents the subdomain from being reachable.



Here is the contents of /etc/apache2/sites-available/default:

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName mysite.net:80
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Here is the contents of /etc/apache2/sites-available/default-ssl

<VirtualHost *:443>
        ServerAdmin webmaster@localhost
        ServerName mysite.net:443
        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

        SSLEngine on    
        SSLCertificateFile    /etc/ssl/crt/mysite_net.crt
        SSLCertificateKeyFile /etc/ssl/private/myserver.key
        SSLCertificateChainFile /etc/ssl/crt/mysite_net.ca-bundle
   
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>

  
        BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        # MSIE 7 and newer should be able to use keepalive
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>

Here is the contents of etc/apache2/sites-available/tools. (This should be a subdomain of mysite: tools.mysite.net) It currently causes a "not found" error if I try to access as tools.mysite.net.


<VirtualHost *:80>
    ServerAdmin [email]webmaster@mysite.net[/email]
    ServerName tools.mysite.net
    DocumentRoot /var/www/tools
<Directory /var/www/tools>
Options Indexes FollowSymLinks MultiViews +Includes
AllowOverride all
Order allow,deny
allow from all
</Directory>
</VirtualHost>

Here is the contents of /etc/apache2/sites-available/myothersite.org. 

NameVirtualHost *:80

<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName myothersite.org:80
        DocumentRoot /var/www/othersite
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/othersite>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Here is the contents of /etc/apache2/ports.conf

#NameVirtualHost *:80 (these lines caused errors before.)
#NameVirtualHost *
Listen 80

<IfModule mod_ssl.c>
       NameVirtualHost *:443
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    NameVirtualHost *:443
    Listen 443
</IfModule>


Any help greatly appreciated!

---

### Post by TheFu on 2012-08-14
If you are using name-based virtualhosts, then each different host needs to have a unique name.
[https://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost](https://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost) has examples.

Note that there is no port in the** ServerName** entry part:
```
 ServerName host.example.com
```I think that's where you got it wrong.
You might also want to be certain that your DNS or /etc/hosts files have each of the virtualnames listed.

You can also put the specific hostname into each 
```
<VirtualHost info.domain.com:80> 
```stanza.

---

### Post by haldrik on 2012-08-17
Thanks. It is now working. I might add that another problem that was preventing my subdomains from being accessible was that the default a-record in my dns setup did not have a wildcard * before the domainname, so all subdomain requests were being rejected outright.

---

