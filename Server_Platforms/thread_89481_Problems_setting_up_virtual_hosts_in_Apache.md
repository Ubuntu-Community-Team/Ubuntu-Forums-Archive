---
title: "Problems setting up virtual hosts in Apache"
date: 2005-11-12
forum: Server Platforms
---

### Post by s0c0 on 2005-11-12
I am having problems setting up virtual hosts for apache.  I do not have domain names setup yet since I am just experimenting, but from what I've read this should work anyways,  When I try going to the either of the two sites I get a 403 Forbidden page that says "You don't have permission to access / on this server."

The only modifications I've made have been to the httpd.conf and the /etc/hosts file.  Is there anything else I need to do or anything wrong with my httpd.conf file.

I am using Apache 1.3. Here is what my httpd.conf file looks like:


### Section 3: Virtual Hosts
#
# VirtualHost: If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them.
# Please see the documentation at <URL:http://www.apache.org/docs/vhosts/>
# for further details before you try to setup virtual hosts.
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# If you want to use name-based virtual hosts you need to define at
# least one IP address (and port number) for them.
#
NameVirtualHost 192.168.1.102:80
#NameVirtualHost 12.34.56.78

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
#
#<VirtualHost ip.address.of.host.some_domain.com>
#    ServerAdmin [email]webmaster@host.some_domain.com[/email]
#    DocumentRoot /www/docs/host.some_domain.com
#    ServerName host.some_domain.com
#    ErrorLog logs/host.some_domain.com-error.log
#    CustomLog logs/host.some_domain.com-access.log common
#</VirtualHost>

#<VirtualHost _default_:*>
#</VirtualHost>

# Automatically added by the post-installation script
# as part of the transition to a config directory layout
# similar to apache2, and that will help users to migrate
# from apache to apache2 or revert back easily
Include /etc/apache/conf.d

<VirtualHost *>
DocumentRoot "/var/www/chrisbsd123/"
ServerName chrisbsd123
<Directory "/var/www/chrisbsd123/">
AllowOverride None
</Directory>
</VirtualHost>

<VirtualHost *>
DocumentRoot "/var/www/debianchris/"
ServerName debianchris
<Directory "/var/www/debianchris/">
AllowOverride None
</Directory>
</VirtualHost>

---

### Post by fiasco on 2005-11-12
/var/www/debianchris/
/var/www/chrisbsd123/

Do these directories exists?  And more likely, are the priveleges set to where apache can read the directories?  Try setting the permissions to: 755.

---

### Post by ScatterBrain on 2005-11-12
First, have you set the proper permissions on the /var/www/XXXX directories?  Basically you need to make sure that all the directories you create have _at_least_ 755 permissions.

Second, Is there an index file in those directories?  Even if the index file is empty, it still needs to exist.

Lastly, add these configuration lines to your vhosts config file after the 'AllowOverride None' statement for both vhosts:

```
Order Allow,Deny
Allow from All
```

---

### Post by s0c0 on 2005-11-13
The permissions were set to 744.  I was unware that write perms were needed for this.  I also added the extra lines to the conf file.  Now the first site listed in the virtual domains "chrisbsd123" shows even when I type-in debianchris.  I'm betting that if I swapped the order in which these two sites are listed that the other would display inplace of the other.

Any ideas?

---

### Post by ScatterBrain on 2005-11-14
[QUOTE=s0c0]The permissions were set to 744.  I was unware that write perms were needed for this.[/QUOTE]

Did you change the permissions to 755?  You shouldn't need write except for the owner of the files/directories.  For the rest of the users/groups, all you need is read on files and read+execute on directories.  (Generally)  This equates to 755 for directories and 744 for files.

[QUOTE=s0c0] I also added the extra lines to the conf file.  Now the first site listed in the virtual domains "chrisbsd123" shows even when I type-in debianchris.  I'm betting that if I swapped the order in which these two sites are listed that the other would display inplace of the other.

Any ideas?[/QUOTE]

I'm betting you don't have a DNS listing for either website.  Add this to the bottom of your /etc/hosts file:

```
[IP ADDRESS OF WEB SERVER]   chrisbsd123
[IP ADDRESS OF WEB SERVER]   debianchris
```

And try the websites again by name.  I bet they both work now.  If they do, then you can either leave them that way (if your wanting these sites only for your own use) or you'll need to costruct a DNS server/have DNS hosted for you (so that other people can get to your sites).

---

### Post by s0c0 on 2005-11-14
I am running a Bind9 Master DNS Server on this box.  Could this need to be modified in addition to the hosts file?

I already have the hosts entry.  It looks like this: 

192.168.1.102  debianchris
192.168.1.102  chrisbsd123

---

### Post by ScatterBrain on 2005-11-15
[QUOTE=s0c0]I am running a Bind9 Master DNS Server on this box.  Could this need to be modified in addition to the hosts file?

I already have the hosts entry.  It looks like this: 

192.168.1.102  debianchris
192.168.1.102  chrisbsd123[/QUOTE]


Hmmmm.  By "this box" do you mean the web server, or the machine you're trying to access the web server from?  I'm assuiming that there are two different machine that we're dealing with.  The web server and the client.

In my vision of the setup:

```
[COLOR="Purple"]Machine one[/COLOR]: Web Server running Apache, DNS, other server apps
[COLOR="Purple"]Machine two[/COLOR]: Client running firefox or other browser. 

```

I'm also assuming the client is a Linux machine and not running Windows.  If it is, then there is no /etc/hosts.  We'll need to look elsewhere later if it is running Windows.

On the client, if you have those entries in your /etc/hosts file, then you should see different sites when you use different names.  (Assuming that the data in the vhosts index.html files is different.)  DNS isn't a problem here, nor is it required with the /etc/hosts entries.

If you don't have those entries in your /etc/hosts on the client, then the DNS server that the client machine uses will need to have some entries that point to the proper place.  If those enties are already present, are you using the domain name in the browser?

---

### Post by LordHunter317 on 2005-11-15
[QUOTE=ScatterBrain]I'm also assuming the client is a Linux machine and not running Windows.  If it is, then there is no /etc/hosts.  We'll need to look elsewhere later if it is running Windows.[/quote]FWIW, Windows NT has a hosts file in %SYSTEMROOT%\system32\drivers\etc\hosts.

---

### Post by s0c0 on 2005-11-15
The client machine is Windows 2000.  The server is running the apache and bin9.  I can't even view the two different sites using the browser on my debian server let alone the client.

No I am not using a domain name in the browser these are not FQDN.  As I am testing this out before purchasing the domain names we will be using.  Is this the issue then?  If so what needs to be placed the my dns conf file?

---

### Post by LordHunter317 on 2005-11-15
[QUOTE=s0c0]The client machine is Windows 2000.  The server is running the apache and bin9.  I can't even view the two different sites using the browser on my debian server let alone the client.[/quote]You are using hte entries in /etc/hosts, that you added, correct?

And you did restart the server after adding them, correct?

You must use resovable hostnames (even if via only /etc/hosts) with name-based virtualhosting.

---

### Post by s0c0 on 2005-11-15
Doh!

So thats why its not working, I'm not using FQDN.  Okay...  Well yahoo domains are only 2.99 a pop/yr.  Might as well try this out now.

---

### Post by LordHunter317 on 2005-11-15
You don't have to use a FQDN.

You can add an entry to /etc/hosts on the server and client:```
192.168.0.1 site1 
192.168.0.1 site2
```

And everything will work, provided the ServerName given in Apache is exactly 'site1' above., and you access the site via [http://site1](http://site1)

You don't need Internet-resolvable FQDNs to test this.  You just need resovable hostnames.  Internal is fine.

---

### Post by s0c0 on 2005-11-15
Okay I do have those entries in my servers /etc/hosts file.

It is still only showing the first site listed in the virtual hosts portion of apache 1.3.

Another interesting thing is if I place the following:
> 
<Virtual Host *>
</Virtual Host>

 in before the other 2 virtual host entries it brings me to the /var/www directory and I can select either debianchris or chrisbsd123.  Once I select one of those directories I am taken to the proper index page.  However if I type [http://debianchris/](http://debianchris/) into the browser and then choose chrisbsd123 the address bar displays [http://debianchris/chrisbsd123](http://debianchris/chrisbsd123) and if I go to the /var/www directory through [http://chrisbsd123](http://chrisbsd123) and select debianchris it displays as [http://chrisbsd123/debianchris](http://chrisbsd123/debianchris).

---

### Post by s0c0 on 2005-11-15
On a hunch of mine I decided to install Apache 2.0 instead.  I must admit I had been intimidated by the new conf files and such, but after reading up on it for about an hour I decided to setup virtual hosts.

I added the following to /etc/apache2/sites-available/default:
```

NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@debianchris
        ServerName debianchris123
        DocumentRoot /var/www/debianchris123/www/
</VirtualHost>

<VirtualHost *:80>
        ServerAdmin webmaster@debianchris
        ServerName chrisbsd123
        DocumentRoot /var/www/chrisbsd123/www/
</VirtualHost>

```

After this I verified that the proper entries were in my /etc/hosts file and reload/restarted apache.  It works :p !!!!!!!!  Still not sure why it wouldn't work with 1.3, but I don't really care any more.  Thanks for your attention folks.

Next on the agenda: e-mail server!

---

### Post by LordHunter317 on 2005-11-16
My guess as to why it didn't work with 1.3 is your NameVirtualHost directive didn't match your VirtualHost directives.  IIRC, they must match exactly.

---

### Post by bouncy35 on 2006-05-20
I have a similar problem. I am running Apache2 on Ubuntu

I have three sites i am trying to host.

*domain -> desired file location*
[wctm.org.uk]("http://wctm.org.uk") -> /var/www/wctm
[blueexpanse.co.uk]("http://blueexpanse.co.uk") -> /var/www/blueexpanse
[blueexp.vm.bytemark.co.uk]("http://blueexp.vm.bytemark.co.uk") -> /var/www/default

I have set up three separate files in /etc/apache2/sites-available and symlinked them into sites-enabled.

The problem occurs as all three domain names all point to the same directory in /var/www

the links above are live so you can try it out.

the three virtual host files are below:

default:
```
NameVirtualHost *

<VirtualHost *>
	ServerAdmin root@localhost
	ServerName blueexp.vm.bytemark.co.uk
	ServerAlias www.blueexp.vm.bytemark.co.uk
	DocumentRoot /var/www/default
	<Directory /var/www/default>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		Allow from All
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
</VirtualHost>

```

wctm:
```
<VirtualHost *>
	ServerAdmin root@localhost
	ServerName wctm.org.uk
	ServerAlias www.wctm.org.uk
	DocumentRoot /var/www/wctm
	<Directory /var/www/wctm>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
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
</VirtualHost>

```

blueexpanse:
```
<VirtualHost *>
	ServerAdmin root@localhost
	ServerName blueexpanse.co.uk
	ServerAlias www.blueexpanse.co.uk
	DocumentRoot /var/www/typo3
	<Directory /var/www/typo3>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
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
</VirtualHost>

```

All the permissions on the directories are at 755. I have googled this to death and i cannot see why this is not working.

Any ideas anyone?

](*,) 

Thanks

Alex

---

