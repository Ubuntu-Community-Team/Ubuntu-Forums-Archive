---
title: "LAMP - 403 Forbidden error"
date: 2010-07-17
forum: Server Platforms
---

### Post by Kdar on 2010-07-17
Here what I get when I try to access my site:
> Forbidden

You don't have permission to access / on this server.
Apache/2.2.14 (Ubuntu) Server at drupal6 Port 80

After configuring LAMP, I used this tutorial to place web-site inside of my home directory:
[http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/](http://tuxtweaks.com/2009/07/how-to-configure-apache-linux/)

```
cd
mkdir drupal6
cd /etc/apache2/sites-available
sudo cp default drupal6
sudo nano drupal6

```
Changed drupal6:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
        ServerName drupal6

	DocumentRoot /home/myID/webdev/drupal6/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/myID/webdev/drupal6/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
.........................
</VirtualHost>
```
Enabled new site:
```
sudo a2ensite drupal6
sudo nano /etc/hosts

```

```
127.0.0.1 localhost drupal6
```

```
sudo /etc/init.d/apache2 reload
```

----
On my laptop, I used same configuration and it all worked.
Only difference between my Desktop and Laptop were the permissions on home and myID directory. I applied the same permissions to home and myID on my laptop (same like on Laptop), but it didn't fix the problem.

Please, someone, help me. I want to be able work on sites from my desktop.
PS: My laptop and desktop both use Ubuntu 10.04

---

### Post by Kdar on 2010-07-17
I found my problem (I think).
It was the same, the permission.. I just forgot to check the permission of "drupal6" directory.

Had to change from "drwx------" to "drwxr-xr-x"

Also, I checked inside of "drupal6" directory and all directories inside of it are also "drwx------"......

How do I make so that any newly created directories are "drwxr-xr-x" and not "drwx------".
It would be a pain to change it every time manually.

---

### Post by Ryan Dwyer on 2010-07-17
The permissions you've provided don't mean much unless you tell us who the user and group are, as well as if www-data is a member of the group.

I believe if the directory has write permission, newly created files and directories will also have write permissions.

You can chmod recursively using chmod -R.

Ideally you should add www-data to your own group. Eg. if your username and group are kdar/kdar, add www-data to the kdar group. Then check that the owner/group of the files is kdar/kdar. Then change the permissions so group has write access and other doesn't.

---

