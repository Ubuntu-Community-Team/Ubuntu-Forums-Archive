---
title: "Apache2 subdomains"
date: 2011-07-25
forum: Server Platforms
---

### Post by brent1975 on 2011-07-25
Hello, I am trying to get sub-domains to work. I am running apache2 on ubuntu 11.4 

my domain works great no issues at all. we will call it domain.com however what I am trying to do is  forums.domain.com.  I have done some searching and appears many different ways of doing this none which seem to work. I have webmin installed but either I dont know what I am am doing in the apache virtual hosts or it is not working proper. I would prefer to do this from the command line if all possible.   here is an example of what my site structure looks like

/var/www               domain.com
/var/www/forums    forums.domain.com

Thank you for the help

---

### Post by koenn on 2011-07-25
how do you lnow it's not working ?

---

### Post by volkswagner on 2011-07-25
> **brent1975 said:**
>  what my site structure looks like

/var/www               domain.com
/var/www/forums    forums.domain.com

Thank you for the help

Not that this is an issue, but putting spaces in filenames and directory names is a bad habit to get into when using Linux.

As koenn asked, how do you know it is not working?  What happens when you try the subdomain in a browser?  Did you setup an A record for DNS?  What do you get when you run

```
dig forums.domain.com
```

If you want command line options for setting up VirtualHosts check the sticky at the top of this forum.

Ubuntu Documentation > Ubuntu 10.04 > Ubuntu Server Guide > Web Servers > HTTPD - [Apache2 Web Server]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html")

Did you add NameVirtualHost to httpd.conf or ports.conf?

---

### Post by brent1975 on 2011-07-26
> **brent1975 said:**
> Hello, I am trying to get sub-domains to work. I am running apache2 on ubuntu 11.4 

my domain works great no issues at all. we will call it domain.com however what I am trying to do is  forums.domain.com.  I have done some searching and appears many different ways of doing this none which seem to work. I have webmin installed but either I dont know what I am am doing in the apache virtual hosts or it is not working proper. I would prefer to do this from the command line if all possible.   here is an example of what my site structure looks like

/var/www               domain.com
/var/www/forums    forums.domain.com

Thank you for the help

Sorry for the miss understanding on the structure
/var/www   = domain.com (main domain)
/var/www/forums  = forums.domain.com (sub domain)
When I go to either domain.com or forums.domain.com I end up at domain.com

---

### Post by volkswagner on 2011-07-26
What about the other questions?

What is the output of:

```
ls /etc/apache2/sites-enabled
```

```
cat /etc/apache2/ports.conf
```

```
cat /etc/apache2/httpd.conf
```

Sounds like DNS is working, so it's most likely Apache is not honoring your NameVirtualHost directive.  We need to verify the directive is present, and your virtual host files are containing correct syntax.

---

### Post by brent1975 on 2011-07-26
> **volkswagner said:**
> What about the other questions?

What is the output of:

```
ls /etc/apache2/sites-enabled
``````
cat /etc/apache2/ports.conf
``````
cat /etc/apache2/httpd.conf
```Sounds like DNS is working, so it's most likely Apache is not honoring your NameVirtualHost directive.  We need to verify the directive is present, and your virtual host files are containing correct syntax.
Here is my output: 
 ls /etc/apache2/sites-enabled
000-default  webmin.1311658344.conf

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
cat /etc/apache2/httpd.conf   no output

---

### Post by koenn on 2011-07-26
according to your output, you only have 1 site, the default site. 
That's why both of your 'sites' show the same content

You need to configure the 2nd site (forums.domain.com) as a so-called "VirtualHost"

read [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html) -> Basic settings -> the stuff about adding a site as a virtualhost

google with keywords ubuntu apache virtualhost will give you additional info

give it a try, come back with questions if need be

---

### Post by volkswagner on 2011-07-27
Actually it appears there are two Vhost files.  The default and one created with webmin.

Let's check the content.

What is the output of

```
cat /etc/apache2/sites-enabled/webmin.1311658344.conf
```

---

### Post by koenn on 2011-07-27
> **volkswagner said:**
> Actually it appears there are two Vhost files.  The default and one created with webmin.

Let's check the content.

What is the output of

```
cat /etc/apache2/sites-enabled/webmin.1311658344.conf
```

oops, you're right, missed that.

---

### Post by brent1975 on 2011-07-27
> **koenn said:**
> oops, you're right, missed that.

Sorry guys, Where I work wont allow me to use SSH. Also I reloaded last night and went back to 10.10. So right now I am sitting with a clean server. apache2 included.  When I get home I will update as to what I have going on.

---

### Post by volkswagner on 2011-07-27
> **brent1975 said:**
> Sorry guys, Where I work wont allow me to use SSH. Also I reloaded last night and went back to 10.10. So right now I am sitting with a clean server. apache2 included.  When I get home I will update as to what I have going on.

Unless there was something offered in 10.10 that is not available in 10.04, I would have opted for the long term support offered with 10.04, vs end of life in April 2012 for version 10.10.

Food for thought.

Before you spend hours configuring this install, perhaps you may want to consider your long term goals, and if you want to do a reinstall, or take your chances with an upgrade in your future.

---

### Post by brent1975 on 2011-07-28
> **volkswagner said:**
> Unless there was something offered in 10.10 that is not available in 10.04, I would have opted for the long term support offered with 10.04, vs end of life in April 2012 for version 10.10.

Food for thought.

Before you spend hours configuring this install, perhaps you may want to consider your long term goals, and if you want to do a reinstall, or take your chances with an upgrade in your future.

Yeah, I tried 11.4 it did not play well at all. However I did like the logon information that I got off of 11.4 Once logged in showed both IP's and last logon info etc...  Pretty nice

You are right, I will grab 10.04 tonight when I get home.   So here is what I am trying to do. I have a domain named iso-world.com  I have this registered at 1and1.com I also created a sub-domain at 1and1.com called forums.iso-world.com  both which are pointed to my server. I have a static IP so I dont have to worry about releasing etc... 

for my hosting  under /var/www I have a folder called Forums.  I want to be able to when I put forums.iso-world.com it goes to that dir>  I also want when I type [www.iso-world.com](www.iso-world.com) it goes to the main website dir> /var/www    When I try them both right now I get the apache2 default page it works. I use an offsite DNS service instead of my own. Which is something that I am going to get into down the road. But for right now one thing at a time  I am going to try and go at this with out using webmin. I guess what I am looking for is one of those nice how-to's step by step to achieve what I am looking for.

---

### Post by volkswagner on 2011-07-28
> **brent1975 said:**
> ... However I did like the logon information that I got off of 11.4 Once logged in...

You will also get this when using 10.04.  Be sure to download the latest .iso 10.04.3 so you will have less updates to download/install.
 

> **brent1975 said:**
> 
for my hosting  under /var/www I have a folder called Forums.  I want to be able to when I put forums.iso-world.com it goes to that dir>  I also want when I type [www.iso-world.com](www.iso-world.com) it goes to the main website dir> /var/www    

You can create a CNAME record at your DNS provider for www and point it to iso-world.com, then setup the "ServerAlias" directive in your virtual host file.

> **brent1975 said:**
>  ...I am going to try and go at this with out using webmin. I guess what I am looking for is one of those nice how-to's step by step to achieve what I am looking for.

I recommend staying away from Webmin if you can help it.  I admit I started using Webmin when first leaning Ubuntu Server and Apache.  I believe for the Apache Vhost handling it caused a couple problems when combined with hand edited host files.  I found editing the config files directly helped me learn at a faster pace.  These forums are a wonderful support venue, which can help with most any hand holding you may need.

[The Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") is stickied at the top of this forum, and should be your first documents to turn to for help.  Included in that guide you'll find the [Apache2 help files]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html"), which spell out the setup of Virtual hosts using individual host files in /etc/apache2/sites-available.

One important thing to remember is ALWAYS create a backup prior to editing ANY config file.

example:
```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/default.bak
```

It is best to start simple.  Create your various virtual hosts and directories.  Copy the default/index.html to each directory and edit it so it is unique to each virtual host.  Once you have a few virtual hosts working as expected using static html files, then go ahead and add your more complex content or web apps, etc.

```
sudo mkdir /var/www/forum
sudo cp /var/www/index.html /var/www/forum/
```

```
sudo cp /var/www/forum/index.html /var/www/forum/index.html.bak
```

Make your forums index.html file unique by editing.

```
sudo nano /var/www/forum/index.html
```

Make it look like this or similar.

```
<html><body><h1>It works!</h1>
<p>This page is a place holder for the soon to be Forum located as<br>forum.iso-wold.com.</p>
</body></html>

```

Copy your default vhost file as mentioned in the above linked how to.

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/forum

```

Now edit the vhost file to reflect the forums file location and ServerName.

```
sudo nano /etc/apache2/sites-available/forum
```

```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName forum.iso-world.com
	DocumentRoot /var/www/forum
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/forum/>
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


Notice the first line

```
<VirtualHost *>
```

This will need to match for the NameVirtualHost directive in ports.conf.

Check to see if the directive is there.  You can add the following line to /etc/apache2/ports.conf if it is not there already.

```
NameVirtualHost *
```

If the directive in ports.conf specifies a port you will need to change it, or all your vhost files will need to specify the port.

ie:
```
NameVirtualHost *:80
```

Then all vhost files shall lead off with

```
<VirtualHost *:80>
```
Which may be the default setup.

The '*' is a wild card meaning Apache2 will use this file for any requested servername not specified elsewhere(any other vhost files).

You'll need to do the same thing for your main domain, either using the default file or create a new one.  For this file, you'll want to add the "ServerAlias www.iso-world.com" after the "ServerName" line.

Then enable the sites as specified in the how to using a2ensite and reload apache.

Don't forget to have fun!

---

