---
title: "[SOLVED] running a local site and an external site..."
date: 2008-08-18
forum: Server Platforms
---

### Post by a.thomas on 2008-08-18
Hi all,
I am trying to setup my server to run a local network site and an external site.
I am relatively new to server setup but know my way around Ubuntu.
I am using the default website virtualhost settings for my external site. I do NOT have a domain name for this external site. Users get to it from another site. 
I can view my external site fine and it all works.

Where I am lost is how to setup the internal site. I have created a new site-available 'testing' and enabled it and copied the default file and edited it as follows:
```
NameVirtualHost 192.168.0.189
<VirtualHost 192.168.0.189>
	ServerAdmin webmaster@site.com
	ServerAlias www.testing.site.com
	DocumentRoot /web/testing/
	<Directory />
		Options -Indexes FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /web/testing/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ErrorLog /var/log/apache2/internal-error.log

	CustomLog /var/log/apache2/internal-access.log combined
	ServerSignature Off
</VirtualHost>

```

The 'default' site's only difference is:
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@externalsite.com
	
	DocumentRoot /var/www/
	<Directory />
		Options -Indexes FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	CustomLog /var/log/apache2/access.log combined
	ServerSignature Off
</VirtualHost>

```
Then I edited the /etc/hosts file as follows:
```
127.0.0.1 localhost.localdomain localhost
192.168.0.189 testing.site.com www.testing.site.com
```

This is not working. Not matter what I type in, I get the files from /var/www/
Am I going about this wrong? I have never worked with virtual hosts before, so I am completely new to this.

Ideally I want to have the 'default' site be my external site and the 'testing' site be the internal site. 

Any help is greatly appreciated.
Thanks!

---

### Post by a.thomas on 2008-08-19
Nobody has any input? I have searched endlessly on this forum with only minimal help.

I think this should be simple but I can't seem to get it figured out...

Please someone help!

---

### Post by Ximbiot on 2008-08-19
To use NameVirtualHost, you should be using the same IP specifier for all your NameVirtualHost and VirtualHost directives (in this case, probably, "*").  Then, specify the "ServerName" directive so that the server can have something to compare the name the client is using to connect against.

IIRC, the first VirtualHost that gets loaded for an IP spec this way will be the default host for that IP spec, if none of the ServerName directives match.

For more, try reading the [Apache Virtual Host documentation]("http://httpd.apache.org/docs/2.0/vhosts/").

Derek

---

### Post by a.thomas on 2008-08-19
Ximbiot: I have looked at the Apache docs and no help. Thanks though.

OK maybe this will make sense... I do not have a domain name for my server. I only use it's IP address. 
Example:
users click on [www.site.com/fun](www.site.com/fun) (hosted elsewhere) 
they are redirected to [http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)

That is fine.

What I then want is if I type in 192.168.0.189 from my machine that is on the same network, I want to get what is in say '/path/here/'...NOT located in /var/www/.


Maybe this clears things up? IDK I guess I knew less about this than I thought...

---

### Post by Ximbiot on 2008-08-19
> **a.thomas said:**
> What I then want is if I type in 192.168.0.189 from my machine that is on the same network, I want to get what is in say '/path/here/'...NOT located in /var/www/.

For "Name-based Vitrual Hosting" to work, you need to access the web server via a host name.  Hence the "Name-based" portion of the name.

> **a.thomas said:**
> Then I edited the /etc/hosts file as follows:
```
127.0.0.1 localhost.localdomain localhost
192.168.0.189 testing.site.com www.testing.site.com
```

If this is the /etc/hosts file on the computer with your *browser*, you should be able to access the server by name and make things work, but you still probably have to set the config file up as I specified in my earlier post.

There is also something called "IP-based Virtual Hosting", but you need two IP addresses on your server to pull it off.  The Apache documentation link I sent earlier also has a link to information on how to set up IP-based virtual hosts.

---

### Post by a.thomas on 2008-08-19
> **Ximbiot said:**
> 
There is also something called "IP-based Virtual Hosting", but you need two IP addresses on your server to pull it off.  The Apache documentation link I sent earlier also has a link to information on how to set up IP-based virtual hosts.

I know what IP-based Virtual Hosting is... I just can't get it to work...

I do have 2 IPs... xxx.xxx.xxx.xxx and 192.168.0.189 each with it's own nic card.

the xxx.xxx.xxx.xxx goes to my dsl modem and the 192.168.0.189 goes to my internal network
```
 sudo ip route
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.189 
xxx.xxx.63.0/24 dev eth0  proto kernel  scope link  src xxx.xxx.63.12 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via xxx.xxx.63.1 dev eth0  metric 100
```

here is my /etc/hosts
```
127.0.0.1 localhost servername
```

here is the 192.168.0.189 config file under /etc/apache2/sites-available/testing
```
<VirtualHost 192.168.0.189>
        DocumentRoot /web/testing/

        <Directory /web/testing/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

here is the xxx.xxx.63.12 config file under /etc/apache2/sites-available/online
```
<VirtualHost xxx.xxx.63.12>
        DocumentRoot /var/www/

        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

```

So with this configuration I can get the external site fine from anywhere.
The internal site (192.168.0.189) returns a 404 not found. Is this due to my file location? i have the files under /web/testing/

Thanks for any help.

---

### Post by Ximbiot on 2008-08-19
> **a.thomas said:**
> The internal site (192.168.0.189) returns a 404 not found. Is this due to my file location? i have the files under /web/testing/

What's in your /var/log/apache/error.log?  If the file system permissions are set wrong on /web/testing/ or some such, there should be a message in there...

---

### Post by a.thomas on 2008-08-19
Well I forgot to reload apache after I enabled the testing site...
so I went back and did it, now I get this

```
[Tue Aug 19 16:46:24 2008] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.0.189 (check DNS) -- or specify an explicit ServerName
```


/var/log/apache2/error.log
```
[Tue Aug 19 16:37:06 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Tue Aug 19 16:37:06 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Tue Aug 19 16:38:09 2008] [error] [client 127.0.0.1] File does not exist: /htdocs
[Tue Aug 19 16:38:56 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Tue Aug 19 16:38:56 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Tue Aug 19 16:39:16 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Tue Aug 19 16:39:16 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Tue Aug 19 16:46:24 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Tue Aug 19 16:46:29 2008] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.0.189 (check DNS) -- or specify an explicit ServerName
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: cannot open shared object file: No such file or directory in Unknown on line 0
[Tue Aug 19 16:46:30 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch configured -- resuming normal operations
[Tue Aug 19 16:50:20 2008] [error] [client 192.168.0.110] Directory index forbidden by Options directive: /web/testing/
```

It may just be some configuration I set and do not realize...

Let me know what you think
Thanks!

---

### Post by Ximbiot on 2008-08-19
> **a.thomas said:**
> ```
[Tue Aug 19 16:50:20 2008] [error] [client 192.168.0.110] Directory index forbidden by Options directive: /web/testing/
```

This means you turned off indexes ("Options -Indexes ...", in your config) and you don't have an /web/testing/index.html file.  Fixing either one of these issues should solve this.

---

### Post by a.thomas on 2008-08-20
Thank you, I finally saw that. But now I am not sure what this error is?
```
[Tue Aug 19 16:46:24 2008] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.0.189 (check DNS) -- or specify an explicit ServerName
```

Any ideas?

---

### Post by Ximbiot on 2008-08-20
> **a.thomas said:**
> Thank you, I finally saw that. But now I am not sure what this error is?
```
[Tue Aug 19 16:46:24 2008] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.0.189 (check DNS) -- or specify an explicit ServerName
```

Any ideas?

You need to put an explicit ServerName line in your Apache config for each virtual host, or provide a reverse-lookup (maybe via /etc/hosts?) for the IP in question on the server.  I suggest the former.

Copied mostly from the [Apache2 VirtualHost examples]("http://httpd.apache.org/docs/2.0/vhosts/examples.html"):

```

# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80

<VirtualHost *:80>
DocumentRoot /web/testing/
ServerName www.testing.site.com

# Other directives here

</VirtualHost>

<VirtualHost *:80>
DocumentRoot /var/www/
ServerName www.site.com

# Other directives here

</VirtualHost>
```

---

### Post by a.thomas on 2008-08-20
Yes this makes sense, but with IP based is it not different? I have added to my apache2.conf file as follows:
```
NameVirtualHost xxx.xxx.63.12
NameVirtualHost 192.168.0.189

```

Here are my site config files now:
```
<VirtualHost 192.168.0.189>
        DocumentRoot /web/testing/
        ServerName testing.site.com

        <Directory /web/testing/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>
```

```
<VirtualHost xxx.xxx.63.12>
        DocumentRoot /var/www/
        ServerName site.com

        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>
```

I do not get this error anymore:
```
[Tue Aug 19 16:46:24 2008] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.0.189 (check DNS) -- or specify an explicit ServerName
```

I now get:
```
sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
```

Is this due to the /etc/hosts file?
I am assuming it is the /etc/hosts file, but I am not sure what to put in there.

Thanks for your help!

---

### Post by Ximbiot on 2008-08-20
> **a.thomas said:**
> I now get:
```
sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
```

Is this due to the /etc/hosts file?
I am assuming it is the /etc/hosts file, but I am not sure what to put in there.

This sounds like you have a third host you haven't showed us config for (the Apache package's sites-available/default?).  Regardless, you should be able to let Apache "reliably determine the server's fully qualified domain name" (FQDN) by putting the FQDN (e.g., "www.site.com") in /etc/hostname.

You have to reboot for the change to /etc/hostname to register, but you can set it until the next reboot like this:

```
sudo hostname www.site.com
```

Derek

---

### Post by a.thomas on 2008-08-20
I forgot I commented out the ServerName in the apache2.conf... so changing it solved my issue. Not sure what I was doing...

I do have the sites-available/default config still there but disabled. 

My server is name good to go with the setup I wanted... for now hahaha

Thanks Derek!

-Aaron

---

