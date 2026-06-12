---
title: "Can't manage to finish Drupal install"
date: 2011-05-17
forum: Server Platforms
---

### Post by Kivech on 2011-05-17
Hi all,

I have installed Drupal through this tutorial: [http://drupal.org/node/326964](http://drupal.org/node/326964)

It seems to be a good one, albeit the instructions to edit the default site file of apache could be a bit clearer.

My problem is that everything seems to go well until I try to actually start the Drupal installation by going to [http://localhost/drupal6/install.php](http://localhost/drupal6/install.php)

I checked and rechecked (also against other tutorials) but I'm fairly confident I followed the instructions properly. However on my system (11.04) the indicated hyperlink leads to an empty page.
I even checked if the directory exists /usr/share/drupal6/ and I can confirm it is actually there. :P :confused:

Pasting the URL in a terminal results in this message:
> bash: [http://localhost/drupal6/install.php:](http://localhost/drupal6/install.php:) No such file or directory
Same goes for the directory itself.

I recon something must have gone wrong with my editing of the default file. It now looks like this:
> <VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /usr/share/drupal6
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /usr/share/drupal6/>
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


I'm pretty new to web server configuration and such, so I have no idea what would be right or wrong.

Also, when I restart apache, it gives me this message:
>  * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]


Could this by any chance be related?

Any help or hints where to look for a solution would be highly appreciated. (Yes, I am desperate)

---

### Post by Kivech on 2011-05-17
Ok, I had a bright moment... (yes, it happens at times, don't tell my wife), and I tried [http://localhost/install.php]("http://localhost/install.php")

Color my blind,... it works!

Now I can see how obvious it was, but anyway.

Thanks for those reading. I'm going to finish my Drupal installation.):P

---

### Post by nublaii on 2011-05-18
Watch out for problems with Php 5.3.*, drupal6 can choke on it

---

### Post by Kivech on 2011-05-18
Thanks for the tip mate.

After giving it all a try, I think I will go for the manual install now. At least I know it all works (also hardware wise).

I have to admit that I don't really like the default way of installing the way Ubuntu does it.

Cheers!

---

### Post by sombrancelha on 2011-05-25
> **Kivech said:**
> 
<VirtualHost *:80>
ServerAdmin webmaster@localhost

DocumentRoot /usr/share/drupal6
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /usr/share/drupal6/>
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

ErrorLog ${APACHE_LOG_DIR}/error.log

# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn

CustomLog ${APACHE_LOG_DIR}/access.log combined

Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>

</VirtualHost>


When you managed to get it working, was your edited file just like the above? I am getting broken links erros.

---

### Post by Kivech on 2011-05-25
> **sombrancelha said:**
> When you managed to get it working, was your edited file just like the above? I am getting broken links erros.

Yes, I didn't change anything in my configuration files, I just tried a different address to find the Drupal install page.

You want to share what broken link errors you are getting? Maybe someone can help you out.
If it is not too complex I might even have a go at it. :P

I should add:

Did you follow the tuturial?
What version of Ubuntu are you using?

Those might make a difference from my situation.
Also, I am on x64. Not sure if it makes a difference, but it might.

---

