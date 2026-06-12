---
title: "Apache. Hosting web site on LAN and WAN"
date: 2012-03-12
forum: Server Platforms
---

### Post by tristicles on 2012-03-12
Hi folks. I realise that I'm in the "wrong" place as it's on a Debian Squeeze box. Having said that, I migrated it from an Ubuntu Lucid box, so it's still kinda relevant. Also, the Debian forums are down for maintenance at the moment, so I thought I'd do some investigation here first.

I'm having a problem with an internally hosted web site that's also available to the public.

For this example we'll say the external IP address is 123.45.67.89 and the internal 192.168.10.1.

There's a static-NAT on our filewall, linking the two address which is working fine.

Apache serves the site correctly for internal visitors. However, it's serving the default "It Works!" site for public visitors.

My Apache config file, looks like this:

```
<VirtualHost *:80>
	ServerName	web-site
	ServerAlias	web-site.internal.dns
	DocumentRoot	/data/www/site-root
	DirectoryIndex	index.php index.html index.htm
</VirtualHost>

<VirtualHost 123.45.67.89:80>
	ServerName	web-site.public.dns
	DocumentRoot	/data/www/site-root
	DirectoryIndex  index.php index.html index.htm
</VirtualHost>
```

The same config file worked perfectly for Ubuntu, but Debian doesn't want to play ball. Anyone know if the Ubuntu folks have tweaked apache in any way which could cause this behaviour?

I have tried adding the internal IP address on the first virtual host. Whilst this seemed to work, it then served this site for all the additional internal sites on the box (intranet, etc). Obviously, that's not an option!

---

### Post by tristicles on 2012-03-12
I'll get my coat...!

OK, so the config file wasn't exactly the same. On additional line has fixed it.

```
<VirtualHost *:80>
	ServerName	web-site
	ServerAlias	web-site.public.dns
	ServerAlias	web-site.internal.dns
	DocumentRoot	/data/www/site-root
	DirectoryIndex	index.php index.html index.htm
</VirtualHost>

<VirtualHost 123.45.67.89:80>
	ServerName	web-site.public.dns
	DocumentRoot	/data/www/site-root
	DirectoryIndex  index.php index.html index.htm
</VirtualHost>
```

Not quite sure why adding the public dns alias in the first section works, but there you go. I'm not knocking it!!

Hope this is of use to someone.

---

