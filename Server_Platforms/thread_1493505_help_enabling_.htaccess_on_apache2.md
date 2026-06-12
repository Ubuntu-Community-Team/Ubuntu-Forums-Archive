---
title: "help enabling .htaccess on apache2"
date: 2010-05-25
forum: Server Platforms
---

### Post by bayonetblaha on 2010-05-25
I'm trying to install a node for the open-source facebook "appleseed" (opensource.appleseedproject.org). It requires the use of .htaccess, which is disabled in ubuntu server by default.

I changed AllowOverride from None to All in <Directory /> and <Directory /home/nelson/appleseed/> but left the others on None. Now server gives 500 Internal Server Error. Did I go about enabling .htaccess incorrectly?

site file:
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/nelson/appleseed
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /home/nelson/appleseed/>
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

</VirtualHost>

---

### Post by cdenley on 2010-05-26
What error did it log in /var/log/apache2/error.log? What is in the .htaccess file? Does the www-data user have permission to access and read that file?

It is easier to read terminal output or file contents if you put them in "code" tags.
[NOPARSE]
```

my code here

```
[/NOPARSE]

---

### Post by bayonetblaha on 2010-05-26
Thanks for your response.

error.log contains several of these:
```

PHP Notice:  Use of undefined constant E_NONE - a$

```

and this is the .htaccess:
```

#-------LOCAL RULES----------------

#------APPLESEED RULES--------------

# Turn magic quotes off if possible
php_flag magic_quotes_gpc off

# Turn Rewrite Engine On
RewriteEngine On

# Redirect image links

# Redirect main page.
RewriteRule ^$ code/site/main.php [L]

# Redirect the asd network location.
RewriteRule .*^asd\/$ code/site/asd.php [L]

# Redirect the ajax server location.
RewriteRule .*^ajax\/$ code/site/ajax.php [L]

# Redirect the join page
RewriteRule .*^join$ code/site/join.php [L]
RewriteRule .*^join\/$ code/site/join.php [L]
RewriteRule .*^join\/(.*)\/$ code/site/join.php?gVALUE=$1&%1 [L]
RewriteRule .*^join\/(.*)$ code/site/join.php?gVALUE=$1&%1 [L]

# Redirect if user directory is accessed
RewriteRule .*^profile\/$ \/ [R,L]
RewriteCond %{QUERY_STRING} ^([^/]+)
RewriteRule .*^profile\/(.*)\/$ code/user/main.php?gPROFILEREQUEST=$1&%1 [L]
RewriteRule .*^profile\/(.*)$ code/user/main.php?gPROFILEREQUEST=$1&%1 [L]

# Redirect the login page
RewriteRule .*login\/$ code/site/login.php [L]
RewriteRule .*login$ code/site/login.php [L]
RewriteRule .*^login\/bounce\/(.*)$ code/site/bounce.php [L]
RewriteRule .*^login\/bounce$ code/site/bounce.php [L]
RewriteCond %{QUERY_STRING} ^([^/]+)
RewriteRule .*^login\/(.*)\/$ code/site/login.php?gLOGINREQUEST=$1&%1 [L]
RewriteRule .*^login\/(.*)$ code/site/login.php?gLOGINREQUEST=$1&%1 [L]

# Redirect the logout page
RewriteRule .*logout\/$ code/site/logout.php [L]
RewriteRule .*logout$ code/site/logout.php [L]

# Redirect the admin pages
RewriteRule .*^_admin\/$ code/admin/main.php [L]
RewriteRule .*^_admin$ code/admin/main.php [L]
RewriteRule .*^_admin\/config\/$ code/admin/config.php [L]
RewriteRule .*^_admin\/config$ code/admin/config.php [L]
RewriteRule .*^_admin\/users\/$ code/admin/users/main.php [L]
RewriteRule .*^_admin\/users$ code/admin/users/main.php [L]
RewriteRule .*^_admin\/content\/$ code/admin/content/main.php [L]
RewriteRule .*^_admin\/content$ code/admin/content/main.php [L]
RewriteRule .*^_admin\/control\/$ code/admin/control/main.php [L]
RewriteRule .*^_admin\/control$ code/admin/control/main.php [L]
RewriteRule .*^_admin\/groups\/$ code/admin/groups/main.php [L]
RewriteRule .*^_admin\/groups$ code/admin/groups/main.php [L]
RewriteRule .*^_admin\/system\/$ code/admin/system/main.php [L]
RewriteRule .*^_admin\/system$ code/admin/system/main.php [L]

# Redirect the admin subpages
RewriteRule .*^_admin\/users\/access\/$ code/admin/users/access.php [L]
RewriteRule .*^_admin\/users\/access$ code/admin/users/access.php [L]
RewriteRule .*^_admin\/users\/accounts\/$ code/admin/users/accounts.php [L]
RewriteRule .*^_admin\/users\/accounts$ code/admin/users/accounts.php [L]
RewriteRule .*^_admin\/users\/questions\/$ code/admin/users/questions.php [L]
RewriteRule .*^_admin\/users\/questions$ code/admin/users/questions.php [L]

# Admin/System redirects
RewriteRule .*^_admin\/system\/config\/$ code/admin/system/config.php [L]
RewriteRule .*^_admin\/system\/config$ code/admin/system/config.php [L]
RewriteRule .*^_admin\/system\/maintenance\/$ code/admin/system/maintenance.php [L]
RewriteRule .*^_admin\/system\/maintenance$ code/admin/system/maintenance.php [L]
RewriteRule .*^_admin\/system\/logs\/$ code/admin/system/logs.php [L]
RewriteRule .*^_admin\/system\/logs$ code/admin/system/logs.php [L]
RewriteRule .*^_admin\/system\/nodes\/$ code/admin/system/nodes.php [L]
RewriteRule .*^_admin\/system\/nodes$ code/admin/system/nodes.php [L]
RewriteRule .*^_admin\/system\/strings\/$ code/admin/system/strings.php [L]
RewriteRule .*^_admin\/system\/strings$ code/admin/system/strings.php [L]
RewriteRule .*^_admin\/system\/tooltips\/$ code/admin/system/tooltips.php [L]
RewriteRule .*^_admin\/system\/tooltips$ code/admin/system/tooltips.php [L]
RewriteRule .*^_admin\/system\/security\/$ code/admin/system/security.php [L]
RewriteRule .*^_admin\/system\/security$ code/admin/system/security.php [L]
RewriteRule .*^_admin\/system\/options\/$ code/admin/system/options.php [L]
RewriteRule .*^_admin\/system\/options$ code/admin/system/options.php [L]
RewriteRule .*^_admin\/system\/logs\/$ code/admin/system/logs.php [L]
RewriteRule .*^_admin\/system\/logs$ code/admin/system/logs.php [L]

# Admin/Content redirects
RewriteRule .*^_admin\/content\/articles\/$ code/admin/content/articles.php [L]
RewriteRule .*^_admin\/content\/articles$ code/admin/content/articles.php [L]
RewriteRule .*^_admin\/content\/pages\/$ code/admin/content/pages.php [L]
RewriteRule .*^_admin\/content\/pages$ code/admin/content/pages.php [L]

# Admin/Control redirects
RewriteRule .*^_admin\/control\/update\/$ code/admin/control/update.php [L]
RewriteRule .*^_admin\/control\/update$ code/admin/control/update.php [L]

# Security redirects.

# Redirect appleseed data request attempts to 403 Forbidden message.
RewriteRule .*adat$ code/error/403.php [L]

# Redirect utilities 
RewriteRule .*^maintenance\/$ code/site/maintenance.php [L]
RewriteRule .*^maintenance$ code/site/maintenance.php [L]

# Redirect image links

# Go directly to these files, do not process through image.php
RewriteRule .*^photos/.*/profile.jpg$ - [R=302,L]
RewriteRule .*^photos/.*/icons/.*\.gif$ - [L]
RewriteRule .*^photos/.*/icons/.*\.jpg$ - [L]
RewriteRule .*^photos/.*/icons/.*\.png$ - [L]
RewriteRule .*^themes.*\.gif$ - [L]
RewriteRule .*^themes.*\.jpg$ - [L]
RewriteRule .*^themes.*\.png$ - [L]

# Redirect the newswire.
RewriteCond %{QUERY_STRING} ^([^/]+)
RewriteRule .*^news\/(.*)$ code/content/articles.php?gARTICLEREQUEST=$1&%1 [L]
RewriteRule .*^news\/(.*)\/$ code/content/articles.php?gARTICLEREQUEST=$1&%1 [L]
RewriteRule .*^articles\/(.*)\/$ code/content/articles.php?gARTICLEREQUEST=$1&%1 [L]
RewriteRule .*^articles\/(.*)$ code/content/articles.php?gARTICLEREQUEST=$1&%1 [L]

# Redirect the discussion groups
RewriteCond %{QUERY_STRING} ^([^/]+)
RewriteRule .*^group\/(.*)\/$ code/content/group.php?gGROUPREQUEST=$1&%1 [L]
RewriteCond %{QUERY_STRING} ^([^/]+)
RewriteRule .*^group\/(.*)$ code/content/group.php?gGROUPREQUEST=$1&%1 [L]

RewriteCond %{QUERY_STRING} ^([^/]+)
RewriteRule .*^groups\/(.*)\/$ code/content/groups.php?gGROUPSECTION=$1&%1 [L]
RewriteCond %{QUERY_STRING} ^([^/]+)
RewriteRule .*^groups\/(.*)$ code/content/groups.php?gGROUPSECTION=$1&%1 [L]

# Redirect to icon.php for default icon.
RewriteRule .*^icon\/(.*)\/$ code/common/icon.php?gICONUSER=$1 [L]
RewriteRule .*^icon\/(.*)$ code/common/icon.php?gICONUSER=$1 [L]

# Redirect to image.php
RewriteRule .*\.jpg$ code/common/images.php [L]
RewriteRule .*\.gif$ code/common/images.php [L]
RewriteRule .*\.png$ code/common/images.php [L]

# Disallow direct access to index.php after install.
RewriteRule .*index.php$ code/site/main.php [L]

# Redirect Error Documents.
Options +FollowSymlinks -Indexes
ErrorDocument 404 /code/site/redirect.php
ErrorDocument 403 /code/site/error/403.php

#------APPLESEED USER DEFINED REDIRECTS --------------

```

and once again, the site file:
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/nelson/appleseed
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /home/nelson/appleseed/>
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

</VirtualHost>

```

---

### Post by cdenley on 2010-05-26
That error you posted doesn't appear to be related to the 500 response you received. Post the line that corresponds to that error.

Did you enable the rewrite module?
```

sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart

```

---

### Post by bayonetblaha on 2010-05-26
That fixed it! 

Thanks, cdenley, I'll spread the word to other potential ubuntu appleseed hosts.

---

