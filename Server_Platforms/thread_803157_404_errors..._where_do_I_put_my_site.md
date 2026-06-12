---
title: "404 errors... where do I put my site"
date: 2008-05-22
forum: Server Platforms
---

### Post by JameoPotato on 2008-05-22
I have finally got my webserver up and running and woho. I go to jameopotato.com and I get a 404 ERROR message.
Well thats not so bad at least there is a clear connection to the server which is all good seeing its little signature on the bottom.

But I have been making files all over the place on my server now and none of them seem to show up on the web.

My ServerRoot (in apache2) is : /etc/apache2
and my DocumentRoot (for my virtual server) is : /var/www

So... i put index.php in /etc/apache2/var/www/
nothing
/var/www/
nothing

Where is my site on my server (srry if this deserves to be in the noob section.)

---

### Post by hvc123 on 2008-05-22
morning,

have you chown -R www-data:www-data /var/www/(directory of web site) and chmod -R 775 /var/www/(directory of web site).

this will allow your apache2 user (web users) to see the files.

in apache 2 you are sopposed to ln -s the website directory to /etc/apache2/sites/enabled. 

also do you not get the "it works" default page from apache if you navigate to [http://127.0.0.1](http://127.0.0.1) ?

---

### Post by JameoPotato on 2008-05-22
Okay, I ran:
chown -R www-data:www-data /var/www/
and
chmod -R 775 /var/www/

And nothing seemed to have changed... what exactly did I do there by those commands?
Also I left the (directory of web site) area blank because my documentRoot is /var/www . so I don't think I needed to add anything there.
Should I maybe change my document root to something unique?

Please explain on this ln -s to the website directory which you are saying is in /etc/apache2/sites/enabled????

and since I am running command prompt and new to this i don't know how to "browse to http://127.0.0.1".

thanks

---

### Post by JameoPotato on 2008-05-22
okay, after setting up my ftp server I now know that my website directory is /var/www/jameopotato/

I put index.php in there again and still no luck ... you can visit my website to see for yourself [www.jameopotato.com](www.jameopotato.com)

i ran the chown and chmod commands like you ask and I now know what they are doing (did some of my own research)
Makes sence that I would need to set permission to allow local web users to see my website, but still no luck.

Any other guesses as to why it doesn't show up and I keep getting ERROR 404?

---

### Post by freebeer on 2008-05-22
I just tried it... I didn't get a 404 error... I got a time-out error.

---

### Post by JameoPotato on 2008-05-23
Yea, I asked some other people to test it too and same result for them.

I'm going to post my httpd.conf and /etc/apache2/sites-available/jameopotato for review and see if you guys can see anything wrong.

httpd.conf
```
NameVirtualHost 207.216.210.44:80
```

/etc/apache2/sites-available/jameopotato
```
<VirtualHost 207.216.210.44:80>
	ServerAdmin mouse_in_the_house90@hotmail.com
	ServerName jameopotato.com
	ServerAlias www.jameopotato.com
	ServerSignature On
	DocumentRoot /var/www/jameopotato
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/jameopotato>
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

let me know if you see anything wrong or out of place pls

ALSO
 
I went to my registration site for my domain name. [www.mydomain.com](www.mydomain.com) and I registered 2 nameservers.
I don't know if I did this right but I named them ns1.jameopotato.com and ns2.jameopotato.com and set their IP address' to the DNS IPs that show up on my router's status screen. Is that the right thing to do?
I then set up a A record for jameopotato.com -> 207.216.210.44 (my servers ip).

Does that sound right or did I do sometihng wrong?
cause it still isn't working

---

### Post by JameoPotato on 2008-05-23
OMG IT WORKS! YES I FIXED IT!

Incase anyone else is having troubles with this here are my notes:

Nameservers- You set the hostnames of these to ns1.(yourdomain).com and ns2.(yourdomain).com. When it asks you for an IP address of these name servers use the ones supplied by your ISP. You can find them by going to your routers status page, beside DNS SERVERS: 
OR if you are running windows on the same network. Start->run->cmd and type ipconfig/all and then they will be shown beside DNS SERVERS: aswell.

Once your name server is set up right, I changed my /etc/apache2/httpd.conf file to this (edit to fit your own site but keep the *'s)

```
NameVirtualHost *
<VirtualHost *>
ServerName jameopotato.com
ServerAlias www.jameopotato.com
ServerAdmin *enter your email address here (optional)*
DocumentRoot /var/www/jameopotato
</VirtualHost>
```
DocumentRoot can be set to anything but I like just /var/www/*your domain* **Be sure to "sudo mkdir /var/www/*your domain*"**

Check your /etc/apache2/ports.conf
it should say "Listen 80" at the top.

Should work.

---

### Post by kustomjs on 2008-05-23
here I will help you out
go to here:[http://ubuntuforums.org/showthread.php?t=201460](http://ubuntuforums.org/showthread.php?t=201460)
read that.

but here is how I did mind:
go to /etc/apache2/sites-available on your webserver and make a new file like JameoPotato.com
then enter this:
```
#
# site.com
#
<VirtualHost *:80>
  ServerName name of the server
  ServerAlias www.JameoPotato.com
  DocumentRoot /var/www/JameoPotato/etc....
  CustomLog /var/log/apache2/JameoPotato.com-access.log combined
  ErrorLog /var/log/apache2/JameoPotato.com-error.log
</VirtualHost>
```

then go to your default code of
```
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/put in your directory name
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

then you do is a2ensite sitename.com for both and then do this /etc/init.d/apache2 restart

then it should come up.

---

