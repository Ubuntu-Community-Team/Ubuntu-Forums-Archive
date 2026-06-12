---
title: "AWstats and apache redirect"
date: 2011-04-05
forum: Server Platforms
---

### Post by Viruk on 2011-04-05
I have set up awstats on a test server and it is working successfully. Currently to access the stats the following address has to be used: 
[http://server/awstats/awstats.pl?config=config-name](http://server/awstats/awstats.pl?config=config-name)

I would like to simplify this so that just using [http://server/awstats](http://server/awstats) redirects to [http://server/awstats/awstats.pl?config=config-name](http://server/awstats/awstats.pl?config=config-name)

I am running Ubuntu server 10.04 and the LAMP stack is set up from the option in the Ubuntu installer. 
The only change I have tried to make to the modules from default is a2enmod rewrite, however the output of apache2ctl -l did not change after running this command.

I am looking at the file /etc/apache2/sites-available/default config file 
I think I need something like the following:

ScriptAlias /awstats/ /usr/local/awstats/wwwroot/cgi-bin/awstats.pl?config=config-name
      <Directory "/usr/local/awstats/wwwroot/cgi-bin/">
            AllowOverride None
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Order allow,deny
            Allow from all
      </Directory>

So not only do I want a particular perl script to be run, I want a particular config file passed to it, but I'm not sure I can do that with scriptalias as all I have managed to do so far is stop my original working path ([http://server/awstats/awstats.pl?config=config-name](http://server/awstats/awstats.pl?config=config-name)) from working at all.

Can anyone point me in the right direction please?

---

### Post by Viruk on 2011-04-05
I have had some help from elsewhere so I don't take the credit for this, but I'm posting the resolution on here in case its useful to anyone else.

The original suggestion was adding the following to /etc/apache2/sites-available/default 
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteRule ^/awstats$ /usr/local/awstats/wwwroot/cgi-bin/awstats.pl?config=config-name
</IfModule> 

However, I wanted both [http://server/awstats](http://server/awstats) and [http://server/awstats/](http://server/awstats/) to redirect to the same place. Also the original redirect was giving me the awstats file to download rather than running the script. 

Ultimately the following worked for me:

# redirect for awstats
	<IfModule mod_rewrite.c>
		RewriteEngine on
		RewriteRule ^/awstats$ /awstats/
		RewriteRule ^/awstats/$ /awstats/awstats.pl?config=config-name [R]

	</IfModule>

---

### Post by Viruk on 2011-04-05
Aditionally I've just spotted this. 

The RewriteRule needs to be to /awstats/ instead of /usr/local/awstats/wwwroot/cgi-bin/ because the install script for awstats already created the following entry in httpd.conf 

```
ScriptAlias /awstats/ "/usr/local/awstats/wwwroot/cgi-bin/"
```

---

