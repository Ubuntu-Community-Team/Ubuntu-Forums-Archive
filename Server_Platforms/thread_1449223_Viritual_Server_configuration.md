---
title: "Viritual Server configuration"
date: 2010-04-07
forum: Server Platforms
---

### Post by gomenor on 2010-04-07
Hi guys,

I'm trying to get "Virtual hosting" with 1 domain to work on my Ubuntu Server. My experiance isn't too overwelming, but I belive that I'm closing in on the solution.

I would like MyDomain.se work with the directory: var/www/wordpress.


And this is the guide I've been using: 
[http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)
This is what is in my etc/apache2/sites-enabled/wordpress.conf:
```

<VirtualHost domainname.se>
ServerName domainname.se
ServerAdmin webmaster@localhost
#We want to be able to access the web site using www.dev.example.com or dev.exa$
ServerAlias www.domainname.se
DocumentRoot /var/www/wordpress
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/wordpress-access.log combined
</VirtualHost>

```

This is what's in my etc/hosts:
```

127.0.0.1 localhost.localdomain localhost domainname.se www.domainname.se
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
So when I write "http://domainname.se" In web browser I get this html text written on my page:

"Apache is functioning normallySo my domain is working - but it seems to be accessing the wrong root directory."

So my domain seems to be working - but it looks like it's accessing the wrong root directory.

Can anyone help me look into this,
or help me troubleshoot the problem?

If you need more information I will get it for you!

Thank you for any reply!

---

### Post by KnottyMars on 2010-04-07
This is part of the guide I use to configure virtual hosting. I think there is some config in the apache.conf that needs to be done. Follow these steps, just insert your preferred folder paths and you should be all set, good luck!! 

Create the webspace folders, first browse to your webspace folder
	cd /var/www

Then make a vhosts folder to house your websites
	sudo mkdir vhosts
	cd /var/www/vhosts
Now make the webspace folders for the domains you want with some default sub folders
	sudo mkdir -p [name of domain]/{public,private,log,cgi-bin,backup}

Rinse and repeat for as many domains as needed.  replace [NOD] with the domain name
You can create a simple html index file to verify that the domains are working when they 
are enabled and activated. (OPTIONAL)

Now we need to setup apache2 so that we can serve multiple domains instead of just one
	cd /etc/apache2
	sudo nano sites-available/default

Delete the 'NameVirtualHost *' line and change the next lines text to read:
	<VirtualHost *:80>
		ServerAdmin webmaster@locahost
		DocumentRoot /var/www
Ctrl+O, then press enter to save. Then Ctrl+X to exit the editor

Now we need to adjust the main apache2 conf file
	sudo nano apache2.conf 

At the very bottom of the file, add the following:
	NameVirtualHost *:80

	<IfModule mod_ssl.c>
		NameVirtualHost *:443
	</IfModule>
Ctrl+O, then press enter to save. Then Ctrl+X to exit the editor

Now reload the apache2 conf file
	sudo /etc/init.d/apache2 reload

Add a new user and set ownership and write privileges to the folder path, each user will be specific to each domain path. 
	sudo useradd [your username]
	sudo passwd [your username] (then assign the password)
	sudo chown -R [your username] /var/www/vhosts/[name of domain]
	sudo chmod -R 775 /var/www/vhosts/[name of domain]

You should get no errors or warnings, if you did, make sure that the adjustments to apache2.conf
and the default file in sites-available were saved. 
Now we need to create a vhost file for the domains that were added 
	sudo nano /etc/apache2/sites-available/[name of domain]

This will be a new file so it will be blank, you will need to type all of the following in: 

#Place any notes or comments here
#It will make any custom setup easier to understand later
#
#domain: [name of domain]
#public: /var/www/vhosts/[name of domain]/public

<VirtualHost *:80>
#Admin email, Server Name, (domain name) and any aliases
Server Admin webmaster@[name of domain]
ServerName [name of domain]
ServerAlias [www.[name](www.[name) of domain]

#Index file and document root (where the public files are)
DirectoryIndex index.php index.html
DocumentRoot /var/www/vhosts/[name of domain]/public

#Custom log file locations
LogLevel warn
ErrorLog /var/www/vhosts/[name of domain]/log/error.log
CustomLog /var/www/vhosts/[name of domain]/log/access.log combined

</VirtualHost>

The site needs to be enabled. If you added multiple sites, each one will need to be activated
	sudo a2ensite [name of domain]

Disable the default site
	sudo a2dissite default

Reload the apache2 conf file
	sudo /etc/init.d/apache2 reload

---

### Post by gomenor on 2010-04-08
Thank you for the reply. I've followed the steps. But when I this command:

sudo /etc/init.d/apache2 reload

I get this message:
 [Thu Apr 08 18:51:43 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
[Thu Apr 08 18:51:43 2010] [warn] NameVirtualHost *:80 has no VirtualHosts

And I used this command to activate my wordpress.conf:
sudo a2ensite /etc/apache2/sites-enabled/wordpress.conf
And it looks like this in my folder:

sites-available$ ls
default  default-ssl

/sites-enabled$ ls
wordpress.conf

wordpress.conf looks like this:

<VirtualHost *:80>
ServerName domain.se
ServerAdmin webmaster@localhost
#We want to be able to access the web site using [www.dev.example.com](www.dev.example.com) or dev.exa$
ServerAlias [www.domain.se](www.domain.se)
DirectoryIndex index.php index.html
DocumentRoot /var/www/wordpress
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
ErrorLog /var/www/wordpress/log/error.log
CustomLog /var/www/wordpress/log/access.log combined
</VirtualHost>

Do you need anymore information about my configuration?

Thank you for any reply!

---

### Post by KnottyMars on 2010-04-08
Hi there, 

Did you do this part? 

cd /etc/apache2
sudo nano sites-available/default

Delete the 'NameVirtualHost *' line and change the next lines text to read:
<VirtualHost *:80>
ServerAdmin webmaster@locahost
DocumentRoot /var/www

Ctrl+O, then press enter to save. Then Ctrl+X to exit the editor

Does your /etc/apache2/sites-available/default look something like this? 
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/vhosts
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/vhosts>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```
I think you are using the www folder as your root, so you would need to mod my instructions accordingly. 

The first line of this is what changed from 'NameVirtualHost *' to virtual host. If possible post the first several lines of your default file if you are still having trouble. 

This part is also important. 

sudo nano apache2.conf 

At the very bottom of the file, add the following:
	NameVirtualHost *:80

	<IfModule mod_ssl.c>
		NameVirtualHost *:443
	</IfModule>
Ctrl+O, then press enter to save. Then Ctrl+X to exit the editor

(the SSL mod is optional and only used if you are planning on using it)

Another thing I thought about was that you are setting the doc root to /var/www and there is a default index.html file there, I would recommend adding a folder (I used vhosts) and make that your root for webspaces. 

Hope that helps, good luck.

---

### Post by gomenor on 2010-04-08
This is the start of etc/apache2/sites-available/default:
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

```

This is the end of etc/apache2/apache2.conf:

```

CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

NameVirtualHost *:80

<IfModule mod_ssl.c>
NameVirtualHost *:443
</IfModule>

```

Can u see anything that looks weird?

Thanks for your fast reply btw!

---

### Post by gomenor on 2010-04-08
I was thinking about the last thing you said. So basically u think I should make a new folder, so that my wordpress directory should be in: var/www/vhost/wordpress instead - Correct?

---

### Post by KnottyMars on 2010-04-08
everything looks right from what I can tell, did you change anything to that or was that how it was set when you were getting the error. 

No problem on the fast reply, I was just checking in on another post I made yesterday :) 

It might be worth just adding that additional folder to see if that would do it. Do you have your whole site already in place? 

Another thing to try would be to delete the default index.html file that apache2 puts in the /var/www folder. 

Also check the file contents of the /etc/apache2/sites-enabled/[whatever your file name is]

Make sure the DocumentRoot is set to the location of your webpages. Let me know if you are still having trouble. Maybe try restarting the box to make sure apache is using all of the new settings you put in. (and just to make sure, you disabled the default site right?) 

Hope some of this helps.

---

### Post by KnottyMars on 2010-04-08
> **gomenor said:**
> I was thinking about the last thing you said. So basically u think I should make a new folder, so that my wordpress directory should be in: var/www/vhost/wordpress instead - Correct?

I have done that out of practice, but Im not sure its 100% needed. It allows me to make sure that there is no way that anything in the /var/www folder gets seen as a website. This gives you folders for each site. My directory is /var/www/vhosts then in that vhosts folder, I have about 6 folders in the vhosts folder. Each of those folders have my domain names in them and each of THOSE have the directories are {public, private, cgi-bin, backup} 

That gives me a DocumentRoot of /var/www/vhosts/domain1/public

This way Im sure that there is a clear line in how the domains are split up. 

Again, this may just be my OCD kicking in lol, but the DocumentRoot should tell apache where to find the index file.

---

### Post by gomenor on 2010-04-11
Thank you guys for the help - the viritual server is now working.

I made this things to make it work:

1. deleted the including code for phpadmin in apache2.conf
2. created a vhost directory so it got easier to understand how it's working
3. made sure that wordpress.conf was enabled.

---

### Post by gomenor on 2010-04-11
Thank you guys for the help - the viritual server is now working.

I made this things to make it work:

1. deleted the including code for phpadmin in apache2.conf
2. created a vhost directory so it got easier to understand how it's working
3. made sure that wordpress.conf was enabled.

---

### Post by Vegan on 2010-04-11
I have posted in the Linux IT section of my site, some ideas for vhosts, see the forum.

---

