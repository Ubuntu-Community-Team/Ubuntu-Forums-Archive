---
title: "Trouble setting up a VirtualHost on Apache (Debian)"
date: 2011-08-27
forum: Server Platforms
---

### Post by kenquad on 2011-08-27
I have a web development box on my network called webdev.local.  Up to now I have been accessing the dev versions of my sites at webdev.local/site1, webdev.local/site2 etc.  However, for certain reasons that aren't relevant to this question, I now need to set up a new virtual host, site1.local, to point to a particular site on the server.  Here is what I've done so far.

First, I created site1.local under /etc/apache2/sites-available, with the following content:

```

<VirtualHost site1.local>
   ServerAdmin webmaster@localhost
   DocumentRoot /var/www/site1
   CustomLog /var/log/apache2/site1.local.log combined
</VirtualHost>

```

I then ran this command to enable my site:

```

a2ensite site1.local

```
which completed successfully.

I then added an entry in /etc/hosts to point fcm.local to 127.0.0.1.

After restarting Apache, I mapped fcm.local to the IP of the dev box in the hosts file on my Windows machine.  But when I access it, I just get the site root of webdev.local.

Whenever I start Apache, I get the following error:
```

Restarting web server: apache2[Sat Aug 27 20:20:54 2011] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sat Aug 27 20:20:54 2011] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Sat Aug 27 20:20:55 2011] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sat Aug 27 20:20:55 2011] [warn] NameVirtualHost *:80 has no VirtualHosts

```

I don't know enough about Apache to know whether this warning has anything to do with the problem or not.  I would really appreciate any help anyone could offer.  I will post any relevant config files and information needed.  Thanks!

---

### Post by meastwood on 2011-08-27
The error is due to the fact that your NameVirtualHost address does not match your VirtualHost address.

If in ports.conf(or httpd.conf) you have
NameVirtualHost *:80

then you will need to specify
<VirtualHost site1.local:80>

if you have more than one virtual host sharing the the same address then you will need to specify
<VirtualHost *:80> 
for each site or else you will likely get

* Restarting web server apache2   
[warn] VirtualHost phpgal:80 overlaps with VirtualHost steves:80, the first has precedence, perhaps you need a NameVirtualHost directive
 ... waiting 
[warn] VirtualHost phpgal:80 overlaps with VirtualHost steves:80, the first has precedence, perhaps you need a NameVirtualHost directive

You may want to use 

ServerName e.g.site1.local
ServerAlias whatever

in your VirtualHost sections

---

### Post by kenquad on 2011-08-29
Thanks for the reply.

> **meastwood said:**
> 
If in ports.conf(or httpd.conf) you have
NameVirtualHost *:80

I do, in httpd.conf

> 
then you will need to specify
<VirtualHost site1.local:80>

I did, but no joy - same errors on restarting Apache.

> 
if you have more than one virtual host sharing the the same address then you will need to specify
<VirtualHost *:80> 
You mean instead of site1.local:80 above, or somewhere else?

---

### Post by kenquad on 2011-09-03
Using info from this thread and from another forum, I've got it partly working, but I would really appreciate some help in getting rid of that "partly" and taking this thing all the way.

Here's my config file for site1.local:

```

<VirtualHost *:80>
   ServerName site1.local
   ServerAlias site1.local
   ServerAdmin webmaster@localhost
   DocumentRoot /var/www/site1.local
   #log file for this server
   CustomLog /var/log/apache2/site1.local.log combined
	
	<Directory /var/www/site1.local/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride all
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>

```

Using Lynx from the server command line itself, I can access site1.local by hostname.  From my Windows workstations, however, where site1.local is mapped to the IP of the server, I get the default document root of the server when I put in site1.local.

I would really appreciate some help here, if anyone can think of anything.

---

### Post by kenquad on 2011-09-03
Never mind, it suddenly started working.  Must have been a caching issue or something like that.

---

