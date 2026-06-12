---
title: "NameVirtualHost *:80 has no VirtualHosts"
date: 2009-02-02
forum: Server Platforms
---

### Post by starfleetcaptainrob on 2009-02-02
Hello I'm getting this error (NameVirtualHost *:80 has no VirtualHosts) when I try to restart Apache2 on my VPS webserver running Ubuntu 8.10.  It was working fine as of Saturday (I did not check it at all yesterday) and suddenly it's not working this morning.  I cannot get to my site at all, it just asks me to download a file.

Here's my VH file under sites-enabled: 

```
# domain: fixmyinternetnow.com
# public: /var/www/public_html/fixmyinternetnow.com/

<VirtualHost *:80>

        # Admin email, Server Name (domain name) and any aliases
        ServerAdmin rob@fixmyinternetnow.com
        ServerName fixmyinternetnow.com
        ServerAlias www.fixmyinternetnow.com

        # Index file and Document Root (where public files are located)
        DirectoryIndex
        DocumentRoot /var/www/public_html/fixmyinternetnow.com
        <Directory />
        AllowOverride All
        </Directory>

        # Custom log file locations
        LogLevel warn
        ErrorLog /var/www/public_html/fixmyinternetnow.com/logs/error.log
        CustomLog /var/www/public_html/fixmyinternetnow.com/logs/access.log combined

</VirtualHost>

```

And my ports.conf:

```
NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```

Plus the end of my Apache2.conf file:

```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

NameVirtualHost *:80

<IfModule mod_ssl.c>
        NameVirtualHost *:443
</IfModule>
ServerName localhost


```

I've searched around the forums, but none of the fixes seem to work for me.  The weirdest part is it was working fine as of two days ago and I haven't made any changes to the server.  I'm also the only one who has access to this server.  Let me know if there's any additional info I should post.  Thanks in advance!

---

### Post by starfleetcaptainrob on 2009-02-02
A little update to this problem.  After talking to a friend I commented out the NameVirtualHost *:80 line in my apache2.conf file.  This gets rid of the error on restarting apache2.  However, I still cannot access the web page.  Not sure if I mentioned this before, but when I go to my site the browser asks me to save or open a file and each time it's a different file.  For example SzlInRuG.part or HUUD1OEs.part.  Anyone have any ideas??

---

### Post by SeaborneClink on 2009-02-02
Here's my config settings,

sites-available
```

<VirtualHost *>
...
...
</VirtualHost>

```

Then in your ports.conf, change 
```
NameVirtualHost *:80
```
to
```
NameVirtualHost *
```

The page trying to save seems odd. Is it a php file? is php installed?

---

### Post by starfleetcaptainrob on 2009-02-02
No dice, still the same problem.  Yup, php5 is installed.

---

### Post by kustomjs on 2009-02-03
here is what you need to do:
go to your /etc/apache2/sites-available

make a file like this yourdomain.com.conf with this:

<VirtualHost *:80>
ServerName yourdomain.com
DocumentRoot /var/www/yourdomain/
</VirtualHost> 

then go to /etc/apache2/ports.conf

and put in Listen your ip address or router ip:80 like this(Listen 192.168.1.5:80)

then go to /etc/apache2/apache2.conf

put in your ServerName  yourservername  note you will put this at the end of the file.


after you do all this type this in command line sudo /etc/init.d/apache2 restart

also you need to edit your root document under: /etc/apache2/sites-available/default  like this:

NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName name of your server
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

     Alias /fckeditor/ /usr/share/fckeditor/
    <Directory "/usr/share/fckeditor/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order allow,deny
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



also this is how I got my server currently setup.

---

### Post by rsrajesh on 2010-04-04
Hi,
I think you wud have solved the problem by now, but next time if the error (asking to save the file as ***.part), just try this:

clear the history of firefox... it worked for me.  but i dont know the logic behind it...!!!

---

### Post by blackhawx on 2010-06-21
> **kustomjs said:**
> here is what you need to do:
go to your /etc/apache2/sites-available

make a file like this yourdomain.com.conf with this:

<VirtualHost *:80>
ServerName yourdomain.com
DocumentRoot /var/www/yourdomain/
</VirtualHost> 

then go to /etc/apache2/ports.conf

and put in Listen your ip address or router ip:80 like this(Listen 192.168.1.5:80)

then go to /etc/apache2/apache2.conf

put in your ServerName  yourservername  note you will put this at the end of the file.


after you do all this type this in command line sudo /etc/init.d/apache2 restart

also you need to edit your root document under: /etc/apache2/sites-available/default  like this:

NameVirtualHost *:80
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName name of your server
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

     Alias /fckeditor/ /usr/share/fckeditor/
    <Directory "/usr/share/fckeditor/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order allow,deny
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



also this is how I got my server currently setup.

I can confirm this worked for me! Thank you for this wonderful post! :popcorn:

---

### Post by JamieKitson on 2010-06-23
I was getting this error because I had two NameVirtualHost lines, one in my sites-enabled file and one in my ports.conf file.

Try grepping for this:

```
jamie@bible:/etc/apache2$ grep NameVir * -R
ports.conf:NameVirtualHost *:80
ports.conf:    # If you add NameVirtualHost *:443 here, you will also have to change
sites-enabled/bible:#NameVirtualHost *
```
See:

[http://wiki.apache.org/httpd/CommonMisconfigurations](http://wiki.apache.org/httpd/CommonMisconfigurations)

---

### Post by jp19online on 2010-09-19
Just confirming, I too had similar problem, which got resolved by removing the duplicate NameVirtualHost *:80  line (removed it from port.conf).
 
Probably the other solution essentially fixes this.
 
Thanks all for this useful thread.

---

### Post by iyayan on 2010-11-16
just remove

NameVirtual host *:80 on "ports.conf"

---

### Post by M0rDoK on 2011-03-22
> **iyayan said:**
> just remove

NameVirtual host *:80 on "ports.conf"

Works for me. Thanks

---

### Post by oaksterdam on 2011-09-09
worked for me too.

many thanks.

(I also had a problem with an request tracker installation that was removed and then left an Include and RedirectMatch in the ports.conf.  Removing those may have helped too.)

---

