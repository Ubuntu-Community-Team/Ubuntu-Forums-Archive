---
title: "apache virtual hosting"
date: 2006-12-19
forum: Server Platforms
---

### Post by Dansaycool on 2006-12-19
Hi, i'm tryin to configure apache for virtual hosting. I did manage to do it in the old version"1.3"  about a  year ago but I now just compiled apache 2.2.3 in ubuntu server and I cant seem to get it working again.
Can someone just give a quick reminder on how u do virutal hosting, i can remeber I had alot of trouble figuring what went inside the Virtual hosting bit inside the httpd.conf file

thanks dan

---

### Post by keithweddell on 2006-12-19
The apache documentation has quite a lot of info.  Otherwise does [this]("http://www.onlamp.com/pub/a/apache/2003/07/24/vhosts.html") help? 

Keith

---

### Post by MystaMax on 2006-12-19
Virtualhosting with apache is actually handled a bit differently on ubuntu, at least to my knowledge. I would read up on the [ubuntu server docs]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html")

from the help article:

>               Apache2 ships with a virtual-host-friendly default configuration.              That is, it is configured with a single default virtual host (using              the *VirtualHost* directive) which can modified or used as-is if you              have a single site, or used as a template for additional virtual hosts              if you have multiple sites.  If left alone, the default virtual host              will serve as your default site, or the site users will see if the              URL they enter does not match the *ServerName* directive of any of your               custom sites.  To modify the default virtual host, edit the file              /etc/apache2/sites-available/default.  If you              wish to configure a new virtual host or site, copy that file into the              same directory with a name you choose.  For example,              **sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite**              Edit the new file to configure the new site using some of the directives              described below.I finally got mine working, but I still get errors when running apacheconfigtest.

---

### Post by envis on 2006-12-19
i set a whole nice set of subdomains for my main domain with virtual hosts its quite easy...

first of all, you need to make sure that the new domain you want to set has a DNS poiting to your host..

after that, you can set the virtual domains

me on Ubuntu Dapper, i go in /etc/apache2/sites-availabe/

in there, you have a default site by default which is called... default....

what I did...

first of all i added those lines to the default <VirtualHost>:
----------------------
ServerName mydomain.com
ServerAlias [www.mydomain.com](www.mydomain.com)
--------------------------
inside, at the beginning of the <VirtualHost> in the default available site
(cos default had no ServerName by default)

then i created a new file in sites-availabe, i named it "mydomain"

inside of it i set each Virtual host other than my main domain (which i let the "default" handle)

the first thing, on top in the default-site, the (NameVirtualHost *) i just copied once on the top of my "mydomain" file 

then i copied the <VirtualHost> tag in the default (and all its contents) and pasted it on my "mydomain" file. 
then i only needed to change the ServerName and ServerAlias accordingly and of course, the DocumentRoot and the dir specified in the <Directory> tag to point to the root of that second domain

then you have 2 domains in you sites-available... now you need to have the "sites-enabled" to link to your new "site-available"...
doing this manually just didnt work for me, instead i just did:
sudo a2ensite mydomain
it enabled the new "site-available" and told me to restart apache

i restarted apache and then i had 2 domains with each their own root folder...

here is an example of a <VirtualHost> tag in my "mydomain" available-site:

(for a subdomain i called "test" at test.mydomain.com)

<VirtualHost>
        ServerName test.mydomain.com
	ServerAlias [www.test.mydomain.com](www.test.mydomain.com)
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/whatever/test
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/whatever/test/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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

