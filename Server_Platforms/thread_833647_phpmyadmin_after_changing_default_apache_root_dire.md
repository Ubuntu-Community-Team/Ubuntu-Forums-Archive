---
title: "phpmyadmin after changing default apache root directory"
date: 2008-06-18
forum: Server Platforms
---

### Post by usfish on 2008-06-18
Hi all, 

At first i installed apache, mysql and phpmyadmin. then I changed apache root directory to something else( say, home/me/www/ ), so apparently phpmyadmin doesn't work any more. but how should I configure it again?

I tried to uninstall phpmyadmin, and install it again. but seems apa-get remove does not work well, because there is still a /phpmyadmin directory in /etc. and a /phpmyadmin directory is still in /var/www/

so if I install it again, there is still no new phpmyadmin directory in home/me/www/  

is there any way to solve this problem? Thanks!!

---

### Post by doogy2004 on 2008-06-18
nothing has changed, phpmyadmin aliases in apache.

```
http://hostname/phpmyadmin
```

will still map to the proper directory, unless you moved phpmyadmin from its default installed directory to /var/www

---

### Post by usfish on 2008-06-18
> **doogy2004 said:**
> nothing has changed, phpmyadmin aliases in apache.

```
http://hostname/phpmyadmin
```

will still map to the proper directory, unless you moved phpmyadmin from its default installed directory to /var/www

Thank you for your reply, 

but what I get is 
The requested URL /phpmyadmin was not found on this server.

I didn't change anything, but there has always been a /phpmyadmin directory under /var/www in the server. 

The following is found in /etc/phpmyadmin/apache.conf file, I think it somewhat implies that it is still tied to /var/www/ directory. 

```

# Configure everything with /etc/phpmyadmin/htaccess file

<Directory /usr/share/phpmyadmin/>
    AllowOverride All
</Directory>

<Directory /var/www/phpmyadmin/>
    AllowOverride All
</Directory>

# Configure everything with /etc/phpmyadmin/htaccess file

<Directory /usr/share/phpmyadmin/>
    AllowOverride All
</Directory>

<Directory /var/www/phpmyadmin/>
    AllowOverride All
</Directory>


# Protect some directories

<Directory /var/lib/phpmyadmin/>
    Options -FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

<Directory /usr/share/phpmyadmin/config/>
    Options -FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

<Directory /var/www/phpmyadmin/config/>
    Options -FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>
# Configure everything with /etc/phpmyadmin/htaccess file

<Directory /usr/share/phpmyadmin/>
    AllowOverride All
</Directory>

<Directory /var/www/phpmyadmin/>
    AllowOverride All
</Directory>


# Protect some directories

<Directory /var/lib/phpmyadmin/>
    Options -FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

<Directory /usr/share/phpmyadmin/config/>
    Options -FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

<Directory /var/www/phpmyadmin/config/>
    Options -FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>




```

---

### Post by doogy2004 on 2008-06-18
what version of ubuntu are you running, I'm using 8.04 LTS and when you install phpmyadmin it places its files in /usr/share/phpmyadmin and it places a configuration file for apache at /etc/apache2/conf.d/phpmyadmin.conf with the following contents
```
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	# Authorize for setup
	<Files setup.php>
	    # For Apache 1.3 and 2.0
	    <IfModule mod_auth.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    # For Apache 2.2
	    <IfModule mod_authn_file.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    Require valid-user
	</Files>
	<IfModule mod_php4.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
</Directory>

```

the contents of my /etc/phpmyadmin/apache.conf is
```
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	# Authorize for setup
	<Files setup.php>
	    # For Apache 1.3 and 2.0
	    <IfModule mod_auth.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    # For Apache 2.2
	    <IfModule mod_authn_file.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    Require valid-user
	</Files>
	<IfModule mod_php4.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
</Directory>

```

---

### Post by usfish on 2008-06-18
> **doogy2004 said:**
> what version of ubuntu are you running, I'm using 8.04 LTS and when you install phpmyadmin it places its files in /usr/share/phpmyadmin and it places a configuration file for apache at /etc/apache2/conf.d/phpmyadmin.conf with the following contents
```
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	# Authorize for setup
	<Files setup.php>
	    # For Apache 1.3 and 2.0
	    <IfModule mod_auth.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    # For Apache 2.2
	    <IfModule mod_authn_file.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    Require valid-user
	</Files>
	<IfModule mod_php4.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
</Directory>

```

the contents of my /etc/phpmyadmin/apache.conf is
```
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
	Options Indexes FollowSymLinks
	DirectoryIndex index.php

	# Authorize for setup
	<Files setup.php>
	    # For Apache 1.3 and 2.0
	    <IfModule mod_auth.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    # For Apache 2.2
	    <IfModule mod_authn_file.c>
		AuthType Basic
		AuthName "phpMyAdmin Setup"
		AuthUserFile /etc/phpmyadmin/htpasswd.setup
	    </IfModule>
	    Require valid-user
	</Files>
	<IfModule mod_php4.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
	<IfModule mod_php5.c>
		AddType application/x-httpd-php .php

		php_flag magic_quotes_gpc Off
		php_flag track_vars On
		php_flag register_globals Off
		php_value include_path .
	</IfModule>
</Directory>

```


I am not sure, I am using SSH to access a remote machine. 

my /etc/apache2/conf.d/ has only one file called "charset"

Thank you all the same.

---

### Post by doogy2004 on 2008-06-18
you can find the version using
```
lsb_release -a
```
or ```
sudo lsb_release -a
```

---

### Post by usfish on 2008-06-18
> **doogy2004 said:**
> you can find the version using
```
lsb_release -a
```
or ```
sudo lsb_release -a
```

I don't have this command seemlingly..

 I just contacted the web master and learned that it is a Debian server.... sorry, though I used to think ubuntu is based on debian so it should be kind of the same thing. 

thank you though. :)

---

### Post by doogy2004 on 2008-06-18
ubuntu is based on debian, however there are still many difference in where things are placed/configured

---

