---
title: "How to access second virtual host? apache"
date: 2006-06-11
forum: Server Platforms
---

### Post by otis_u on 2006-06-11
Hi!

I've been looking around the forums and a few tutorials around and haven't found the answer to my very very simple question:

How on earth do I actually *access* a second virtual host I added to my apache server?

I've added the host fine and when restarting apache definitely sees it with no problems- I just don't understand how to actually GET THERE in my web browser!

Any help would be greatly appreciated- thanks :D

**edit:**
I was simply trying to make a separate folder public on my server, I achieved what I wanted by creating a symbolic link to the folder in my shared directory, but I'm still interested to learn how these virtual hosts actually work- thanks!

---

### Post by jinacio on 2006-06-12
Well, if it's name-based virtual host, access it by simply opening up a web browser and head to http://<your virtual host>/

Remember, you pc needs to know what ip that domain is pointing to

if it's for private use only, you can edit "/etc/hosts" and add that domain,
example (on local pc, domain is domain.tld)
```

127.0.0.1 domain.tld www.domain.tld mail.domain.tld

```

If it's for internet use, you need to be able to tell the DNS servers for that domain what the ip is.


here's a sample of a name-based virtual host in apache2:
```

<VirtualHost *:80>
  ServerName domain.tld
  ServerAlias www.domain.tld
  DocumentRoot /home/domain.tld/public_html
  ErrorLog /home/domain.tld/logs/error_log
  <Directory /home/domain.tld/public_html>
    Options Indexes IncludesNOEXEC FollowSymLinks
    allow from all
  </Directory>
</VirtualHost>

```

you should also read the apache docs on this.

I hope this answers your question, if not please add more details

cheers,
Joao Inacio

---

### Post by mushr00m on 2006-06-12
your thread solved my questions regarding dual named virtual hosts 

Am I correct in thinking that you want to have two virtual hosts served by a single IP or domain?

This may not be the correct method:
Add another port(ie 10420) to listen to. (for me: /etc/apache2/ports.conf)
```

Listen 10420
```

Then your virtual host settings would be similar to example above except:
```
<VirtualHost *:10420>
```

I think that is it. You would access that virtual host at  xxx.xxx.xxx.xxx:10420  I may be wrong as I'm just working my way through the same problems.

Good Luck,
Mushr00m

---

### Post by LordHunter317 on 2006-06-13
[QUOTE=mushr00m]your thread solved my questions regarding dual named virtual hosts 

Am I correct in thinking that you want to have two virtual hosts served by a single IP or domain?

This may not be the correct method:
Add another port(ie 10420) to listen to. (for me: /etc/apache2/ports.conf)
```

Listen 10420
```

Then your virtual host settings would be similar to example above except:
```
<VirtualHost *:10420>
```

I think that is it. You would access that virtual host at  xxx.xxx.xxx.xxx:10420  I may be wrong as I'm just working my way through the same problems.[/quote]No, this method is totally wrong.  Name-based virtual hosting allows multiple sites to be served from teh same port.  But it requires working hostname resolution, and you must use it.

---

### Post by mushr00m on 2006-06-13
[QUOTE=LordHunter317]No, this method is totally wrong.  Name-based virtual hosting allows multiple sites to be served from teh same port.  But it requires working hostname resolution, and you must use it.[/QUOTE]

I agree the method is wrong for 99.9% of typical server usage.

What if he is accessing his server via localhost? or sandboxed bedhind a NAT?. I know I was scared to release my well researched and configured server into the wilds of the internet, specially when I didn't understand the convention of the first order of XML in the apache2 conf's.  After reading the documentation I felt like adding another host entry to my dyndns account, it doesn't cost anything except a measured reduction in security, and keeping both virtual hosts in the default config file in /etc/apache2/sites-availible did what I needed.  I suspect proper syntax is for each virtual host to have it's own site config in above dir(and enabled with a2ensite tool)

here is my default config file if that helps you otis_u!
```
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@xxxxxx.org
	ServerName somepage.dyndns.com	

	DocumentRoot /var/www
	
	<Directory /> #locks away rootdir! very good thing!
		Options FollowSymLinks
		AllowOverride None
		Deny from all
	</Directory>
	
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order Allow,Deny
		Allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		# RedirectMatch ^/$ /apache2-default/

# Security - Simple Auth for domain

		AuthType Basic
		AuthName "Restricted Files"
		AuthUserFile /usr/share/apache2/passwd/passwd
		Require user xxxxxxxxxxx 
	</Directory>

#	Alias /blog/ /usr/share/wordpress/  #wordpress template entry.
	
#	<Directory /usr/share/wordpress>
#  		Options FollowSymLinks
#  		AllowOverride Limit Options FileInfo
# 		DirectoryIndex index.php
#	</Directory>

# CGI access - unchanged from default

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
	ServerSignature On

</VirtualHost>


<VirtualHost *:80>  #  This is the second virtual host, a friends blog.
#server layout:
#ServerAdmin webmaster@host.example.com  #if you've got a mailserver
#DocumentRoot /www/docs/host.example.com
#ServerName host.example.com
#ErrorLog logs/host.example.com-error_log
#TransferLog logs/host.example.com-access_log
	

	ServerAdmin webmaster@xxxxxxxx.org
	ServerName thisguysblog.dyndns.org

	DocumentRoot /home/xxxxxxxxxx/public_html
	ErrorLog /home/xxxxxxxxxx/logs/error_log
  
	<Directory /> #locks away rootdir! very good thing! (is this redundant?)
		Options FollowSymLinks
		AllowOverride None
		Deny from all
	</Directory>

	<Directory /home/xxxxxxxxxx/public_html>
    		Options Indexes IncludesNOEXEC FollowSymLinks
		AllowOverride All
		allow from all
	</Directory>


</VirtualHost>

```
after a "sudo apache2 -k restart -S" in the terminal I get:

VirtualHost configuration:
wildcard NameVirtualHosts and _default_ servers:
*:80                   is a NameVirtualHost
         default server thisserver.dyn-linux.org (/etc/apache2/sites-enabled/000-default:2)
         port 80 namevhost thisserver.dyn-linux.org (/etc/apache2/sites-enabled/000-default:2)
         port 80 namevhost someguysblog.dyndns.org (/etc/apache2/sites-enabled/000-default:104)
Syntax OK


hope my example of a functioning(if hacked) multiple virtual host served by a single ip and port(http+ssl) helps you figure out a configuration that works for you.

---

### Post by LordHunter317 on 2006-06-13
[QUOTE=mushr00m]What if he is accessing his server via localhost? or sandboxed bedhind a NAT?.[/quote]Doesn't matter.  If you want name-based virtual hosting, it goes on teh same IP and port.  Being on localhost or being accessed through NAT doesn't change the rules.

> , specially when I didn't understand the convention of the first order of XML in the apache2 conf's.Apache doesn't use any XML.

> it doesn't cost anything except a measured reduction in security,There is no security reduction in name-based virtual hosting.  None.

> and keeping both virtual hosts in the default config file in /etc/apache2/sites-availible did what I needed.  I suspect proper syntax is for each virtual host to have it's own site config in above dir(and enabled with a2ensite tool)Yes, it is.

Some notes on your config:[list][*]You shouldn't enable FollowSymLinks globally, most likely.

Don't put your password file in /usr/share.  Don't put anything there unless you must.  That goes in /etc.  Make a directory for it under the apache2 directory, if you feel like it.  Or just stick it directly in /etc/apache2.

Understand the security gain of basic auth over plain text is virtually zero.

---

### Post by mushr00m on 2006-06-14
Lordhunter,

Thanks for the security advice... I spent most of yesterday hardening my LAN but it still has plenty of holes yet.

> Some notes on your config:[list][*]You shouldn't enable FollowSymLinks globally, most likely.

Don't put your password file in /usr/share. Don't put anything there unless you must. That goes in /etc. Make a directory for it under the apache2 directory, if you feel like it. Or just stick it directly in /etc/apache2.

Understand the security gain of basic auth over plain text is virtually zero.

I took out the FollowSymlinks, it was a hack-around that I had in place to solve my original problems.

I thought that /etc/ was for configuration.... which is why I had the passwd file in /usr/share; what is the security ramafications if I leave it where it is?

Basic Auth is fine for this purpose, though I may increase that security later... does auth via mysql offer more protection?

> Apache doesn't use any XML.
Sorry, you are correct.  I should have said that I didn't understand the convention of the <VIRTUALHOST> directive in relation to the NameVirtualHost directive.... and I still don't have my head wrapped around it, even though my server is running great.

> Doesn't matter. If you want name-based virtual hosting, it goes on teh same IP and port. Being on localhost or being accessed through NAT doesn't change the rules.

Are we sure otis_u wants name-based virtual hosting?  I found a supported single IP/multiple port setup in the Apache2 documentation in the Virtual Host Examples area, [http://httpd.apache.org/docs/2.0/vhosts/examples.html#port]("http://httpd.apache.org/docs/2.0/vhosts/examples.html#port"), so I am comfortable in standing by my earlier comments.

That said, I finally understand what adding entries to the /etc/hosts file will do for the local name resolution(first line in /etc/host.conf--> "order hosts,bind); I feel like I'm stuffing my head through a pinhole.

Thanks for the ideas Jinacio and LordHunter

mushr00m.

---

### Post by LordHunter317 on 2006-06-14
> **mushr00m]I thought that /etc/ was for configuration....[/quote]It is, passwords are clearly a configuration item.

> which is why I had the passwd file in /usr/share said:**
> There aren't any security ramifications per se if the file is properly secured.  But the point is you're not supposed to put anything in /usr/share in the first place

[quote]Basic Auth is fine for this purpose, though I may increase that security later... does auth via mysql offer more protection?No.  Where the passwords are stored has nothing to do with the protection offered.  You'd still be doing basic authentication.  Digest is more secure, but limits what clients can see the site.

The right solution is to setup and use SSL.

[quote]Sorry, you are correct.  I should have said that I didn't understand the convention of the <VIRTUALHOST> directive in relation to the NameVirtualHost directive.... and I still don't have my head wrapped around it, even though my server is running great.You should supply a NameVirtualHost directive for every Listen directive you want to do name-based virtual hosting on (and the NameVirtualHost should really go with them).  You then provide the same value in the <VirtualHost> host section.

It's worth noting to ensure a reliable configuration, the three should match perfectly.  IOW, if Listen says *:80 or 80, then NameVirtualHost should say *:80 and the VirtualHost sections the same.

It's possible to multi-home a VirtualHosted site, but not really recommended unless you know exactly what you're doing.

> Are we sure otis_u wants name-based virtual hosting?That's what 99% of people want, so I'm comfortable in that, yes.

---

