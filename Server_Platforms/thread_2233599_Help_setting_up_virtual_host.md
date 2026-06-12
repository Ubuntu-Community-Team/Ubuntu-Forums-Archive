---
title: "Help setting up virtual host"
date: 2014-07-09
forum: Server Platforms
---

### Post by john264 on 2014-07-09
Hey guys, I'm learning how to setup a virtual host using LAMP. I'm pretty new to Linux, especially using it without the GUI. I'm following [this guide]("http://www.servermom.org/how-to-add-new-site-into-your-apache-based-ubuntu-server/272/") to add a site to apache. I'm pretty sure I did it correctly but when I test it I get this page:
[IMG]http://teamfitdogs.com/wp-content/uploads/2014/07/results.jpg[/IMG]
What I want to happen is I get to this page:
[IMG]http://teamfitdogs.com/wp-content/uploads/2014/07/what-i-want.jpg[/IMG]
Here is my config:
```
        DocumentRoot /var/www/fitdev/htdocs
        DirectoryIndex index.html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory />
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory />
                Options FollowSymLinks MultiViews
                AllowOverride None
```
Any help would be much appreciated.

---

### Post by slickymaster on 2014-07-09
Hi john264, welcome to the forums.

I moved your thread to the **Server Platforms** sub-forum, where you probably will get a more knowledgeable help.

---

### Post by john264 on 2014-07-09
Thanks!

---

### Post by SeijiSensei on 2014-07-09
Does it really look like 
```

        DocumentRoot /var/www/fitdev/htdocs
        DirectoryIndex index.html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory />
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory />
                Options FollowSymLinks MultiViews
                AllowOverride None

```
or just you just hit "paste" too many times?  You only need one specification for Directory / and you are missing the one you need for the DocumentRoot.  Try this:
```

        DocumentRoot /var/www/fitdev/htdocs
        DirectoryIndex index.html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/fitdev/htdocs>
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```
Where is this specified?  Did you replace /etc/apache2/sites-available/000-default with this code?  Did you read [https://help.ubuntu.com/14.04/serverguide/httpd.html](https://help.ubuntu.com/14.04/serverguide/httpd.html)?

---

### Post by dudumomo on 2014-07-09
And don't forget to restart apache afterwards

---

### Post by john264 on 2014-07-09
This is what it actually looks like. Not sure what happen before.
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName fitdev

        DocumentRoot /var/www/fitdev/htdocs
        DirectoryIndex index.html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory />
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
```

---

### Post by SeijiSensei on 2014-07-09
You have two conflicting definitions for "<Directory />", which is the default for all directories that do not match the DocumentRoot.  As I said before, you need to replace the second '<Directory />' entry with '<Directory "/var/www/fitdev/htdocs">' to define the rules for the DocumentRoot.

---

### Post by volkswagner on 2014-07-11
Since you are trying to setup/use "Name Based Virtual Hosts", addressing the server via ipaddress is not 
going to give you the expected results.

From your config file you have:
```
ServerName fitdev
```

This means when addressing [http://fitdev](http://fitdev) you should land at your site (once config file is fixed as per SeijiSensei's post.

To get [http://fitdev](http://fitdev) working, you'll also need DNS config.  The easiest solution would be to add the following to /etc/hosts file
on the client computer (pc with web browser you are using to access the site).

```
192.168.1.10 fitdev
```

---

