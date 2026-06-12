---
title: "ubuntu server apache 2 wont load pictures from sub directory"
date: 2013-01-14
forum: Server Platforms
---

### Post by ThaDoctor99 on 2013-01-14
Hey All.

I have this strange problem with apache running on a VPS server I bought for the purpose of running a website.
Well and perhaps other things as well, but when I try to load any pictures on the server in the root it just says that I am not allowed to go and load those pictures.
You can see the errors as well as I can if you visit [http://ziggy-dog.eu](http://ziggy-dog.eu) and view the source and click on one of the image links.

// ThaDoctor99

---

### Post by volkswagner on 2013-01-14
What are the permissions of the folder and files?  They need to be readable by apache2 user (www-data).

```
ls -l /path/to/folder
```

---

### Post by tgalati4 on 2013-01-14
```
sudo chown -R www-data:www-data /var/www/picturedirectorythatisgivingyoutrouble
```

---

### Post by ThaDoctor99 on 2013-01-14
I suppose it makes sense to make www-data the owner, wonder why I didn't think of that.
But it seems it didn't quiet work.
Perhaps I should do some more research into this command.
Although I have done these things it still doesn't seem to work.
I have never really used apache so much before, so I am not very fluent in the config files.

---

### Post by lisati on 2013-01-14
I took a look at the page, and ended up with a blank screen. I was able to see the the references to the images in the page source, but attempting to access the images gave me a message "You don't have permission to access /images/clothing.jpg on this server."

Your apache log file and error log might be able to give you some clues as to what's happening.

---

### Post by ThaDoctor99 on 2013-01-14
Hmm That indicates that the system is actively denying the server access to that directory, although I just did try to change the owner and all that.

---

### Post by volkswagner on 2013-01-14
> **ThaDoctor99 said:**
> Hmm That indicates that the system is actively denying the server access to that directory, although I just did try to change the owner and all that.


Please post output of the following, change to match your directory.

```
ls -alt /path/to/folder
```

---

### Post by tgalati4 on 2013-01-14
You have to restart the apache server after making changes.  (Always.)

```
sudo service apache2 restart
```

---

### Post by volkswagner on 2013-01-15
> **tgalati4 said:**
> You have to restart the apache server after making changes.  (Always.)

```
sudo service apache2 restart
```

This is not required when changing file permissions.  Apache2 does not cache all the permissions for all files on your system.

It appears the directory is not readable.  Even if it is owned by www-data, if the permissions don't have the read bit set... permission will still be denied.

---

### Post by ThaDoctor99 on 2013-01-15
Hmm Yeah I did just to test out stuff set the permission to 777 on the files.

---

### Post by SeijiSensei on 2013-01-15
There are two levels of security involved when using Apache.  One is the OS permissions on the directory where the files are stored.  However Apache itself restricts what directories may be listed and which files may be displayed.  The default is very restrictive; only /var/www and its subdirectories can be displayed.  

The OP hasn't really told us where the files are located or the contents of the relevant <Directory> stanza in the configuration file for this directory.  Unless there is an "Options Indexes" entry in this stanza, the directory cannot be listed except via an "index" file like "index.html" or "index.php".  OP, I suggest looking at this explanation of the [Options directive]("http://httpd.apache.org/docs/2.2/mod/core.html#options").

---

### Post by ThaDoctor99 on 2013-01-15
Hmm I have all my data in a subdirectory under /var/www/ziggy-dog.eu/public_html/ 

Where should I go to add the configuration for that directory and what should I call that directory in the configuration 
my images live at /var/www/ziggy-dog.eu/public_html/images/ 

I am not really that good with apache, and find the documentation really messy.

---

### Post by tgalati4 on 2013-01-15
Page source shows:  [http://ziggy-dog.eu/images/clothing.jpg](http://ziggy-dog.eu/images/clothing.jpg)

What is your root web directory set to in your apache configuration file?

Is /var/www set to root directory or is /var/www/public_html set to root directory?

---

### Post by eenofonn on 2013-01-16
> **tgalati4 said:**
> Page source shows:  [http://ziggy-dog.eu/images/clothing.jpg](http://ziggy-dog.eu/images/clothing.jpg)

What is your root web directory set to in your apache configuration file?

Is /var/www set to root directory or is /var/www/public_html set to root directory?
just to clarify they're talking about DocumentRoot :)

can you print the information for your virtualhost 

```

cat /etc/apache2/sites-enabled/site

```

Where site=the name of your virtualhost (if you haven't modified it you should have a file named "000-default"

e.g.
```

cat /etc/apache2/sites-enabled/000-default

```

---

### Post by ThaDoctor99 on 2013-01-16
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


is the in the /etc/apache2/sites-enabled/000-default.

---

### Post by volkswagner on 2013-01-16
> **ThaDoctor99 said:**
> <VirtualHost *:80>
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


is the in the /etc/apache2/sites-enabled/000-default.

This does not jive with the directory in question.

> **ThaDoctor99 said:**
> Hmm I have all my data in a subdirectory under /var/www/ziggy-dog.eu/public_html/ 

Where should I go to add the configuration for that directory and what should I call that directory in the configuration 
my images live at /var/www/ziggy-dog.eu/public_html/images/ 

I am not really that good with apache, and find the documentation really messy.

Have you added your own virtualhost file?

Please post output:

```
ls /etc/apache2/sites-enabled
```

Please read examples offered.  Often times members offer help in the form of generic info, which in turn you need to apply to your specific situation.

Please also post output of:

```
ls -al /var/www/ziggy-dog.eu
```

---

### Post by ThaDoctor99 on 2013-01-16
In /var/www/ziggy-dog
there is a error.log (which should not be there.)
and then directories public_html and logs, with 744

in the other there is only 000-default and ziggy-dog.eu

---

### Post by volkswagner on 2013-01-16
> **ThaDoctor99 said:**
> In /var/www/ziggy-dog
there is a error.log (which should not be there.)
and then directories public_html and logs, with 744

in the other there is only 000-default and ziggy-dog.eu

I don't know why you're reluctant to post what is requested.  Perhaps someone else can help you with their crystal ball.

---

### Post by ThaDoctor99 on 2013-01-16
I just have a little problems with getting a listing...
Out of the vps.

---

### Post by tgalati4 on 2013-01-16
Fix your DocumentRoot.

---

### Post by volkswagner on 2013-01-16
> **ThaDoctor99 said:**
> I just have a little problems with getting a listing...
Out of the vps.

How are you accessing the server, ssh, putty?  You should be able to copy and paste with either solution.

---

### Post by ThaDoctor99 on 2013-01-16
I have ssh inside tmux (d'oh) Hmm... Although I did take pictures :D

---

### Post by ThaDoctor99 on 2013-01-16
[http://imageshack.us/photo/my-images/703/82289129.png/](http://imageshack.us/photo/my-images/703/82289129.png/)
[http://imageshack.us/photo/my-images/29/screenshotbtf.png/](http://imageshack.us/photo/my-images/29/screenshotbtf.png/)

are the two pictures...

---

### Post by volkswagner on 2013-01-16
Those pictures are difficult to read.

If you need help copy/paste in a terminal session, use the shift key.

copy = <shift> + <ctrl> + c
paste = <shift> + <ctrl> + v

Please post your vhost file for the site in question and the permissions for said root folder.



```
cat /etc/apache2/sites-available/ziggy-dog.eu
```

```
ls -al /var/www/ziggy-dog.eu/public_html
```

---

### Post by ThaDoctor99 on 2013-01-17
/etc/apache2/sites-enabled/ziggy-dog.eu

```

<VirtualHost *:80>
	ServerAdmin Tobias.private@gmail.com
	ServerName ziggy-dog.eu
	ServerAlias www.ziggy-dog.eu
	DocumentRoot /var/www/ziggy-dog.eu/public_html
	<Directory /var/www/ziggy-dog.eu/public_html>
		Options Indexes FollowSymLinks
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>
	ErrorLog /var/www/ziggy-dog.eu/logs/error.log
	CustomLog /var/www/ziggy-dog.eu/logs/access.log combined
</VirtualHost>

```

ls -al /var/www/ziggy-dog.eu/public_html

```

  total 16
  drwxr-xr-x 3 www-data www-data 4096 Jan 14 15:16 .
  drwxr-xr-x 4 root     root     4096 Jan 12 21:20 ..
  drw-r--r-- 2 www-data www-data 4096 Jan 13 14:16 images
  -rw-r--r-- 1 www-data www-data  266 Jan 14 15:16 index.php

```

---

### Post by volkswagner on 2013-01-17
Your directory is not executable.

You need to make the permissions read and executable for it to work.

```
sudo chmod 755 /var/www/ziggy-dog.eu/public_html
```

This is also true for you pics directory.

To bad you didn't post this when it was first requested (three days ago)

):P

---

### Post by ThaDoctor99 on 2013-01-18
Thanks a lot, now it works fine.
Gee wonder why I couldn't make it work when I tried making the pics directory 777 ? 
Well never mind it works now :D

---

