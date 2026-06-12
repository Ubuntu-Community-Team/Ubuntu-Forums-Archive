---
title: "Apache2 and name-based virtual host."
date: 2007-06-17
forum: Server Platforms
---

### Post by Levander on 2007-06-17
On my LAN, I've set up bind9 so that my machine named louis and another one named kb, which I want to use as a virtual host in apache2 both, resolve to the same IP.  When a user goes to [http://kb/](http://kb/) on my LAN, I want the user to be forwarded to the instiki application (a wiki written in Ruby)  running on louis.

Instiki is up and running successfully on my machine.  When I go to [http://louis:2500/kb](http://louis:2500/kb), I do get my wiki.  I've tried setting up a virtual host in the apache config for instiki, but when the user opens up [http://kb/](http://kb/) in his browser, he just gets the DocumentRoot of louis.

How do I get [http://kb/](http://kb/) forwarded to [http://louis:2500/kb/](http://louis:2500/kb/) in my apache config on louis?

The only two files in my /etc/apache2/sites-enabled directory are named 000-default and instiki.

Here's the initiki:

```

<Virtualhost *>
    ServerName kb.highhat.net
    ProxyPass / http://localhost:2500/kb/
    ProxyPassReverse / http://localhost:2500/kb/
</Virtualhost>

```

Here's 000-default.  I thnk it's just a standard file written by the Ubuntu installation/upgrade procedure:

```

NameVirtualHost *

<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
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

### Post by MJN on 2007-06-18
There's no need for the proxying, instead try this (as a minimum):
 
```

<Virtualhost *>
    ServerName kb.highhat.net
    DocumentRoot /location/of/wiki/
</Virtualhost>
```
 
The 000-default file is, as you say, the default config file for virtual hosts - it might be worth you adding the above to it and changing the first VirtualHost section to [i]your[/i/ default site (which, by the sounds of it, isn't the wiki). Note that the first VirtualHost container will be the one used if no name-match (as per the ServerName directives) is found.
 
Mathew

---

### Post by Levander on 2007-06-18
Okay thanks.  I do need the ProxyPass because the wiki isn't just a bunch of HTML pages.  It's an application written on Rails that needs it's own runtime environment.  It may be possible to have Apache act as a container for this runtime environment, but you can't just use DocumentRoot to do that.

It turned out one of the problems was that I only had a named virtual host for "kb.highhat.net", but was trying to open up "kb" in my browser.  This resulted in a no name-match and so I was getting the default virtual host in 000-default, as you mention above.

Opening up kb.highhat.net in my browser gets around this problem.  I've also now added a ServerAlias in the apache config so that I can just open up kb in my browser.

Then, I had enabled mod_proxy, but hadn't enabled mod_proxy_http (I didn't know mod_proxy_http existed until this).  Lastly, I had to edit /etc/apache2/mods-enabled/proxy.conf.  Ubuntu ships such that after you enabled mod_proxy, the configuration still has all proxy turned off in that config file.  

Now it works.

---

