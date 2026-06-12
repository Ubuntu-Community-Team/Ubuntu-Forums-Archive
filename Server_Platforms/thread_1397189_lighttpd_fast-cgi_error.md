---
title: "lighttpd fast-cgi error"
date: 2010-02-03
forum: Server Platforms
---

### Post by skaramanger on 2010-02-03
Greetings again,

I get an error message from:

sudo /etc/init.d/lighttpd force-reload

Duplicate config variable in conditional 0 global: fastcgi.server
2010-02-01 10:06:13: (configfile.c.864) source: /etc/lighttpd/lighttpd.conf line: 172 pos: 1 parser failed somehow near here: (EOL)

I did setup lighttpd according to :

[URL=http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html[/URL]

I enabled cgi and fastcgi.  I'm running 9.10 with latest installs from repos.  I'm new to this web server thingy so go easy on me just trying to view web pages I create before uploading them to my online web presence. 

Tia

---

### Post by dmizer on 2010-02-03
> **skaramanger said:**
> Greetings again,

I get an error message from:

sudo /etc/init.d/lighttpd force-reload

Duplicate config variable in conditional 0 global: fastcgi.server
2010-02-01 10:06:13: (configfile.c.864) source: /etc/lighttpd/lighttpd.conf line: 172 pos: 1 parser failed somehow near here: (EOL)

I did setup lighttpd according to :

[URL=http://www.ubuntugeek.com/lighttpd-webserver-setup-with-php5-and-mysql-support.html[/URL]

I enabled cgi and fastcgi.  I'm new to this just trying to view web pages I create before uploading them to my online web presence. Any idea what this message means? Suggestions.

Tia

Please post the relevant lines (surrounding line 172) from your lighttpd.conf file.

---

### Post by skaramanger on 2010-02-04
Here goes,

> **dmizer said:**
> Please post the relevant lines (surrounding line 172) from your lighttpd.conf file.


tail /etc/lighttpd/lighttpd.conf
	#	"/images/" => "/usr/share/images/"
	#)
	$HTTP["url"] =~ "^/doc/|^/images/" {
		dir-listing.activate = "enable"
	}
}
fastcgi.server = (".php" => ((
	"bin-path" => "/usr/bin/php5-cgi",
	"socket" => "/tmp/php.socket"
	)))< line 172 here >


Thankx

---

### Post by dmizer on 2010-02-04
> **skaramanger said:**
> Here goes,




tail /etc/lighttpd/lighttpd.conf
	#	"/images/" => "/usr/share/images/"
	#)
	$HTTP["url"] =~ "^/doc/|^/images/" {
		dir-listing.activate = "enable"
	}
}
fastcgi.server = (".php" => ((
	"bin-path" => "/usr/bin/php5-cgi",
	"socket" => "/tmp/php.socket"
	)))< line 172 here >


Thankx

Remove the last 4 lines (all the fastcgi server stuff).

Activate fastcgi using the lighty-enable-mod script like so:
```
sudo lighty-enable-mod fastcgi
```

Then, restart lighttpd and you will have php support in lighttpd.

---

### Post by skaramanger on 2010-02-05
> **dmizer said:**
> Remove the last 4 lines (all the fastcgi server stuff).

Activate fastcgi using the lighty-enable-mod script like so:
```
sudo lighty-enable-mod fastcgi
```

Then, restart lighttpd and you will have php support in lighttpd.

Hey that did the trick! Thanks. One more thing though Do I still need the use the cgi module? 

skaramanger

This can be marked [solved]

---

### Post by dmizer on 2010-02-05
> **skaramanger said:**
> Hey that did the trick! Thanks. One more thing though Do I still need the use the cgi module? 

skaramanger

This can be marked [solved]

If you've run the lighty-enable-mod command I gave above, then you already have fastcgi enabled. The fastcgi mod is necessary for PHP support.

Glad you're working!

---

