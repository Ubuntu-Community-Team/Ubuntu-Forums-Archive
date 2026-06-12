---
title: "Browser access to folder checked out by svn on apache2?"
date: 2009-06-11
forum: Server Platforms
---

### Post by seeminglee on 2009-06-11
Hi,

**Summary:**
I'm using svn as my version control system to develop a web site, and would like to serve those pages locally so I can see the results and debug more easily. However, it appears that if the DocumentRoot is set to a folder that's a svn checkout, I'll get a 403 Forbidden message. Is there another way around it or must I do an svn export to another folder just so I can see it on the browser?

**Detail:**
Following the the default config provided with a standard apache2 installation, I created two files named smlwwwexport and smlwwwsvn in  and crated symbolic links to both of them in /etc/apache2/sites-enabled

What I put in smlwwwexport:
```

<VirtualHost *:8080>
	ServerAdmin webmaster@localhost

	DocumentRoot /path/to/smlwwwexport
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /path/to/smlwwwexport/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
	
	# the rest of the file truncated for brevity
	# ...

```

What I put in smlwwwsvn:
```

<VirtualHost *:8888>
	ServerAdmin webmaster@localhost

	DocumentRoot /path/to/smlwwwsvn
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /path/to/smlwwwsvn/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
	
	# the rest of the file truncated for brevity
	# ...

```

and then I added the ports into /etc/apache2/ports.conf:
```

NameVirtualHost *:80
Listen 80

NameVirtualHost *:8080
Listen 8080

NameVirtualHost *:8888
Listen 8888

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```

The structures of /path/to/smlwwwsvn and /path/to/smlwwwexport are exactly the same, with the exception that /path/to/smlwwwsvn is a checkout from svn and thus contain hidden files and folders created by svn to version-control whereas /path/to/smlwwwexport is an export so there's no svn stuff inside.

Now when I use my browser to visit [http://localhost:8080](http://localhost:8080), I see my site running as it should be, but visiting [http://localhost:8888](http://localhost:8888), I get a 403 Forbidden. I'm hoping that there is a way around this, or must I do an export or rsync when I'm tweaking css just to see it on my browser?

Help would be much appreciated!

Cheers,
See-ming

---

