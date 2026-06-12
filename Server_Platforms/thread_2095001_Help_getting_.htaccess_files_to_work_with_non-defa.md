---
title: "Help getting .htaccess files to work with non-default virtual hosts"
date: 2012-12-15
forum: Server Platforms
---

### Post by Breadstick on 2012-12-15
Hi guys,

I am developing locally a number of sites (numerous localhosts), on an ubuntu LAMP stack (apache 2.2) which require some levels of authectication.

I have successfully installed the module which authecticates the users and have verified that it works when I visit [http://localhost/](http://localhost/) everything works as it should.

However, I can't for the life of me to get it to work for my non-default sites, when I add a .htaccess to the folder, the server denies access (to say myothersite.localhost) as it should but it does not go through the authectication proceedure.

The authectication utilises a cookie, and is done through an external site which is all handled my a module which has been successfully installed.

This is the code I have under /etc/apache2/sites-available/default (ie this works perfectly for localhost):

```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	AACookieKey "##########################"

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

This is the code under /etc/apache2/sites-available/myothersite.localhost which does not resul in proper auhectication:

```

<VirtualHost *:80>
DocumentRoot /home/luke/workspace/MYOTHERSITE
ServerName www.myothersite.localhost
ServerAlias myothersite.localhost

	AACookieKey "###############"

	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>

	<Directory "/home/luke/workspace/MYOTHERSITE/">
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

</VirtualHost>

```

The only sticking point I can think of is that the default document root is under the protected /var/www/, while my other sites are in my home folder.

Any suggestions? Thankyou very much for your help.

---

### Post by SeijiSensei on 2012-12-15
Usually /home/username has 700 permissions, granting only the user the right to access her own files and directories.  Try

```

cd /home
sudo chmod go+x luke
sudo chmod go+rx luke/workspace

```

---

### Post by Breadstick on 2012-12-15
> **SeijiSensei said:**
> Usually /home/username has 700 permissions, granting only the user the right to access her own files and directories.  Try

```

cd /home
sudo chmod go+x luke
sudo chmod go+rx luke/workspace

```

Thanks, but those commands don't seem to have done the trick.

Am I being silly having my virtual hosts roots external to /var/www/?

Will I save a lot of headaches in the future by just moving them into root's control?

---

### Post by SeijiSensei on 2012-12-16
Show us the /var/log/apache2/access.log and error.log entries from a failed attempt.

Also
```

cd /
sudo ls -lR
cd luke
sudo ls -lR

```

Put the results in [noparse]```

```[/noparse] tags for clarity.

---

### Post by Breadstick on 2012-12-28
Thanks for the continued help.

Unfortunately, there were no relevant error messages in either log file.

I have decided to just move by development over to /var/www/, as it works as expected under that root and it will prob save headaches in the long run.

I hope you having a good holiday, and wish you a happy new year :)

---

