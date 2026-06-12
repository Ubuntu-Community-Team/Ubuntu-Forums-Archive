---
title: "Apache2 not starting"
date: 2007-07-02
forum: Server Platforms
---

### Post by danieljay on 2007-07-02
I have had ubuntu installed on my laptop for some time now. I am trying to setup a very basic testing server for some local website coding on my laptop. I have installed and removed both apache and apache2 several times trying to get things to properly run. I have completely removed apache 1.3 and have installed apache2. When I try and connect to [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) or [http://192.168.1.100](http://192.168.1.100) I cannot access the server.

I then go to the terminal and run: sudo /etc/init.d/apache2 stop and I get "* Stopping web server (apache2)...                                                                                                                   [ OK ]"

I then run sudo /etc/init.d/apache2 start and it returns blank. I then try to connect again and nothing.

I have installed all of the php5 packages that I would like including the libapache2-mod-php5 (If I remember the name correctly)

Any ideas?

---

### Post by duckmannz on 2007-07-02
Check your log files, general ones like /var/log/syslog or apache specific ones like /var/log/apache2/error.log

If there's anything in there that you don't understand then please post it ad verbatim

---

### Post by danieljay on 2007-07-02
The /var/log/apache2/error.log file is completely empty. The /var/log/syslog does not seem anything different.

This is the file in sites-enabled which is a symlink:
> NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
#	DocumentRoot /var/www/
	DocumentRoot /home/daniel/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
#	<Directory /var/www/>
	<Directory /home/daniel/public_html/>
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

Both the access.log and error.log file in /var/log/apache2/ have a filesize of 0.

---

### Post by duckmannz on 2007-07-02
When logged in as root, what do you get if you run
```
 apache2 -t
```
?

You could also try
```
apache2 -E ./error.log
```

apache -h shows:
```
Usage: apache2 [-D name] [-d directory] [-f file]
               [-C "directive"] [-c "directive"]
               [-k start|restart|graceful|stop]
               [-v] [-V] [-h] [-l] [-L] [-t] [-S]
Options:
  -D name           : define a name for use in <IfDefine name> directives
  -d directory      : specify an alternate initial ServerRoot
  -f file           : specify an alternate ServerConfigFile
  -C "directive"    : process directive before reading config files
  -c "directive"    : process directive after reading config files
  -e level          : show startup errors of level (see LogLevel)
  -E file           : log startup errors to file
  -v                : show version number
  -V                : show compile settings
  -h                : list available command line options (this page)
  -l                : list compiled in modules
  -L                : list available configuration directives
  -t -D DUMP_VHOSTS : show parsed settings (currently only vhost settings)
  -S                : a synonym for -t -D DUMP_VHOSTS
  -t                : run syntax check for config files

```

---

### Post by danieljay on 2007-07-02
sudo apache2 -t returns:
> apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/httpd.conf: No such file or directory

I changed to the /etc/apache2/ and there is no httpd.conf file

Would I need to then open up synaptics or apt and try to force a reinstall? How would I do that?

---

### Post by duckmannz on 2007-07-03
I know this is Ubuntu but I would resort to the CLI:
```
apt-get remove --purge apache2 -y
apt-get install apache2
```

---

### Post by scxtt on 2007-07-03
try touching it, **sudo touch /etc/apache2/httpd.conf** -- it's basically a legacy file anyway ... the bulk of the config is in /etc/apache2/apache2.conf ...

---

### Post by kelster on 2007-07-06
Hey Daniel did you figure this out?  I am doing the same thing you are on a laptop and having identical issues.  I followed this guide:
[http://www.debianadmin.com/apache2-web-server-with-php-support-in-ubuntu.html](http://www.debianadmin.com/apache2-web-server-with-php-support-in-ubuntu.html) ,

and tried the steps outlined by the previous posters,

to no avail.  I did notice before I uninstalled apache 1.3.34 that when I could log on to the localhost that on the bottom of the directory page it said apache 1.3.34 port 80.  So obviously apache2 wasn't being used.  Also after I did uninstall apache 1.3.34 then the localhost was unavailable, "unable to connect."  Which made sense since the editing I did in the apache2 confs didn't transfer to that page.  All I wanted was to test out some php includes on my computer.  Ubuntu, is that too much to ask?  LOL.

Kel

---

### Post by koenn on 2007-07-06
> # DocumentRoot /var/www/
DocumentRoot /home/daniel/public_html/
I suppose this requires www-data, or whatever account apache2 runs with, to have read/execute rights on /home/daniel/public_html/, which is not so by default; you'll have to chmod it.

---

### Post by danieljay on 2007-07-07
No I have not gotten this to work just yet.

I ran:
```
sudo apt-get remove --purge apache2 -y
sudo apt-get install apache2
```

Then I ran:
```
sudo touch /etc/apache2/httpd.conf
ls -l /etc/apache2/
```
I ran the ls -l just to make sure that the file was created and with the same permissions as the other files in the dir.

Next I ran:
```
sudo apache2 -t
```
Which returned Syntax OK

Apache was setup to run as my local user but have since changed it back to www-data and reverted to the original default enabled site file.(Which put the doc root back to /var/www)

I checked out /var/log/apache2/ and noticed that I had:
```
daniel@daniel704:/var/log/apache2$ ls -l
total 8
-rw-r----- 1 root adm   0 2007-07-03 14:07 access.log
-rw-r----- 1 root adm 704 2007-07-03 12:37 access.log.1
-rw-r----- 1 root adm   0 2007-07-03 14:07 error.log
-rw-r----- 1 root adm 165 2007-07-03 12:40 error.log.1
```

I have tried to start apache since 7-3 so apparently there are no errors being processed by apache. The contents of error.log.1 are:
```
daniel@daniel704:/var/log/apache2$ cat error.log.1 
[Tue Jul 03 12:25:04 2007] [notice] Apache/2.2.3 (Ubuntu) configured -- resuming normal operations
[Tue Jul 03 12:40:14 2007] [notice] caught SIGTERM, shutting down
```

I apparently got apache to run once on 7-3 since the access.log.1 since there are records listed.

Any ideas?

---

### Post by danieljay on 2007-07-07
Well after some more messing around with this I ended up removing all php5 related packages and all apache packages that I had installed. I then deleted the /etc/init.d/apache2 file and then deleted my old /etc/apache and /etc/apache2 folders that were left there. I then re-installed apache2 and noticed that it had started up correctly. Then I downloaded and installed all php5 extensions that I wanted and everything looks like it is working fine now.

---

