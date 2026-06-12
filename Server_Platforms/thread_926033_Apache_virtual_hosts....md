---
title: "Apache virtual hosts..."
date: 2008-09-21
forum: Server Platforms
---

### Post by yoghurt on 2008-09-21
(solved)

Hi there,
I'm just trying to set up apache2 to run on my home PC (with Ubuntu on it of course). Long story short, it doesn't work:

```
My /etc/hosts:
127.0.0.1	localhost
127.0.1.1	Ubuntu
127.0.0.1	hamplici.localhost
127.0.0.1	joomla.localhost
127.0.0.1	php.localhost

...

```

As you can see from this file, I'm trying to have 3 different apache virtual hosts (hamplici.localhost, joomla.localhost and php.localhost).
This is the content of /etc/apache2/sites-available (default is disabled):

```
-rw-r--r-- 1 root root  985 2008-06-25 15:50 default
-rw-r--r-- 1 root root 1056 2008-09-16 17:53 hamplici
-rw-r--r-- 1 root root 1046 2008-09-16 21:22 joomla
-rw-r--r-- 1 root root 1031 2008-09-21 20:06 php
```

All of these config files are set up properly (document roots all to different folders etc...), config files went through the "a2ensite" procedure, apache configuration was reloaded and apache was later even restarted. 

What happens though is that when I enter to the browser for example php.localhost, browser opens the index.html from joomla.localhost. Then, whichever of the 3 virtual hosts name I enter to the browser, it never opens the relevant index.html...

So, question for a million; what's wrong? 

Just to be sure I haven't forgotten anything, here's the content of one of the virtual hosts config files:
```

<VirtualHost *>
	ServerAdmin tomas.hampl@gmail.com
	
	DocumentRoot /home/yoghurt/web/php/
	ServerName php.localhost
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/yoghurt/web/php/>
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

	ErrorLog /home/yoghurt/web/php/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /home/yoghurt/web/php/access.log combined
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

Thanks in advance for your help!

---

### Post by mbeach on 2008-09-23
do you have the servername set anywhere else in your /etc/apache2/ conf files?  For some reason people are putting it in httpd.conf.  Only set it in the virtual hosts files.  Try:
```
grep -iR servername /etc/apache2/*
```  I'd double check your Servername and Documentroot directives.  Restart with "sudu /etc/init.d/apache2 restart".

Do all the sites go to the joomla site?

---

### Post by leg on 2008-09-23
try <VirtualHost php.localhost> instead of the asterisk. Change the others in the same way also.

---

### Post by yoghurt on 2008-09-24
> **leg said:**
> try <VirtualHost php.localhost> instead of the asterisk. Change the others in the same way also.

Hm...that was probably the only place I have not checked before...seemed to have worked: I've changed the setup of the virtual hosts as per your advice in the the <Virtual Host > I entered the full "server name" and it works like a charm.

Thanks a bunch mates!!!

@mbeach: No, I strictly followed the advice on various websites how to set up the virtual hosts on Apache.I have also tried to restart apache directly. It was always the same...anyway, thanks for your advice!

---

### Post by yoghurt on 2008-09-26
Hmph...thought that was it, but tried it again today after enabling the other virtual hosts and the same thing happened.

I'd be very grateful for any ideas....

---

### Post by iLLiCiTgr on 2008-09-26
Why don't you change your apache to Name-based bound to your local ip? something like this

    NameVirtualHost 127.0.0.1

    <VirtualHost 127.0.0.1>
    ServerName php.localhost
    DocumentRoot /home/yoghurt/web/php/
    </VirtualHost>

    <VirtualHost 127.0.0.1>
    ServerName joomla.localhost
    DocumentRoot /home/yoghurt/web/joomla/
    </VirtualHost>

etc..

You can learn more here [http://httpd.apache.org/docs/1.3/vhosts/name-based.html]("http://httpd.apache.org/docs/1.3/vhosts/name-based.html")

---

### Post by yoghurt on 2008-09-27
> **iLLiCiTgr said:**
> Why don't you change your apache to Name-based bound to your local ip? something like this

  You can learn more here [http://httpd.apache.org/docs/1.3/vhosts/name-based.html]("http://httpd.apache.org/docs/1.3/vhosts/name-based.html")

Thanks for the tip...I'll give it a try and will post here how it went...

---

### Post by yoghurt on 2008-09-27
I'm not sure that IP-based virtual hosts are the way to go for the home PC - the article you have linked says 

```
...Therefore you need to have a separate IP address for each host...
```

So I guess I'll have to keep looking :)

---

### Post by Nockerofnod on 2008-10-17
Ok here is how I got mine to work and ill point out the changes that you may want to make to get the 
Virtual Host to work. 

1) Create a user on the local box. This is for easy of ftp.
2) The Virtual Host that you whant to host the site go in to the config and point the first document root to a user home folder.
 here is the one that I have my site running for reference. 

NameVirtualHost nockerofnod.homelinux.com
<VirtualHost 192.168.4.16>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/nockerofnod/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

---

