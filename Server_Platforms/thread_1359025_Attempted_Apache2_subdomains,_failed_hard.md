---
title: "Attempted Apache2 subdomains, failed hard"
date: 2009-12-19
forum: Server Platforms
---

### Post by _goatboy_ on 2009-12-19
Earlier today, I attempted to set up local-only subdomains on my home server for testing purposes.  After trying several different methods, I decided to sleep on it and try again tomorrow.  I decided to check out the site one more time to make sure nothing went wrong and as fate would have it, a ***lot*** went wrong.

Right now, I cannot view the site through a browser on another machine.  The internal IP is 192.168.11.6, and that brings up an Object Not Found error.  However, if I try to view 192.168.11.6/~goatboy (or some other user) it works just fine.

I'll include my "sites-allowed/default" below, for what it's worth.  I've looked through it a few times, but since I'm not sure what a "correct" file looks like, I don't know what to look for.

[html]<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        UserDir public_html

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews +Includes
                XBitHack On
                AllowOverride All
                Order allow,deny
                allow from all
                AddType image/x-icon .ico
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

</VirtualHost>[/html]Other items of note:


[LIST]
[*]I have restored my "hosts" file to the best of my knowledge, and can supply it if needed (ditto any other file, save /etc/passwd|shadow  ;])
[*]My permissions are set correctly, since I did not change them before the error occurred.  I temporarily set the /var/www/ directory to 777 to see if this was the case, and it is not.
[*]I have made sure the files exist within the DocumentRoot (/var/www/) directory
[*]Software:
[LIST]
[*]OS:  Ubuntu 9.10
[*]Apache: 2.1.12
[/LIST]
 
[/LIST]
Does anyone see any immediate errors that would cause this Object Not Found error?  If so, how would I fix it?  I realize these posts are often frustrating and I am a little ashamed to be asking for help, but once again, anything else you need (within reason) will be supplied.

---

### Post by Adina on 2009-12-19
I'm not sure if it helps, but this is the default sites-availible file that I use.


```
NameVirtualHost *
<VirtualHost *>
	#ServerName yourdomainname.com
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/yourdomain/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/yourdomain/>
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
```

---

### Post by nsche on 2009-12-19
Goatboy..
I note that you do not seem to have a  Servername line in your virtual hosts declaration.  If I were you I would start making it work using a virtual hosts declaration containing only the minimal needed like this:
```

<VirtualHost *:80>
  <Directory "/somewhere">
    AllowOverride None
    Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
    Allow from all
  </Directory>
  ServerName MyServer
  DocumentRoot /MyServerDir
</VirtualHost>

```

I then put an entry in /etc/hosts like this
```

127.0.0.1	localhost MyServer

```
I can then access the server at [http://MyServer](http://MyServer).  I also have a default virtual host (part of the apache2 setup) that catches the [http://localhost](http://localhost) traffic.

YMMV
Norm

---

