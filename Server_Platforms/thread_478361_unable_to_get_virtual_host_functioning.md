---
title: "unable to get virtual host functioning"
date: 2007-06-19
forum: Server Platforms
---

### Post by ebohatch on 2007-06-19
I have been running Apache2 on Windows for years  with virtual hosts.
I am trying to setup Apache2 on Ubuntu but am unable to get vitrual hosts working.
I can get the default page (redirect flag is on in conf) when choosing  [http://127.0.0.1](http://127.0.0.1)  or [http://localhost](http://localhost)

If I enter [http://localhost/eib](http://localhost/eib)  I do get my index page of my sub-directory,

BUT if I enter [http://eib](http://eib) I keep getting 500 Internal Server Error

Here is a list of my appropriate files:

	**sites-available/default**
#
# Use name-based virtual hosting.
#
NameVirtualHost *

<VirtualHost *>
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
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                RedirectMatch ^/$ /apache2-default/
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



	**sites-available/001-eib**
<VirtualHost *>
ServerAdmin [email]webmaster@eibassoc.com[/email]
ServerName eib

DocumentRoot /var/www/eib

<Directory /var/www/eib>
	   Options FollowSymLinks MultiViews ExecCGI Includes
	    AllowOverride All
	    Order allow,deny
	    Allow from all
</Directory>

Alias /icons/ /var/www/eib/images/
<Directory /var/www/eib/images>
		Options All MultiViews
	        AllowOverride All
	        Order allow,deny
	        Allow from all
</Directory>

ScriptAlias /cgi-bin/ /var/www/eib/cgi-bin/

<Directory /var/www/eib/cgi-bin>
	       AllowOverride All
	        Options ExecCGI Includes
	        Order allow,deny
	        Allow from all
</Directory>

ErrorLog /var/www/eib/logs/eib_error_log
CustomLog /var/www/eib/logs/eib_access.log combined

</VirtualHost>


	**/etc/hosts**
127.0.0.1	localhost
127.0.0.1	eib
127.0.1.1	emil-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


	**/etc/apache2/ports.conf**
Listen 80

---

### Post by twistedtwig on 2007-06-19
I believe (could be wrong) but this is becuase it is looking for a computer called eib

localhost is a dns lookup to that machine.  I have subdomains set up with virtual hosts e.g. subdom.mydom.com

if i tried to do subdom.com it wouldn't work.

so... to reiterate (because that didn't read well :p).... I think it is because the browser is looking to resolve the DNS name eib and is failing...

But I have been wrong once or two before ;)

---

### Post by ebohatch on 2007-06-19
Yeah that occured to me but on my Windows Apache2 setup that isn't a problem.
I will test your theory out.

---

### Post by ebohatch on 2007-06-19
Tested and that is not the problem. But in testing if I put in [http://eib](http://eib)  it actually took me to [www.eib.com](www.eib.com)    (no connection to me or my sites) so obviously eib was working but something else was going wrong. I looked at the apache main error logs before and saw nothing. Now that it appears I am pointing to the right directory I looked at the error logs in that directory /var/www/eib/logs/error_log.  Sure enough it was being kicked out for some other reason. Turns out I copy the entire web directory and it had .htaccess which was telling it to access mod_rewrite which I have not included in the available mods. Eliminated the mod-rewrite info and reset to eib now works properly.

Thanks for pointing me in the right direction.

---

