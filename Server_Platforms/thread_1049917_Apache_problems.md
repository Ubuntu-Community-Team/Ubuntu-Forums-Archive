---
title: "Apache problems"
date: 2009-01-25
forum: Server Platforms
---

### Post by turbozmike on 2009-01-25
Im trying to get apache and squirrel mail setup and am failing.
I can access the apache test message from inside my network.
I cannot access any squirrelmail web interface.

Im 100% positive my router and firewall are setup correctly.  I have an SBS 2003 server up and running behind it and just added this ubuntu server into the same rules the sbs server operates under.  An external IP is also forewarded to the ubuntu server.

netstat -an | grep LISTEN makes me think apache is using the loopback adapter and not eth0.

HELP!!!

---

### Post by spiderbatdad on 2009-01-25
To do this very thing I set up two vitual host containers inside apache's sites-available folder. The squirrelmail virtualhost first, listening on port 443 with SSLEngine on. SM also has its own DocumentRoot. It also has its own FQDN registered to resolve to my ip address.

The other website goes second. Listens on port 80 has its own FQDN and DocumentRoot.

Also the SM config has to be run and set up correctly.

---

### Post by turbozmike on 2009-01-25
could you describe how to do any of what you mentioned?
I did run the squirrelmail-config by the way.

---

### Post by spiderbatdad on 2009-01-25
I will try, but you will have to do some leg work. I may miss a detail, or have a typo.
First I registered a second site with DynDns. I think they allow you 25, or 50 sites. Both sites resolve to my external ip address. So site 1 is examplemail.podzone.com and site 2 is example.podzone.com

I have /var/www for site 2. For site 1, I made the folder /www, and put the squirrelmail docs in it. The main directory squirrelmail is linked to /usr/share/squirrelmail. Simply ln-s /www/squirrelmail /usr/share/squirrelmail

This is an example of my /etc/apache2/sites-available/mysite file. It has since changed, but trying to show you what I had:
```


<VirtualHost *:443>
	ServerAdmin email@gmail.com
	ServerName examplemail.podzone.com
	DocumentRoot /www/squirrelmail/
		SSLEngine On
	 <Directory /www/squirrelmail>
               Options FollowSymLinks MultiViews
               AllowOverride none
                Order allow,deny
                allow from all
       </Directory>

	<Directory /usr/share/squirrelmail>
		Options Indexes FollowSymLinks
	<IfModule mod_php4.c>
		php_flag register_globals off
	</IfModule>
	<IfModule mod_php5.c>
		php_flag register_globals off
	</IfModule>
	<IfModule mod_dir.c>
		DirectoryIndex index.php
	</IfModule>

  # access to configtest is limited by default to prevent information leak
	<Files configtest.php>
		order deny,allow
		deny from all
		allow from 127.0.0.1
	</Files>
	</Directory>

# users will prefer a simple URL like http://webmail.example.com

		ErrorLog /var/log/apache2/error-webmail.log 
		LogLevel warn 
		CustomLog /var/log/apache2/access-webmail.log combined 

# redirect to https when available (thanks omen@descolada.dartmouth.edu)

	<IfModule mod_rewrite.c>
	<IfModule mod_ssl.c>
	<Location /squirrelmail>
		RewriteEngine on
		RewriteCond %{HTTPS} !^on$ [NC]
		RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
	</Location>
	</IfModule>
	</IfModule>



	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel info

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
<VirtualHost example.podzone.com:80>
        ServerAdmin email@gmail.com
        ServerName example.podzone.com

        DocumentRoot /var/www/
        <Directory />
                AuthType Basic
                AuthName "Restricted Files"
                AuthUserFile /home/my_user/.htpasswords
                Require valid-user
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel info

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

</VirtualHost>


```
Of course the SSL used for squirrelmail might be something you dont want right off. In which case you will want a different port...like 8080 perhaps. If you go with ssl, you will need to generate a certificate...etc

I did not set this up in a matter of minutes or even hours. I'm a little embarrassed to say I spent almost 80 hours getting all this working, but I also used postfix, mysql, courier, spamassassin, shorewall, etc. as outlined in this tutorial:
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

And that guide wasn't perfect either, but close most of the time. I had to do additional web searches and sign on to irc #squirrelmail #courier #postfix to get some answers. This was mostly a way to stay out of trouble for a week.
There is a much easier mail server called citadel that will run on its own...without appache...as will squirrelmail. I tried citadel. It was ok. It was up and running in 20 minutes. Personally I didn't like the interface as much as I like SM. SM also hs all those great plugins...users can change passwords, etc. Anyway, goodluck. Expect to spend some time on this. Research with google was key for me.

---

### Post by turbozmike on 2009-01-26
I still cant access the ubuntu webserver from outside the network
I confirmed the default ubuntu firewall is turned off.

Internally it works ok.
Any other ideas?

---

### Post by spiderbatdad on 2009-01-26
what is the message from the browser or web server when you fail to connect from outside the network?

---

### Post by turbozmike on 2009-01-26
from outside i get nothing at all like theres no such thing as [www.reliantappraisals.com](www.reliantappraisals.com) or 70.89.xxx.xxx ip address.

from inside the network only the server can view the [www.reliantappails.com](www.reliantappails.com)
or [http://localhost](http://localhost)

the workstation on my nework can only see it using the internal IP or localhost.  it doesnt resolve the name for some reason.

---

### Post by Lori700698 on 2009-01-26
This may seem seriously dumb, BUT I had similar issues when I was trying to connect my music server to the outside world.  I accidentally pointed my DNS to my internal IP address that was hosting the site instead of my actual IP address served up by my internet provider.  Go here from an internal machine on your network [http://www.dyndns.com/support/tools/](http://www.dyndns.com/support/tools/) and choose checkip.dyndns.com.  Point your DNS to this address.  If this is what you are already using than you are out of my league of assistance.  Hope this helps!

---

### Post by turbozmike on 2009-01-27
I included my default file as it is a little differnt than what you posted and possibly not %100 corrrect though it does work internally.
the first 2 lines are what Im unsure of.

Ports.conf uses listen 80

I use cheapdomains123.com,I have my domain.com pointed to my static external ip address (I have a domain.biz address fully functional on another server)


> NameVirtualHost *
<VirtualHost *>
	ServerAdmin [email]mike@reliantappraisals.com[/email]
	ServerName reliantappraisals.com
	ServerAlias *.reliantappraisals.com
	
	DocumentRoot /var/www/
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

---

### Post by spiderbatdad on 2009-01-27
edit the file /etc/hosts so that the internal ip points to your fqdn:
192.xxx.xx.xxx [www.reliantappraisals.com](www.reliantappraisals.com)

ports.conf can have more than one port. you will need at least 80 and one other for SM.

put the ports in your virtualhosts files. For example:
<VirtualHost *:80>

lose the <NameVirtualHost*> line. Instead try placing a single line in httpd.conf: ServerName [www.reliant](www.reliant)..... Also leave that same line in your vitualhost container.

Check log files: /var/log/auth.log and /var/log/apache2/error.log

---

### Post by turbozmike on 2009-01-27
still a no go.
I reinstalled the whole thing thinking i probably got 1/2 the stuff fubr.  I gave webmin a try to see if that might curb some mistakes but i get the same results.

Works internally but not from an external source.
Weird.  Mail gets in and out with no problem.

Im really missing and appreciating IIS/exchange right now.

---

### Post by turbozmike on 2009-01-27
this has gotta be some kinda dns issue.
my workstation doesnt resolve reliantappraisals.biz either.
i have to put the local ip for it to work.

---

### Post by turbozmike on 2009-01-28
maybe this will help.

Sitting at the ubuntu server I can

ping 70.89.XXX.XX1 exchange server on same network
Nmap on the exchange server works fine
If I ping 70.89.XXX.XX2 the ububuntu server it goes no where.
Nmap on the ubuntu servers wan address doesnt work either.

Does this help?
Im stumped.

Internet works just fine on the ubuntu server, I can dowload, update programs ect with no problems.

---

### Post by turbozmike on 2009-01-28
I figured it out.
I use a zywall firewall.  These are excellent pieces of hardware if you ever need a good firewall.

Anyways when I changed the rules in the firewall I just loged out of it.
The new rules took effect but the old rules were working also.
I figured this out when I noticed my workstation had the same external IP the server was using.

I rebooted the firewall and not it works

70.89.145.58

WOW, talk about simple things causing huge problems.

---

