---
title: "apache2 location &amp; proxy"
date: 2009-02-07
forum: Server Platforms
---

### Post by ensis2k on 2009-02-07
Hi

I'd like to proxy a location in apache2 through to another webserver running on another port. How can I do that?

I tried adding a file named "citadel" to the /etc/apache2/sites-available folder.
```

<Location /citadel>
    ProxyPass http://127.0.0.1:2000/
    ProxyPassReverse http://127.0.0.1:2000/
</Location>

```
Then I executed "a2ensite citadel" and restarted apache.

Unfortunately this does not seem to work as expected. [http://myserver/citadel](http://myserver/citadel)

Edit:
The other server runs fine on port 2000. And apache runs fine on port 80.

---

### Post by peter72 on 2009-02-07
Try this:

```


<Virtualhost *:80>
ProxyRequests On
ProxyTimeout 120
ProxyPass /citadel/ http://127.0.0.1:2000/
ProxyPassReverse /citadel/ http://127.0.0.1:2000/
</Virtualhost>


```

You'll also have to make sure mod_proxy module is enabled.

---

### Post by ensis2k on 2009-02-08
Thank you, but it still does not work.


Maybe it does not work because i have two sites on "<VirtualHost *:80>" ???  I have enabled the "default" site which has been customized by me some time ago.
Here comes "default":
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options -Indexes FollowSymLinks MultiViews
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
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```


mod_proxy was already enabled but maybe other modules are preventing something?
```

/etc/apache2/mods-enabled$ ls
actions.load          authz_user.load  deflate.load      php5.conf        ssl.conf
alias.conf            autoindex.conf   dir.conf          php5.load        ssl.load
alias.load            autoindex.load   dir.load          proxy.conf       status.conf
auth_basic.load       cgi.load         env.load          proxy.load       status.load
authn_file.load       dav.load         mime.conf         proxy_http.load
authz_default.load    dav_svn.conf     mime.load         python.load
authz_groupfile.load  dav_svn.load     negotiation.conf  setenvif.conf
authz_host.load       deflate.conf     negotiation.load  setenvif.load

```

---

### Post by ensis2k on 2009-02-12
Bump

Any ideas?

---

### Post by conjur3r on 2009-02-12
Can you also include the config about your proxy?

---

### Post by RealPSL on 2009-02-12
What you need is a new virtual host. A combination of both the answers above should do it with a couple of additional steps.

```

<Virtualhost *:80>
  ServerName myserver.example.org
  ServerAlias myserver
  ProxyRequests On
  ProxyTimeout 120
  <Location /citadel>
    ProxyPass http://127.0.0.1:2000/
    ProxyPassReverse http://127.0.0.1:2000/
    Order allow,deny
    Allow from all
  </Location>
</Virtualhost>

```

Note that the ServerName and ServerAlias lines above are very important this is how apache knows to send the requests to this server and not to the default server.

Check the configuration with ```
 sudo apache2ctl configtest
```

Enable the site with ```
sudo a2ensite citadel
```
Enable the modules with ```
sudo a2enmod proxy; sudo a2enmod proxy_http
```

Restart apache with ```
sudo /etc/init.d/apache2 restart
```

Note that the above configuration could be cleaner by including ifmodule statements.

---

