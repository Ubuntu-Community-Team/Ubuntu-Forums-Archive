---
title: "Apache2 cgi-bin perl internal server error"
date: 2005-07-19
forum: Server Platforms
---

### Post by Ian Fleeton on 2005-07-19
It started well - I used Synaptic to install apache2, vsftpd, php and perl and it's all mostly working.

However I'm now stuck with Internal Server Errors (500) whenever I try to view a Perl script.

I've done the following (with help from other posts here):

Made a new virtual site /etc/apache2/sites-enabled/euroguns

Added euroguns to /etc/hosts

Successfully viewed files in a browser [http://euroguns/index.php](http://euroguns/index.php) (/home/ian/euroguns/httpdocs/index.html)

Created /home/ian/euroguns/cgi-bin/ with 755 as permissions

Created /home/ian/euroguns/cgi-bin/test.pl using kate and set 755 for permissions

```
 #!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hello, World.";
```

Noticed that mod-perl is mentioned in the apache signature and there are perl symlinks from /etc/apache2/mod-enabled/ to /etc/apache2/mods-available/

Tested the script on the command line - runs fine

Changed the ScriptAlias in the new virtual host file which I copied from the default (below)

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName euroguns
	DocumentRoot /home/ian/euroguns/httpdocs/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/ian/euroguns/httpdocs/>
		Options Indexes FollowSymLinks MultiViews +ExecCGI
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /home/ian/euroguns/cgi-bin/
	<Directory "/home/ian/euroguns/cgi-bin/">
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

Added ```
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
``` to apache2.conf, as well as ```
AddHandler cgi-script .pl
```

If I view the script, or even a non-script, inside the cgi-bin I get 500 Internal Server Error in the browser and "Premature end of script headers: test.pl" errors showing up in error.log

Any ideas?

Thanks,
Ian

---

### Post by sunwave on 2005-07-27
[QUOTE=Ian Fleeton]It started well - I used Synaptic to install apache2, vsftpd, php and perl and it's all mostly working.

However I'm now stuck with Internal Server Errors (500) whenever I try to view a Perl script.

I've done the following (with help from other posts here):

Made a new virtual site /etc/apache2/sites-enabled/euroguns

Added euroguns to /etc/hosts

Successfully viewed files in a browser [http://euroguns/index.php](http://euroguns/index.php) (/home/ian/euroguns/httpdocs/index.html)

Created /home/ian/euroguns/cgi-bin/ with 755 as permissions

Created /home/ian/euroguns/cgi-bin/test.pl using kate and set 755 for permissions

```
 #!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hello, World.";
```

Noticed that mod-perl is mentioned in the apache signature and there are perl symlinks from /etc/apache2/mod-enabled/ to /etc/apache2/mods-available/

Tested the script on the command line - runs fine

Changed the ScriptAlias in the new virtual host file which I copied from the default (below)

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName euroguns
	DocumentRoot /home/ian/euroguns/httpdocs/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/ian/euroguns/httpdocs/>
		Options Indexes FollowSymLinks MultiViews +ExecCGI
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /home/ian/euroguns/cgi-bin/
	<Directory "/home/ian/euroguns/cgi-bin/">
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

Added ```
<Files ~ "\.pl$">
Options +ExecCGI
</Files>
``` to apache2.conf, as well as ```
AddHandler cgi-script .pl
```

If I view the script, or even a non-script, inside the cgi-bin I get 500 Internal Server Error in the browser and "Premature end of script headers: test.pl" errors showing up in error.log

Any ideas?

Thanks,
Ian[/QUOTE]
 Please post the error-log from /var/log/apache2/error.log (last few entries)
or if you've an Server specific Apache2-Error log, the one from your Server (Eurogun)

Have you installed mod_perl try the following entry:

<Files ~ "\.(pl)$">
         SetHandler perl-script
         PerlHandler ModPerl::Registry
         Options +ExecCGI
</Files>

---

### Post by greymoose58 on 2006-08-07
Hi Ian,

I just sorted out the same problem with a .cgi file after reinstalling my Apache2 server. I don't know if your problem is caused by the same thing but it's worth a go. I got error 500 because I didn't have a CGI module loaded that the script called for. Once I sorted that out it was all go.

Cheers.

---

