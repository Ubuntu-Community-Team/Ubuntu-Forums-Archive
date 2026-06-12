---
title: "Virtual server help"
date: 2007-11-10
forum: Server Platforms
---

### Post by turtle02 on 2007-11-10
i am using ubuntu lamp 6.06. i have decided to create a couple of vhosts on my server. i installed webmin and created a vhost.when i try to view my site it takes me to the directory /var/www and lets me view all of the directorys inside /var/www. why does it  not take me to the correct dir and the correct site? what am i missing or doing wrong

---

### Post by k_grdn on 2007-11-10
Hi turtle02,

Post your vhosts files, you'll find them in /etc/apache2/sites-available, I'm assuming as it's dapper apache2.

Regards,

k_grdn

---

### Post by turtle02 on 2007-11-10
it is apache2
 i have two files the default and the webmin created one.

here is the default on

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
<Directory "/var/www">
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


here is the webmin created one.


<VirtualHost .com:80>
DocumentRoot /var/www/cool
<Directory "/var/www/cool">
allow from all
Options +Indexes
</Directory>
UserDir "/var/www/cool"
ServerPath /var/www/cool
ServerName .com
</VirtualHost>

---

### Post by turtle02 on 2007-11-10
i fixed it. i had the address set to the dns name of my site. i needed to be set to"any" it is working now.

---

### Post by hockey97 on 2007-11-11
I need help with mine.

I have it working, but it only works on my computer that has the servers.

on other computer on the network and also external traffic can't.

I have a paid domain name, I am having trouble to direct traffic from that domain name to my apache2 server for the website and the resource of the website.

my domain name paid one I tested it by using a proxy server to see what people get to see on the outside of my network they get a error message saying the web page is experiencing difficulties please try again later.

I need to know what I need to do to  have my paid domain name be pointed to my apache server to the virtuial host that will take care of that domain webpage resorce.

on my computer the one I am using I can type that domain name in my web browser and I will get the main page so it's working.

but only works on my computer, my other computers at my house on the same network get error's when they try to go on that domain name .

How would I fix this??

---

