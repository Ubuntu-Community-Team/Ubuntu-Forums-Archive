---
title: "403 forbidden virtualhost"
date: 2010-07-03
forum: Server Platforms
---

### Post by PauGNU on 2010-07-03
Hi all,

I'm trying to set up a local server using apache/mysql/etc. After a fresh install, I can work without any problem using /var/www as a base directory.

The problem comes when I try to use virtualhosts. At this moment, my /etc/apache2/sites-available/default file is this:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

<VirtualHost *:80>
	DocumentRoot /usr/share/phpmyadmin
	ServerName phpmyadmin.local
</VirtualHost>

<VirtualHost *:80>
	DocumentRoot /home/pau/webs/barcelonadecideix
	ServerName barcelonadecideix.local
</VirtualHost>

<VirtualHost *:80>
	DocumentRoot /home/pau/webs/gnulinux
	ServerName gnulinux.local
</VirtualHost>
```

And the /etc/hosts file:

```
127.0.0.1	localhost
127.0.1.1	lucid-xps phpmyadmin.local barcelonadecideix.local  gnulinux.local

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

But whenever I try to go to [http://barcelonadecideix.local](http://barcelonadecideix.local) or [http://gnulinux.local](http://gnulinux.local), I get always the same error:

> Forbidden
You don't have permission to access / on this server.

The error.log says (after trying to go to [http://barcelonadecideix.local):](http://barcelonadecideix.local):)
> [Sat Jul 03 14:37:02 2010] [crit] [client 127.0.1.1] (13)Permission denied: /home/pau/webs/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

I can't understand why it is asking for an .htacces file on /home/pau/webs/ when the main directory is /home/pau/webs/barcelonadecideix/. 

What am I doing wrong?

Thanks!

---

### Post by sjinks on 2010-07-04
This is how Apache works. Your document root is /home/pau/webs/barcelonadecideix/. Apache will test .htaccess file in /, /home, /home/pau, /home/pau/webs, /home/pau/webs/barcelonadecideix.

See [http://httpd.apache.org/docs/2.2/mod/core.html#accessfilename](http://httpd.apache.org/docs/2.2/mod/core.html#accessfilename) for details.

---

