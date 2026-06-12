---
title: "Apache2 VirtualHost Multiple Sites"
date: 2005-05-14
forum: Server Platforms
---

### Post by cavalier67 on 2005-05-14
Hello,
I'm a linux/ubuntu noobie and could use a little help.

First some background and general information:

I have installed LAMP (Linux Apache2 MySql PHP) and it seems to be working fine in a very basic manner.  I can access the default site (/var/www/) on the server itself from localhost, its ip address (192.168.2.102), or it's machine name (gremlin).  From outside the server but still within the network I can only access it by it's IP address.


Here is what I want to do:

I want to run several web servers from the same machine.  One will be only accessible from within the network and for the rest I want to use no-ip.com (or some other free DNS service) to forward a domain name to my public IP address.  I also want the web server that is only accessed locally to have it's own domain name that does not come from no-ip.com.

I also want each of these webservers to be located in /home/username/some_directory.

What is the best way to accomplish this?

Seems that it has something to do with Virtual Hosting but most of the tutorials out there don't seem to apply to the way that Ubuntu sets up apache2.

Also, I have tried VHCS and for some reason it just doesn't want to install on my box.  Gandalf has been a great help here, but in the end I have had to abandon that as a possible solution to my problem.

Any help would be most appreciated,
Thanks,
Cavalier

---

### Post by SychoSly on 2005-05-14
[QUOTE=cavalier67]Hello,
I'm a linux/ubuntu noobie and could use a little help.

First some background and general information:

I have installed LAMP (Linux Apache2 MySql PHP) and it seems to be working fine in a very basic manner.  I can access the default site (/var/www/) on the server itself from localhost, its ip address (192.168.2.102), or it's machine name (gremlin).  From outside the server but still within the network I can only access it by it's IP address.


Here is what I want to do:

I want to run several web servers from the same machine.  One will be only accessible from within the network and for the rest I want to use no-ip.com (or some other free DNS service) to forward a domain name to my public IP address.  I also want the web server that is only accessed locally to have it's own domain name that does not come from no-ip.com.

I also want each of these webservers to be located in /home/username/some_directory.

What is the best way to accomplish this?

Seems that it has something to do with Virtual Hosting but most of the tutorials out there don't seem to apply to the way that Ubuntu sets up apache2.

Also, I have tried VHCS and for some reason it just doesn't want to install on my box.  Gandalf has been a great help here, but in the end I have had to abandon that as a possible solution to my problem.

Any help would be most appreciated,
Thanks,
Cavalier[/QUOTE]
 Here you go:

[http://www.unix-girl.com/geeknotes/apache_virtual_host_conf.html](http://www.unix-girl.com/geeknotes/apache_virtual_host_conf.html)

---

### Post by LordHunter317 on 2005-05-14
No, don't use the link he posted to.  It's not relevant to Debian/Ubuntu's apache2 configuration.

The procedure for name-based virtual hosting is pretty simple. Create a site for each virtualhost in /etc/apache2/sites-available. The form of each file should be something like this:```
<VirtualHost *>
ServerName example.com # Primary DNS Name of Server goes here
ServerAlias  # Any DNS names alised to this site go here

DocumentRoot /home/example.com/html/
<Directory "/home/example.com/html">
AllowOverride AuthConfig, Limit, Options
Order Allow, Deny
Allow from all
</Directory>

# Logging for this site and this site only
ErrorLog /home/example.com/logs/error_log
CustomLog /home/example.com/logs/access_log combined
</VirtualHost>
```Then, create the directory structure aliased above:```
mkdir -p /home/example.com/{logs,html}
```Finally, enable the site by running:```
a2ensite [filename]
```Where [filename] is the name of the file you created in /etc/apache2/sites-available.

The hosting user can now create files in /home/example.com/html and they'll be served only when people connect to example.com.  

For your site, you should have it use the default site, which will be the fallback site in all cases, or the site used when a Host request isn't sent by the browser. This will meet your needs.

Note that you still have to configure things like log rotation manually. Also, those files created have to be readable by the apache-user (www-data). This usually means giving them world-read access.

---

### Post by LordHunter317 on 2005-05-14
I forgot to mention, if all these virtualhosts will be the same, the documentation here: [http://httpd.apache.org/docs-2.0/vhosts/mass.html](http://httpd.apache.org/docs-2.0/vhosts/mass.html) might prove useful.

---

### Post by ali4728 on 2005-05-23
I tried the above method to set up two hosts but both of them are pointing to the same directory (original host /var/www ). 


This is the default host

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
	
	Alias /icons/ "/usr/share/apache2/icons/"
	<Directory "/usr/share/apache2/icons">
	    Options Indexes MultiViews
	    AllowOverride None
	    Order allow,deny
	    Allow from all
	</Directory>

    Alias /doc/ "/usr/share/doc/"
    RedirectMatch ^/doc/apache2-doc/manual(.*)$ /manual$1
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>





------------------------------------------------------------------------------
----------------------------------------------------------------------------
---------------------------------------------------------------------------

Here is the Socond Site (host)

<VirtualHost *>
ServerName [http://aliyilmaz.no-ip.info](http://aliyilmaz.no-ip.info) # Primary DNS Name of Server goes here
ServerAlias  # Any DNS names alised to this site go here

DocumentRoot /var/www/site2/
<Directory "/var/www/site2">
AllowOverride AuthConfig, Limit, Options
Order Allow, Deny
Allow from all
</Directory>

# Logging for this site and this site only
ErrorLog /var/www/site2/logs/error_log
CustomLog /var/www/site2/logs/access_log combined
</VirtualHost>

---

### Post by LordHunter317 on 2005-05-23
How are you connecting to the site?

---

### Post by ali4728 on 2005-05-25
I am Just typing the url [http://aliyilmaz.no-ip.info](http://aliyilmaz.no-ip.info)

---

### Post by LordHunter317 on 2005-05-25
Did you restart/reload apache after making these changes?  What do the logs say?

---

### Post by ali4728 on 2005-05-31
I figured it out, when I restart apache it did not like "AllowOverride AuthConfig, Limit, Options" in the <VirtualHost *> block. I removed those line and only left seerver name  and document root. Now both sites are functional.

Example: I have a directory in "/etc/apache2/sites-available" called mysecondsite, (/etc/apache2/sites-available/mysecondsite )

Content is:

<VirtualHost *>
ServerName [http://aliyilmaz.no-ip.info](http://aliyilmaz.no-ip.info)
DocumentRoot /var/www/site2/
</VirtualHost>

I think one should create a virtual host for every page hosted including  the default page.

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=ali4728]I figured it out, when I restart apache it did not like "AllowOverride AuthConfig, Limit, Options" in the <VirtualHost *> block.[/quote]Yeah, I see that now.  It should be "AllowOverride AuthConfig Limit Options" (note the lack of commas).  Sorry I missed it before, as it's a subtle thing.  One fustrating thing about apache is that if the core configuration loads and you have an error within a VirtualHost, it just disables that host instead of just crashing on load.  Which is retarded, IMO.

> I think one should create a virtual host for every page hosted including  the default page.That's not quite true.  You create one for every unique site you host.

---

