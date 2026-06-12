---
title: "Which Virtual host directives are overriding my vhosts?"
date: 2009-11-01
forum: Server Platforms
---

### Post by tadwick on 2009-11-01
[COLOR=#000000][COLOR=#000000]First time Linux user here (Ubuntu 8.04 on Linode VPS). I've installed Apache 2 and not clear about vhost configuration and whether I should retain the default vhost config.[/COLOR][/COLOR]
 
[COLOR=#000000][COLOR=#000000]Below is the contents of the default file in sites-available. This seems to take precedence over any other vhost file I create (or if I embed my vhost block **after** this one in the default file).[/COLOR][/COLOR]
 
If I delete the contents of default or place my block ahead of this I get my content as expected; otherwise I just get "It works" from the default location.
 
What is best practice here?
 
Tx
 
 
 
 
[html] 
<VirtualHost *:80>
 ServerAdmin webmaster@localhost
 
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
[/html]

---

### Post by mrsteveman1 on 2009-11-01
What do your other vhost sections say?

---

### Post by tadwick on 2009-11-02
Hi Steve,

Here's an example:

[HTML]<VirtualHost *:80>
	ServerAdmin webmaster@example.com
        ServerName cms.example.com
        DocumentRoot /srv/www/cms.example.com/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /srv/www/cms.example.com/public_html>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>


        ErrorLog /srv/www/cms.example.com/logs/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

        CustomLog /srv/www/cms.example.com/logs/access.log combined
	ServerSignature On


</VirtualHost>[/HTML]

---

### Post by Lars Noodén on 2009-11-02
If you are not using the default vhost, then it is probably fine to deactivate it.  

Looking at the two configurations, you have ServerName in only one of them.  If you are aiming for [name-based](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) virtual hosts, you will need a unique SeverName directive in each vhost.

The name-based virtual hosts should be defined here:
/etc/apache2/ports.conf

Then it's up to each vhost to identify itself.

PS.  I've been considering this kind of problem lately and wonder if Ubuntu, at least the server edition, should come with 2 example vhosts just to make the method more obvious.  So, when things are sorted on your server, feedback about how it could have been made more clear in the default Ubuntu would be valuable.

---

### Post by tadwick on 2009-11-02
The [Ubuntu Apache documentation]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html") suggests that as long as your other virtual hosts have a ServerName directive that matches your DNS then the fact that the default file is missing a ServerName directive should be ok:

> [LIST]
[*]Apache2 ships with a virtual-host-friendly default configuration. That is, it is configured with a single default virtual host (using the VirtualHost directive) which can modified or used as-is if you have a single site, or used as a template for additional virtual hosts if you have multiple sites. If left alone, the default virtual host will serve as your default site, or **the site users will see if the URL they enter does not match the ServerName directive of any of your custom sites**. To modify the default virtual host, edit the file /etc/apache2/sites-available/default. If you wish to configure a new virtual host or site, copy that file into the same directory with a name you choose. For example, sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite Edit the new file to configure the new site using some of the directives described below.
[/LIST]

However, to make my virtual hosting work I have to do one of the the following:

[LIST=1]
[*]Delete the default file,
[*]Replace the entries in the default file with the directives of one of my own virtual sites,
[*]Delete the entries in the default file, or
[*]Disable the default file (using a2dissite)
[/LIST]

---

