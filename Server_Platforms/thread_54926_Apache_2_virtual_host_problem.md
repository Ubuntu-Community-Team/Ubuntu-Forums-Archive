---
title: "Apache 2 virtual host problem"
date: 2005-08-06
forum: Server Platforms
---

### Post by slumption on 2005-08-06
I'm in the process if setting a hoary box up to replace my RH9 server. On the RH9 I have only needed to edit the http.conf and alter the hosts table. However I've read the posts about how apache2 uses more configs Im 99% there but I'm having a problem with the default site anyway: 

The set up is:

ADSL router NATing to the LAN IP of my server

hosts file has entrys for the FQD and the LAN IP so my clients inside the LAN can resolve the domains. I have a static IP and the DNS is set up via dydns.org

On the older server I have the LAN IP as the servername and then a series of virtual hosts. If I browse any of these they work and if I browse via the IP I get my default site.

I want to do the same on my ubuntu box so I have edited apache2.conf and have added the line:

NameVirtualHost 10.10.10.9

as the last line in my file

I have then made a 3 files in the /etc/apache2/sites-enabled/ folder

Contents of one as they are all similar other than doc roots / names

# Virtual host Paulssite
<VirtualHost 10.10.10.9>
 	DocumentRoot /webdocs/html/pauls-php/
 	ServerAdmin [email]myemail@yahoo.com[/email]
 	ServerName paulsite.homelinux.com
 	DirectoryIndex  index.php index.html index.htm index.shtml 
</VirtualHost>

I've run a2ensite and enabled them all, reloaded apache and altered my host table.

I can browse all 3 sites no problem But If I use the IP it defaults to the last virtual server I enabled.

My docroot is /webdocs/html/ for the default and /webdocs/html/sitename for the others as this is a seperate partion. I've edited my configs to represent this.

Any ideas  \\:D/

---

### Post by tonym on 2005-08-12
Is your default site in a <VirtualHost> of its own or in the main config file.  If the latter then I don't think it can work.

If the IP address of the interface that receives the message is in a <NameVirtualHost> then it will search the <VirtualHosts> for one with a <ServerName> that matches.  If it doesn't match it defaults to the first or last <VirtualHost>  - can't remember which.  Thus the behaviour you describe is what I would expect.

---

### Post by LordHunter317 on 2005-08-12
[QUOTE=tonym]Is your default site in a <VirtualHost> of its own or in the main config file.  If the latter then I don't think it can work.[/quote]Nope, Apache doesn't care.


> If it doesn't match it defaults to the first or last <VirtualHost>  - can't remember which.First.

To the OP:
Name-based virtual hosting doesn't work with IP addresses.  You must use the DNS name to access the server.  It's required.

As to why it's accessing the last one, that's odd.  Post all your virtual host sections.

---

### Post by slumption on 2005-08-15
Apache2.conf - lines I've added

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/[^.#]*
NameVirtualHost 10.10.10.50

0000-default - first virtual host file
NameVirtualHost * 
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
#	DocumentRoot /var/www/
	DocumentRoot /webdocs/html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
#	<Directory /var/www/>
	<Directory /webdocs/html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

Next virtual host - the other ones are all like this

# Virtual host PaulsPHP
<VirtualHost 10.10.10.50>
 	DocumentRoot /webdocs/html/pauls-php/
 	ServerAdmin [email]slumption@yahoo.com[/email]
 	ServerName paulsphp.homelinux.com
 	DirectoryIndex  index.php index.html index.htm index.shtml 
</VirtualHost>

---

