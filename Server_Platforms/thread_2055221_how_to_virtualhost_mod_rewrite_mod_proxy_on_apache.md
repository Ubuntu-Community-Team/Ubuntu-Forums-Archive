---
title: "how to virtualhost mod_rewrite mod_proxy on apache2 + tomcat - java server"
date: 2012-09-08
forum: Server Platforms
---

### Post by 007casper on 2012-09-08
how to virtualhost mod_rewrite mod_proxy on apache2 + tomcat - java server

I am running on tomcat server that has webapps listening on 8080

I would like to host these webapps on different domains. 

For example, if the public virtual host is [www.foobar.com](www.foobar.com) and the friendly URL is /foobar, then [www.foobar.com](www.foobar.com) is mapped to [http://www.hostdomain.com/dir/foobar](http://www.hostdomain.com/dir/foobar)

**How can I achieve this?**

I have tried several things without success.

I was thinking I should have server to 
1 - Grab the wild subdomain from the domain
2 - Make sure the subdomain is not www, w or ww
3 - Check if the directory actually exists on "www.domain.com" before rewrite
4 - if the directory doesnt exist it stays as wild domain
5 - Finally, if the directory exist the actual rewrite

I couldnt make it work with mod_rewrite alone.  I have been looking into mod_proxy, mod_proxy_ajp, and mod_rewrite


```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName [www.domain.com](www.domain.com)
	ServerAlias [www.domain.com](www.domain.com) domain.com *.domain.com
	RedirectPermanent / [http://www.domain.com](http://www.domain.com)
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
	<IfModule mod_rewrite.c>	
                Options +FollowSymLinks
                Options +Indexes

                RewriteEngine On
                RewriteBase /

                # Prevent looping this rule
                RewriteCond %{ENV:REDIRECT_STATUS} !200
                RewriteCond %{HTTP_HOST} !www.domain.com$ [NC]
                RewriteCond %{HTTP_HOST} ^(www\.)?([a-z0-9.-]+).domain.com$ [NC]
                RewriteRule (.*) /%2/$1 [L]

                # change the "." in the path to "/"
                RewriteRule ^(.*)\.(.*)/(.*)$ /$1/$2/$3 [L]

                #redirect domain.com to [www.domain.com](www.domain.com)
                RewriteCond %{HTTP_HOST} !^domain\.com$ [NC]
                RewriteRule ^ http://www.domain.com%{REQUEST_URI} [R=301,NC]	
	</IfModule>	
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
	<Proxy *>
	Order deny,allow
	Allow from all
	</Proxy>

#	ErrorLog /var/log/apache2/foobar_error.log
#	LogLevel warn
#	CustomLog /var/log/apache2/foobar_access.log combined
	
	ProxyPass / ajp://localhost:8009/
	ProxyPassReverse / ajp://localhost:8009/

#	ProxyPass        /user/ [http://localhost:8080/user/foobar/](http://localhost:8080/user/foobar/)
#	ProxyPassReverse /user/ [http://localhost:8080/user/foobar/](http://localhost:8080/user/foobar/)

#	ProxyPass        /foobar/ [http://localhost:8080/web/foobar/](http://localhost:8080/web/foobar/)
#	ProxyPassReverse /foobar/ [http://localhost:8080/web/foobar/](http://localhost:8080/web/foobar/)

#	ProxyPass        / [http://localhost:8080/web/foobar/](http://localhost:8080/web/foobar/)
#	ProxyPassReverse / [http://localhost:8080/web/foobar/](http://localhost:8080/web/foobar/)

</VirtualHost>
```

---

### Post by nothingspecial on 2012-09-10
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2012-09-10
> **007casper said:**
> For example, if the public virtual host is [www.foobar.com](www.foobar.com) and the friendly URL is /foobar, then [www.foobar.com](www.foobar.com) is mapped to [http://www.hostdomain.com/dir/foobar](http://www.hostdomain.com/dir/foobar)

**How can I achieve this?**

If you don't mind that [www.hostdomain.com/dir/foobar](www.hostdomain.com/dir/foobar) appears in the address bar, then you can just use simple redirects in Apache:

```

<VirtualHost *:80>
     ServerName     www.foobar.com
     ServerAlias    foobar.com <=optional

     Redirect / http://www.hostdomain.com/dir/foobar
</VirtualHost>

```

---

### Post by HugoSerrano on 2012-09-10
Hello!

I'm not a big user of Tomcat. I remember i did something related with that. Had to use something called workers.

Try to see if this helps you:
[http://blog.tele-lab.org/2010/03/configuring-apache2-and-tomcat6-with-virtual-hosts/](http://blog.tele-lab.org/2010/03/configuring-apache2-and-tomcat6-with-virtual-hosts/)

Regards!

---

