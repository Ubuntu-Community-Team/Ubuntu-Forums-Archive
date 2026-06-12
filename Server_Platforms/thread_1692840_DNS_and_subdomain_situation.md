---
title: "DNS and subdomain situation"
date: 2011-02-22
forum: Server Platforms
---

### Post by crazyness003 on 2011-02-22
Hi everyone. I have a particularly weird situation and was wondering if what im trying to do is even possible. If so, how?

Im running an apache2 server from home and purchased webspace hosted by a provider. Of the domain I have, being hosted by my provider, I have a subdomain thats forwarded to my home IP. But when I go there, it resloves to my IP address instead of staying as a subdomain (does that even make sense?)

EXAMPLE: Through 1and1.com hosting, I own [http://example.com](http://example.com). At home, im hosting my own site from my IP [http://123.456.789](http://123.456.789).

Can I get [http://home.example.com](http://home.example.com) to not just forward to 123.456.789, but actually become the address of my IP? 

Im not too sure how DNS and all the other stuff works, and im terribly sorry if I posted in the wrong forum, but ANY pointers would be appreciated.

Right now, so far, i changed my /etc/hosts file to substitute my ip with the subdomain address, but it only works on my local machine. so locally, home.example.com works. but anywhere else, it resolves to my IP address.

---

### Post by volkswagner on 2011-02-22
Does this happen if you are outside your LAN?  If it works properly outside your LAN, it may be an issue with your router or apache settings.

What type of record did you set for your DNS at your hosting site?  Was it an "A Record"?

What does your virtual host file look like and also your index.html or similar?

---

### Post by crazyness003 on 2011-02-22
> **volkswagner said:**
> Does this happen if you are outside your LAN?  If it works properly outside your LAN, it may be an issue with your router or apache settings.
No, outside my LAN, when I go to [http://subdomain.example.com](http://subdomain.example.com), i have it forwarded to my IP, and it resolves to my IP, so it doesnt keep the subdomain.example.com address. Instead it reverts to 123.456.789.

> **volkswagner said:**
> What type of record did you set for your DNS at your hosting site?  Was it an "A Record"?
Ok. This is the part that has been bothering me. For subdomains on my hosting site, i can only change the root directory or a forwarding address. I have no clue where to mess with any records. If you can give me pointers on that, i'd appreciate it.

> **volkswagner said:**
> What does your virtual host file look like and also your index.html or similar?
Well, I used whatever examples i can to compile them. Along with the defaults.

Heres an example of what it looks like (addresses and certain records have been changed for privacy issues)

```
<VirtualHost *:80>
	ServerAdmin email@gmail.com
	ServerName home.example.com
	ServerAlias www.home.example.com *.home.example.com

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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

I also have an SSL enabled vhost, that has same directives plus the mod_ssl settings.

My index is a simple html document right now, with nothing special. Im not sure if it has to do with anything. It is being hosted from home though, not my hosting company.

In the future I plan to use my home server to host needed documents online, of course I'll do this as soon as i can learn more about security and authentication.

Anyway, thanks for the reply, and interest to help me.

---

### Post by crazyness003 on 2011-02-22
> **volkswagner said:**
> ...What type of record did you set for your DNS at your hosting site?  Was it an "A Record"?...
Ok, so I got curious, and there's a way to change the A record for a subdomain. And I did. All I have to do is test it with a machine outside my network. 

[[[testing out with my mobile phone over carrier network]]]

Sweet success!!! Wow, had I know it was that easy... I wouldn't have bothered you.

Thank you very much!!! I would hit that Thank You button...but it was removed a while ago. Thanks anyway.

---

