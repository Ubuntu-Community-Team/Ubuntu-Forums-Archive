---
title: "SSL not working on 7.04"
date: 2007-07-02
forum: Server Platforms
---

### Post by PopcornEaterMan on 2007-07-02
I'm trying to get SSL working in 7.04
I followed the instructions here: 
[https://help.ubuntu.com/7.04/server/C/httpd.html](https://help.ubuntu.com/7.04/server/C/httpd.html)

after attempting the restart, I am getting the error:

```
 * Forcing reload of web server (apache2)... 
 Syntax error on line 8 of /etc/apache2/sites-enabled/000-default: 
 SSLOptions: Illegal option 'CompatEnvVars'                                     
                                                          [fail]



```
                                                                     
What am I doing wrong?

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	SSLEngine on

	SSLOptions +FakeBasicAuth +ExportCertData +CompatEnvVars +StrictRequire

	SSLCertificateFile /etc/ssl/certs/server.crt
	SSLCertificateKeyFile /etc/ssl/private/server.key
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

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

---

### Post by duckmannz on 2007-07-04
A quick google for " SSLOptions: Illegal option 'CompatEnvVars'" shows:

[http://www.apache.org/dist/httpd/CHANGES_2.2](http://www.apache.org/dist/httpd/CHANGES_2.2)

  *) mod_ssl: Drop support for the CompatEnvVars argument to
     SSLOptions, which was never actually implemented in 2.0.
     [Joe Orton]

Just remove the option.

---

