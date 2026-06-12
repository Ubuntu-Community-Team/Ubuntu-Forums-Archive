---
title: "Problem installing apache webserver: “You don't have permission to access this resour"
date: 2019-11-20
forum: Server Platforms
---

### Post by jorisvh2 on 2019-11-20
When I go in my browser to [http://localhost](http://localhost), I get this: 

[h=1]Forbidden[/h] You don't have permission to access this resource.
 [HR][/HR] Apache/2.4.29 (Ubuntu) Server at localhost Port 80


I installed a new version of Ubuntu on my computer. Ubuntu 18.04.3 LTS

 
 
 The files for my website are on another disk. See program tools &#8594; disks  
 Device: *dev*/sdb1
 Partition type: Linux Contence: Ext4(versie 1.0) – Mounted on /*media*/joris/doc
 
 
 I did following:

 source: [https://tutorials.ubuntu.com/tutorial/install-and-configure-apache#1](https://tutorials.ubuntu.com/tutorial/install-and-configure-apache#1)
 
 
 
 
 sudo apt update
 sudo apt install apache2
 cd /etc/apache2/sites-available/
 sudo cp 000-default.conf gci.conf
 
 
 sudo gedit gci.conf
 DocumentRoot *media*/joris/doc/website
 
 
 sudo a2ensite gci.conf
 service apache2 reload
  sudo adduser joris  www-data
 sudo chown -R www-data:www-data /media/joris/doc/website
 sudo chmod -R g+rw /media/joris/doc/website
 
 
 
 
  P.S. I live in Belgium and I speak Dutch. Exist also a dutch forum
  of ubuntu?

---

### Post by uRock on 2019-11-20
Moved to **Server Platforms** sub-forum.

---

### Post by Doug S on 2019-11-20
Hi,

I just pointed you to an answer over on your [askubuntu question]("https://askubuntu.com/questions/1190340/problem-installing-apache-webserver-you-dont-have-permission-to-access-this-r").
Now, I'll point you to an answer here: [https://ubuntuforums.org/showthread.php?t=2425950&p=13884703#post13884703]("https://ubuntuforums.org/showthread.php?t=2425950&p=13884703#post13884703")

But also copy it below:

If you want to use a non-stanadard directory, and in addition to all the permissions stuff, you have to tell apache to allow it via the /etc/apache2/apache2.conf file.
Just copy the /var/www/html stantza stuff to whatever, example:

```
<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

<Directory /media/newhd/test_web/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>
```

---

### Post by jorisvh2 on 2019-11-20
My contence of *etc*/apache2/sites-available/gci.conf


```

<VirtualHost *:80>
     # The ServerName directive sets the request scheme, hostname and port that
     # the server uses to identify itself. This is used when creating
     # redirection URLs. In the context of virtual hosts, the ServerName
     # specifies what hostname must appear in the request's Host: header to
     # match this virtual host. For the default virtual host (this file) this
     # value is not decisive as it is used as a last resort host regardless.
     # However, you must set it for any further virtual host explicitly.
     #ServerName [www.example.com](www.example.com)
 
 
     ServerAdmin webmaster@localhost
     # DocumentRoot /var/www/html
     DocumentRoot /media/joris/doc/website
     # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
     # error, crit, alert, emerg.
     # It is also possible to configure the loglevel for particular
     # modules, e.g.
     #LogLevel info ssl:warn
 
 
     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
 
 
     # For most configuration files from conf-available/, which are
     # enabled or disabled at a global level, it is possible to
     # include a line for only one particular virtual host. For example the
     # following line enables the CGI configuration for this host only
     # after it has been globally disabled with "a2disconf".
     #Include conf-available/serve-cgi-bin.conf
 </VirtualHost>


```

 
 
  
 
 
 
 Contence of:
 *etc*/apache2/apache2.conf
 first try: (I forgot to mention it in my first mail)
 
 ```

 <Directory />
     Options FollowSymLinks
     AllowOverride None
     Require all denied
 </Directory>
 
 
 <Directory /usr/share>
     AllowOverride None
     Require all granted
 </Directory>
 
 
 #<Directory /var/www/>
 <Directory /media/joris/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
 </Directory>

```

 
 
 
 
 Second try:
```

 <Directory />
     Options FollowSymLinks
     AllowOverride None
     Require all denied
 </Directory>
 
 
 <Directory /usr/share>
     AllowOverride None
     Require all granted
 </Directory>
 
 
 <Directory /var/www/>
 Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
 </Directory>
 
 
 <Directory /media/joris/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
 </Directory>
 
 

```
 
 
 Now I have the problem that my site is not shown! I get this:  
 The default site of Apache! 
 
  Apache2 Ubuntu Default Page  
     
 
 It works!

---

### Post by SeijiSensei on 2019-11-20
If you want to point the server to non-standard directories, the easiest method to use an Alias directive.  E.g.,

```

<VirtualHost *:80>
[stuff]

Alias /joris /media/joris/website
 
<Directory /media/joris/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
</Directory>

[stuff]
</VirtualHost>

```

Now, after restarting the server, the URL [http://localhost/joris](http://localhost/joris) will use the /media/joris/website directory.

---

### Post by jorisvh2 on 2019-11-20
My contence of *etc*/apache2/sites-available/gci.conf


```

<VirtualHost *:80>
     # The ServerName directive sets the request scheme, hostname and port that
     # the server uses to identify itself. This is used when creating
     # redirection URLs. In the context of virtual hosts, the ServerName
     # specifies what hostname must appear in the request's Host: header to
     # match this virtual host. For the default virtual host (this file) this
     # value is not decisive as it is used as a last resort host regardless.
     # However, you must set it for any further virtual host explicitly.
     #ServerName [www.example.com](www.example.com)
 
 
     ServerAdmin webmaster@localhost
     # DocumentRoot /var/www/html
     DocumentRoot /media/joris/doc/website
     # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
     # error, crit, alert, emerg.
     # It is also possible to configure the loglevel for particular
     # modules, e.g.
     #LogLevel info ssl:warn
 
 
     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined
 
 
     # For most configuration files from conf-available/, which are
     # enabled or disabled at a global level, it is possible to
     # include a line for only one particular virtual host. For example the
     # following line enables the CGI configuration for this host only
     # after it has been globally disabled with "a2disconf".
     #Include conf-available/serve-cgi-bin.conf
 </VirtualHost>


```

 
 
  
 
 
 
 Contence of:
 *etc*/apache2/apache2.conf
 first try: (I forgot to mention it in my first mail)
 
 ```

 <Directory />
     Options FollowSymLinks
     AllowOverride None
     Require all denied
 </Directory>
 
 
 <Directory /usr/share>
     AllowOverride None
     Require all granted
 </Directory>
 
 
 #<Directory /var/www/>
 <Directory /media/doc/joris/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
 </Directory>

```

 
 
 
 
 Second try:
```

 <Directory />
     Options FollowSymLinks
     AllowOverride None
     Require all denied
 </Directory>
 
 
 <Directory /usr/share>
     AllowOverride None
     Require all granted
 </Directory>
 
 
 <Directory /var/www/>
 Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
 </Directory>
 
 
 <Directory /media/doc/joris/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
 </Directory>
 
 

```
 
 
 Now I have the problem that my site is not shown! I get this:  
 The default site of Apache! 
 
  Apache2 Ubuntu Default Page  
     
 
 It works!

---

### Post by TheFu on 2019-11-20
```
DocumentRoot media/joris/doc/website
```
uses a relative path.  It must be an absolute path.  Also, that directory needs to be open enough for the apache userid, www-data, to read.

If the storage isn't using a Linux file system, then only storage mount options can control the needed permissions.

---

### Post by SeijiSensei on 2019-11-20
On Ubuntu/Debian you never need to edit the apache2.conf file. All your configurations should be in the .conf files in /etc/apache2/sites-available.  Have you read this: [https://help.ubuntu.com/lts/serverguide/httpd.html?](https://help.ubuntu.com/lts/serverguide/httpd.html?) Any Alias directives and associated <Directory> stanzas need to be inside a <VirtualHost> container in a file like gci.conf.

---

### Post by jorisvh2 on 2019-11-20
> **SeijiSensei said:**
> If you want to point the server to non-standard directories, the easiest method to use an Alias directive.  E.g.,

```

<VirtualHost *:80>
[stuff]

Alias /joris /media/joris/website
 
<Directory /media/joris/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
</Directory>

[stuff]
</VirtualHost>

```

Now, after restarting the server, the URL [http://localhost/joris](http://localhost/joris) will use the /media/joris/website directory.

I did this in /etc/apache2/sites-available/gci.conf
```


Alias /joris /media/joris/doc/website
 
<Directory /media/joris/doc/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
</Directory>

```


But it doesn't work! 

[http://localhost/joris](http://localhost/joris) give:

**Not Found**

 The requested URL was not found on this server.

 [HR][/HR] Apache/2.4.29 (Ubuntu) Server at localhost Port 80

---

### Post by Doug S on 2019-11-20
> **SeijiSensei said:**
> On Ubuntu/Debian you never need to edit the apache2.conf file. That hasn't been my experience for non-standard directories, but I have always respected your posts herein. I don't have time right now, but I'll try it again on my test server when I do.

---

### Post by SeijiSensei on 2019-11-20
> **jorisvh2 said:**
> I did this in /etc/apache2/sites-available/gci.conf

[http://localhost/joris](http://localhost/joris) give:

**Not Found**

The requested URL was not found on this server.

Apache/2.4.29 (Ubuntu) Server at localhost Port 80

First, try using 
```
Alias /joris/ /media/joris/website/
```
Sometimes having both leading and trailing slashes works better.

I'd also examine the log in /var/log/apache2 to see if they provide more detailed information.

Did you restart Apache? Did you run "sudo a2ensite gci" to "activate" the site? Check in /etc/apache2/sites-enabled and make sure there is a symbolic link to /etc/apache2/sites-available/gci.conf.

Earlier you suggested you had copied 000-default.conf to gci.conf.  I'd delete or otherwise disable 000-default.conf.  Apache parses these files in alphanumeric order which is why 000-default has the name it does.

If none of that helps, I'd suggest moving the /etc/apache2 directory to /etc/apache2.old, then reinstalling apache2. Rename 000-default.conf to gci.conf if you like, but have just one instance of this configuration.  Add the Alias directive and <Directory> stanza to that file and leave apache2.conf alone. Run a2ensite and restart apache2.  Any better?

Here, for example, is part of the configuration file for one of the virtual hosts on a server I manage:

```

<VirtualHost *:80>
    
ServerName      www.example.com
ServerAlias     example.com
ServerAdmin     admin@example.com
DocumentRoot    /var/www/html/wordpress
ErrorLog        logs/error_log-example.com
TransferLog     logs/access_log-example.com
CustomLog       logs/referer_log-example.com "%h: %{referer}i -> %U"

Alias /gallery/ /home/web/gallery/
<Directory "/home/web/gallery">
    Options All
</Directory>

<Directory /var/www/html/wordpress>
[etc.]
</Directory>

</VirtualHost>

```

The site runs WordPress from /var/www/html/wordpress, but serves up files from /home/web/gallery/ when using the URI /gallery/.

---

### Post by jorisvh2 on 2019-11-21
I have taken new steps
I encountered problems with rights in other programs
 
 
 
 
 mkdir /d
 sudo cp *etc*/fstab etc/fstab_oud
 
 
 sudo gedit *etc*/fstab
 # Harde schijf 1TB
 UUID="23f455e3-08a4-4e34-9122-19e375ed6a4c" /d ext4 defaults 0 0
 
 
 Folder website: /*d*/website
 
 
 cd *etc*/apache2/sites-available
 
 
 sudo gedit gci.conf
 # DocumentRoot /var/www/html
 DocumentRoot /d/website
 
 
 sudo gedit *etc*/apache2/apache2.conf
 <Directory /d/website/>
     Options Indexes FollowSymLinks
     AllowOverride None
     Require all granted
 </Directory>
 
 
 With the program dolphin i added a named user www-data

 
 I have added named user www-data and 
[v] Apply changes to all subfolders and their content

 
 
 
 
 
 
 
 
 service apache2 reload
 
 
 My site is still not displayed, but the default site of apache!

---

### Post by LHammonds on 2019-11-21
Well, I see one glaring problem right off the bat (besides putting your site config edits in apache2.conf), when you created a folder, you failed to set the ownership and permissions.

Whenever you do something like this:
```
sudo mkdir -p /d
```
You need to follow it up with something like this:
```
sudo chown www-data:www-data /d
sudo chmod 0755 /d
```

Once you start placing files in there, you need to make sure ownership and permissions are being set correctly.  It would behoove you to create a permission settings script and ensure it runs on a regular basis.

Example (taken from my [web tutorial](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261#p711)):
setperms.sh
```

#!/bin/bash
#############################################
## Name          : setperms.sh
## Version       : 1.1
## Date          : 2019-09-03
## Author        : LHammonds
## Compatibility : Ubuntu Server 18.04 LTS
## Requirements  : Run as root user
## Purpose       : Ensures ownership and permissions are set correctly.
## Run Frequency : Manual as needed or via crontab schedule.
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2019-07-23 LTH Created script.
## 2019-09-03 LTH Added full path to executables.
#############################################
wwwdir='/d'
webuser='www-data'
webgrp='www-data'
rootuser='root'

echo "Setting Ownership..."
/bin/chown -R ${webuser}:${webgrp} ${wwwdir}/
/bin/echo "Setting Folder Permissions..."
/usr/bin/find ${wwwdir}/ -type d -print0 | /usr/bin/xargs -0 /bin/chmod 0750
/bin/echo "Setting File Permissions..."
/usr/bin/find ${wwwdir}/ -type f -print0 | /usr/bin/xargs -0 /bin/chmod 0640
if [ -f ${wwwdir}/.htaccess ]; then
  /bin/chmod 0644 ${wwwdir}/.htaccess
fi
/bin/echo "Permission change complete."

```

LHammonds

---

### Post by jorisvh2 on 2019-11-21
I did this: 
sudo chown -R www-data:www-data /d/website
sudo chmod -R 0755 /d/website

My site is still not displayed!! I get this: See: [http://pasteall.org/pic/show.php?id=f51de8164fbf6a9d411b89145c01d5af](http://pasteall.org/pic/show.php?id=f51de8164fbf6a9d411b89145c01d5af)

---

### Post by SeijiSensei on 2019-11-21
As I said, if you have both 000-default.conf and gci.conf in the /sites-enabled/ directory, Apache will use the first of these. If you want it use gci.conf, use a2dissite or delete the symbolic link in /sites-enabled/.

---

### Post by jorisvh2 on 2019-11-21
> **SeijiSensei said:**
> As I said, if you have both 000-default.conf and gci.conf in the /sites-enabled/ directory, Apache will use the first of these. If you want it use gci.conf, use a2dissite or delete the symbolic link in /sites-enabled/.

Indeed SeijiSensei!!

i did this: 
joris@joris-MS-7798:/etc/apache2/sites-available$ sudo  a2dissite 000-default
[sudo] wachtwoord voor joris: 
Site 000-default disabled.
To activate the new configuration, you need to run:
  systemctl reload apache2
joris@joris-MS-7798:/etc/apache2/sites-available$ sudo a2ensite gci.conf
Site gci already enabled
joris@joris-MS-7798:/etc/apache2/sites-available$ sudo service apache2 reload

and it worked!!! Thank you very much!!!

---

### Post by Doug S on 2019-11-24
In earlier posts, I mentioned that access to non-standard directories also needed to specifically allow access via /etc/apache2/apache2.conf. That seems to be the case for my Ubuntu 16.04 test server. Without it I get:

```
[Sun Nov 24 15:42:28.330709 2019] [authz_core:debug] [pid 28871] mod_authz_core.c(809): [client 192.168.111.101:62206] AH01626: authorization result of Require all denied: denied
[Sun Nov 24 15:42:28.330741 2019] [authz_core:debug] [pid 28871] mod_authz_core.c(809): [client 192.168.111.101:62206] AH01626: authorization result of <RequireAny>: denied
[Sun Nov 24 15:42:28.330748 2019] [authz_core:error] [pid 28871] [client 192.168.111.101:62206] AH01630: client denied by server configuration: /media/vm/test_web/

```

And with it I get:

```
[Sun Nov 24 15:51:53.260036 2019] [authz_core:debug] [pid 13148] mod_authz_core.c(809): [client 192.168.111.101:62259] AH01626: authorization result of Require all granted: granted
[Sun Nov 24 15:51:53.260056 2019] [authz_core:debug] [pid 13148] mod_authz_core.c(809): [client 192.168.111.101:62259] AH01626: authorization result of <RequireAny>: granted

```

---

