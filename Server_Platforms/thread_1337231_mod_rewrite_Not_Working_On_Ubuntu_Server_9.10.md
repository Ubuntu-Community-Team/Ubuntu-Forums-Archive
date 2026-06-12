---
title: "mod_rewrite Not Working On Ubuntu Server 9.10"
date: 2009-11-25
forum: Server Platforms
---

### Post by NoSalt on 2009-11-25
Hello All

    I have been pulling my hair out for two days now "attempting" to get mod_rewrite working on Ubuntu Server 9.10 and I was hoping somebody out there could help. What I am, again, "attempting" to do ultimately, is get Bugzilla3 to work, but even a simple rewrite test isn't working.

    In /var/www there is, of course, the index.html file. I created a test file called tmp.html. It is a very simple html file just for a test. Here are the changes I have made to "attempt" to get this to work:

in httpd.conf I have:

```

RewriteEngine On  
RewriteRule ^/$ /tmp.html

```

in sites-enables/000-default I have:

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
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
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

```

When I run a apache2ctl -M I get:

```

Loaded Modules:
 core_module (static)
 log_config_module (static)
 logio_module (static)
 mpm_worker_module (static)
 http_module (static)
 so_module (static)
 alias_module (shared)
 auth_basic_module (shared)
 authn_file_module (shared)
 authz_default_module (shared)
 authz_groupfile_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)
 autoindex_module (shared)
 cgid_module (shared)
 deflate_module (shared)
 dir_module (shared)
 env_module (shared)
 mime_module (shared)
 negotiation_module (shared)
 rewrite_module (shared)
 setenvif_module (shared)
 status_module (shared)
Syntax OK

```

So I know that the rewrite_module is loaded.

F.Y.I., I also changed apache2.conf to:

```

Include /etc/apache2/mods-available/*.load
Include /etc/apache2/mods-available/*.conf

```

to load all of the modules, but that didn't help either. I ran apache2ctl graceful and I am STILL getting the default index.html page. I have cleared caches I have changed browsers but it is the same. It's as if the rewrite isn't even working at all.

Somebody please help!!! This has got to be the most frustrating thing I have ever experienced; and, I haven't even got to fixing Bugzilla3 yet.

Thank you all for reading, have a good day.  :)

---

### Post by Lars Noodén on 2009-11-25
Isn't httpd.conf a legacy from Apache 1.3 and not used for 2.x?

Apache2 uses /etc/apache2/apache2.conf

---

### Post by NoSalt on 2009-11-25
apache2.conf has this line:

```

# Include all the user configurations:
Include /etc/apache2/httpd.conf

```

Plus ... I also made the changes in apache2.conf and it still doesn't work.

---

### Post by NoSalt on 2009-11-25
I forgot to mention that I am getting absolutely **NO** help from the /var/log/apache2/*.log files ... even when set to "debug".

---

### Post by dharrigan on 2009-11-25
Hi,

I've had the same problem. I solved it by moving my:

RewriteEngine On
RewriteRule .......

into the 

<Directory /var/www/>
</Directory>

section in 000-default

Hope this helps!

---

