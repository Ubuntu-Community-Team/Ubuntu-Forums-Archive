---
title: "apache cgi exec"
date: 2009-09-14
forum: Server Platforms
---

### Post by redbrain on 2009-09-14
Hey

Having a bad day and for some reason one of my subdomains in apache just broke. Well not broke but it won't execute the cgi script, all it does is offer me to download it:

[http://code.redbrain.co.uk](http://code.redbrain.co.uk)

Its really annoying me i cant see why it is happening my config looks like:

```

<VirtualHost *:80>
	ServerAdmin redbrain@crules.org
	ServerName code.redbrain.co.uk

	ScriptAlias /cgi-bin/ /home/redbrain/cgit/ 
	DocumentRoot /home/redbrain/cgit
	<Directory /home/redbrain/cgit>
	  AllowOverride None
	  Options FollowSymLinks +ExecCGI
	  AddHandler cgi-script .cgi .pl
	  Order allow,deny
	  Allow from all
        </Directory>

	ErrorLog /var/log/apache2/cgit.error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/cgit.access.log combined

</VirtualHost>


```

Thats very messy config i know but i have been doing trail and error with this i don't get any error messages in my logs because it is serving pages from apache's perspective, just its not executing cgi.

Any ideas would be great.

---

