---
title: "Apache2 NameVirtualHost ?"
date: 2009-03-30
forum: Server Platforms
---

### Post by artheus on 2009-03-30
```

<NameVirtualHost *.mydomain.org:80>
	ServerAdmin wwwmaster@localhost
	
	DocumentRoot /mnt/sdb1/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /mnt/sdb1/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
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

</NameVirtualHost>

```

When I restart the Apache2 with this in the /etc/apache2/sites-available/default it just won't work. It returns

```
Invalid command '<NameVirtualHost', perhaps misspelled or defined by a module not included in the server configuration
[fail]
```

Hum.. What am I doing wrong?

What I want to do is, I want to have my webserver show different sites on different domain names. I've got a few domain names which I want to use. Let's call them "mydomain.org" and "myotherdomain.org".. I can't really find out how to configure this.
I've been directed here :
[https://help.ubuntu.com/8.04/serverguide/C/httpd.html]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")
But I can't really find where they explain this..

Cheers,
Artheus

---

### Post by BkkBonanza on 2009-03-30
You are using this directive incorrectly.
You put ip address in VirtualHost directive and the name is specified inside the block as, 

NameVirtualHost 111.222.111.111

<VirtualHost 111.222.111.111>
ServerName splat.mydomain.org
DocumentRoot /var/whatever

... more of same and other directives...
</VirtualHost>

Also if you only have 1 interface on your machine then it's easiest to use,

NameVirtualHost *
and
<VirtualHost *>

See docs here,
[http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost](http://httpd.apache.org/docs/2.2/mod/core.html#namevirtualhost)

---

### Post by artheus on 2009-03-30
Well thanks!

But!!

Now I get the response 
```

[Mon Mar 30 17:30:17 2009][warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting apache2: Could not reliably determine the server's fully qualified 
domain name, using 127.0.1.1 for ServerName.

```

---

### Post by BkkBonanza on 2009-03-30
Mistaken comment *deleted*

---

### Post by artheus on 2009-03-30
hmm.. Is that for several urls?

---

### Post by BkkBonanza on 2009-03-30
Just checked again my old configs and I was reading a fragment that was incorrect. In my actual httpd.conf it looks as I stated above.

Sorry I have to dig deeper. All my stuff for more than a year now has been done with nginx not apache. Different style config (easier in my opinion).

---

### Post by BkkBonanza on 2009-03-30
Here is a portion form my original apache config and this definitely worked for me. I have altered only the domain name for privacy.

NameVirtualHost *:80

<VirtualHost *:80>
    ServerAdmin [email]admin@mydomain.com[/email]
    DocumentRoot /var/www/mydomain/adminX
    ServerName mydomain.com
    ServerAlias n1.mydomain.com
    ServerAlias [www.mydomain.com](www.mydomain.com)
    ErrorLog /var/log/www/adminX-error.log
    CustomLog "/var/log/www/adminX.log" common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin [email]admin@mydomain.com[/email]
    DocumentRoot /var/www/mydomain/admin
    ServerName n2.mydomain.com
    ServerAlias anotherdomain.com
    ServerAlias [www.superdomain.com](www.superdomain.com)
    ScriptAlias /cgi-bin/ /usr/www/cgi-bin/    
    ErrorLog /var/log/www/admin-error.log
    CustomLog "/var/log/www/admin.log" common
</VirtualHost>

---

### Post by artheus on 2009-03-30
Well.. I still get the

```
[Mon Mar 30 17:30:17 2009][warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting apache2: Could not reliably determine the server's fully qualified 
domain name, using 127.0.1.1 for ServerName.
```

Is this supposed to be in the httpd.conf or in the /etc/apache2/sites-available/default??

I really don't get this..

Thanks by the way!

EDIT:

This is the current way the /etc/apache2/sites-available/default looks

```

NameVirtualHost *:80

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName mydomain.org
	ServerAlias *.mydomain.org
	
	DocumentRoot /mnt/sdb1/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /mnt/sdb1/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
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

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName myotherdomain.org
	ServerAlias *.myotherdomain.org
	DocumentRoot /mnt/sdb1/www2/
</VirtualHost>

```

---

### Post by BkkBonanza on 2009-03-30
I don't know what's causing that. It looks like a warning so I wonder if your sites are working despite the warning?

I just thought to check other settings in my working conf file and compare.
In addition to the virtual host settings I have the following that may have some influence on how virtual hosts are interpreted. You may want to check if you have similar ones. These are "global", ie. before the NameVirtualHost directive and outside any blocks. Real names changed only.

ServerName myhost.com
DocumentRoot /var/www/myhost
HostnameLookups Off
Listen 80
Listen 443

I keep all my config in one file but I don't think if it's split into seperate files it makes any difference. I have about 12 sites setup like this including a couple ssl sites on secondary ips. I don't get any warnings or error messages though.

Also, if you haven't already seen it you may want to look over some of the examples given in the apache docs here,

[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

---

### Post by artheus on 2009-03-31
Thanks alot for your help!

Found out the problem!

The problem was that in the ports.conf there already where a "NameVirtualHost *:80" So I had made a duplicate.. Which made the error that one of those did not have VirtualHosts.. So I Removed the one from my "/etc/apache2/sites-available/default" and it now works perfectly! :)

Cheers,
Artheus

---

### Post by BkkBonanza on 2009-03-31
Good to hear! 
They didn't used to have so many different conf files, and personally I think it just makes it harder to use. But oh well, I'm not using Apache any more anyway.

---

### Post by lbharti on 2009-08-17
One does not have to have so many conf files for Apache. That is only for convenience, and one can add all configuration modifications to httpd.conf by standard or even in apache2.conf, yes even website definitions.

For the No virtualhost problem see my blog at [http://fixed-it.blogspot.com/2009/08/jaunty-apache2-no-virtualhosts-problem.html](http://fixed-it.blogspot.com/2009/08/jaunty-apache2-no-virtualhosts-problem.html)

---

### Post by creatorbri on 2010-03-22
*In case someone else comes along looking for the answer:*

The likely cause of the message ```
Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
``` is that you have not included a default ServerName value in your config. You need to add a line like this to your httpd.conf or apache2.conf:

```
ServerName localhost
```

---

### Post by hallboy3 on 2010-07-08
Hi guys.
If you have error:
> 
  [COLOR=Red]* Reloading web server config apache2
  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName                             [ OK ][/COLOR]

when you reloading  (or restarting) apache with some NameVirtualHost, you need to edit file /etc/hosts  like this:

> 
127.0.0.1    localhost laptop
127.0.1.1    laptop
127.0.1.1 YourVirtualHostName


---

