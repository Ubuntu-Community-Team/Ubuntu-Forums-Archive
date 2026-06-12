---
title: "new server and webpage is keeps redirecting to default page"
date: 2015-01-01
forum: Server Platforms
---

### Post by kustomjs on 2015-01-01
Guys
I am working with Ubuntu 12.04.5 LTS and this is brand new server and the webpage keeps redirecting to default when I have the new site configured under /etc/apache2/sites-enabled with site.conf with all correct information.

---

### Post by Doug S on 2015-01-01
In order to help, we will need more information. Perhaps post the actual files.

---

### Post by kustomjs on 2015-01-01
what actual files are you talking about? Because its keeps redirecting to the default page that is listed in /var/www/ and I have tried to move it to /var/www/guest in the apache2 and it just keeps redirecting to /var/www/index.html.

---

### Post by Doug S on 2015-01-01
> **kustomjs said:**
> what actual files are you talking about?Any Apache config files that you added or changed. And any other information about what you have done so far.

---

### Post by kustomjs on 2015-01-01
well if I edit the original apache2 sites enable and add /var/www/guest in it works but I take it out it dont work so if I add unifi.domain.com.conf and enable the sites it dont redirect at all like I want it to.

---

### Post by volkswagner on 2015-01-01
> **kustomjs said:**
> well if I edit the original apache2 sites enable and add /var/www/guest in it works but I take it out it dont work so if I add unifi.domain.com.conf and enable the sites it dont redirect at all like I want it to.


Please post your /etc/apache2/sites-enabled/site.conf


FYI, files should not be saved in sites-enabled. You should create/edit in /etc/apache2/sites-available, then "run sudo a2ensite nameOfconfFileInSitesAvailable" this
will create a link in sites-enabled. You'll also need to restart apache2 after making changes.

---

### Post by kustomjs on 2015-01-02
```
<VirtualHost *:80>
        ServerAdmin webmaster@domain.com
        ServerName unifi.domain.com

        DocumentRoot /var/www/guest/s/default
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/guest/s/default/>
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
```

Here is the original sites default:

```

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
```

---

### Post by volkswagner on 2015-01-02
The configs look good. Either Apache is not properly configured for NameVirtualHosts, or Apache is not aware your config is supposed to be enabled.

Please post output of the following:

```
cat /etc/apache2/ports.conf
```

```
ls -al /etc/apache2/sites-available
```

```
ls -al /etc/apache2/sites-enabled
```

---

### Post by kustomjs on 2015-01-03
```
user@domain:~$ cat /etc/apache2/ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```

```
tim@domain:~$ ls -al /etc/apache2/sites-available
total 24
drwxr-xr-x 2 root root 4096 Jan  1 14:46 .
drwxr-xr-x 7 root root 4096 Dec 23 20:22 ..
-rw-r--r-- 1 root root  951 Jan  1 14:46 default
-rw-r--r-- 1 root root 7469 Feb  6  2012 default-ssl
-rw-r--r-- 1 root root 1264 Jan  1 14:46 unifi.domain.com.conf 
```

```


tim@domain:~$ ls -al /etc/apache2/sites-enabled
total 8
drwxr-xr-x 2 root root 4096 Jan  1 12:24 .
drwxr-xr-x 7 root root 4096 Dec 23 20:22 ..
lrwxrwxrwx 1 root root   26 Jan  1 12:24 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root   42 Jan  1 11:55 unifi.domain.com.conf -> ../sites-available/unifi.domain.com.conf 
```

---

### Post by volkswagner on 2015-01-03
Please make certain this is not a browser cache issue. Clear browser cache, try a different browser, or try from a machine that hasn't browsed the domain yet.

If the issue is not a browser cache problem or some redirect or url rewrite upstream you may want to try a shot in the dark.

Rename the config file as follows:

```
sudo a2dissite unifi.domain.com.conf
```

```
 cd /etc/apache2/sites-available
```
```
sudo mv unifi.domain.com.conf unifi
```
```
sudo a2ensite unifi
```

```
sudo service apache2 restart
```

---

### Post by kustomjs on 2015-01-03
its an not an browser issue I have tried it with 3 different browsers and it all does the same.

---

### Post by Doug S on 2015-01-03
> **kustomjs said:**
> its an not an browser issue I have tried it with 3 different browsers and it all does the same.O.K., but did you try volkswagner's other suggestion?
Myself, I had assumed that this line:```
      ServerName unifi.domain.com 
```was something to hide your actual domain name. Let's say your real domain name is abcdef.com, then myself I would to this:```
<VirtualHost *:80>
        ServerAdmin webmaster@domain.com
        ServerName abcdef.com
ServerAlias *.abcdef.com
DocumentRoot /var/www/guest/s/default
        <Directory />
Options FollowSymLinks
                AllowOverride None
...
```(And I do not know why I can not get the formatting correct for the above).

---

### Post by kustomjs on 2015-01-03
see I dont have issues with my other subnames on my domain just this one.

---

### Post by volkswagner on 2015-01-04
According to your output of listing contents of sites enabled, you don't have any other sub domains. 

I suggest creating a simple index.html file one directory up and edit your host file. My gues is your content in s/default possibly is causing url rewrite or redirect. Your logs should offer some insight. 

We are trying to help, but your not productively contributing.

---

### Post by volkswagner on 2015-01-04
> **kustomjs said:**
> see I dont have issues with my other subnames on my domain just this one.

What does this mean to us? You have not initiated or shared any info pertaining to working sub domains.

---

### Post by kustomjs on 2015-01-04
the subnames off of my domain is on different machines so I dont know why this one isnt working correctly

---

### Post by volkswagner on 2015-01-05
You have made zero effort to respond to my specific suggestions of simplifying web content folder and file name scheme.

I won't waste anymore of my time with your useless one liner responses.

---

### Post by Doug S on 2015-01-05
> **volkswagner said:**
> You have made zero effort to respond to my specific suggestions of simplifying web content folder and file name scheme.

I won't waste anymore of my time with your useless one liner responses.+1. neither will I.

---

### Post by kustomjs on 2015-01-05
wow.... how rude of comments I told you everything that you guys wanted again

If I edit the original sites enable it works(/etc/apache2/sites-available/default) but if you add an different host file (/etc/apache2/sites-available/unifi) it dont redirect how hard is that to understand...

---

