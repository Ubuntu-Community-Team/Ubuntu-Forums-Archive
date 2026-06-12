---
title: "Apache - AuthType not set"
date: 2014-04-29
forum: Server Platforms
---

### Post by Trond_Ulseth on 2014-04-29
Totatly new with Linux/Ubuntu/Apache

I've tried setting up a new virtual host with:

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName trondulseth.com
    ServerAlias lab.trondulseth.com
    DocumentRoot /var/vhosts/trondulseth
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/vhosts/trondulseth/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>

```

Trying to go to [http://lab.trondulseth.com/index.html](http://lab.trondulseth.com/index.html) I get an [B]500 Internal Server Error message

[/B]In the error log I see this:

```

[Tue Apr 29 12:28:47 2014] [crit] [client 185.3.3.190] configuration error:  couldn't perform authentication. AuthType not set!: /index.html

```

When I use the default website it is up and running: [http://85.25.194.102/index.html](http://85.25.194.102/index.html)

Here are the default settings for the server:

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost


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

```

Any suggestions as how to get the virtual host up and running?

---

### Post by SeijiSensei on 2014-04-29
> ```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName trondulseth.com
    ServerAlias lab.trondulseth.com
    DocumentRoot /var/vhosts/trondulseth
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/vhosts/trondulseth/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

Remove the <Directory /> stanza.  That should only appear in the default virtual host configuration.

That's the only anomaly I see.  There isn't anything in your configuration that should launch an authentication check requiring the AuthType directive.  Even if there is a stray .htaccess file in /var/vhosts/trondulseth/, it should be ignored by the "AllowOverride None" directive.  Still I'd check and make sure there isn't an .htaccess hiding there.  You can check by running the command "ls -a /var/vhosts/trondulseth".  The "-a" switch will list all files, including "hidden" files that start with a dot like .htaccess.

---

### Post by Trond_Ulseth on 2014-04-29
Thank you. But still not working.

I updated my setting to this:

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName trondulseth.com
	ServerAlias *.trondulseth.com
	DocumentRoot /var/vhosts/trondulseth
	<Directory /var/vhosts/trondulseth/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		Require all granted
	</Directory>
</VirtualHost>

```

The way it is set up on the server is this:

apache2.conf
httpd.conf
sites-available
 - 000-default
 - default
 - default-ssl
 - trondulsethcom
sites-enabled
 - 000-default
 - default-ssl
 - trondulsethcom

(there are some other files and directories there also)

as I can see both the 000-default files and the default file contain the same setup. And I've added my setup to both the trondulsethcom files.

---

### Post by Trond_Ulseth on 2014-04-29
Solved it with this:

```

<Directory /var/vhosts/trondulseth/>
    Satisfy Any
    Allow from all
</Directory>

```

---

