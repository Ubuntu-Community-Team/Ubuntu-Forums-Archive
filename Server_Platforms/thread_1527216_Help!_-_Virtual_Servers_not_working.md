---
title: "Help! - Virtual Servers not working"
date: 2010-07-09
forum: Server Platforms
---

### Post by TekMuzik on 2010-07-09
Hello. I'm trying to set up virtual servers for my two websites. I'm making the change from a very generic server which served whatever was at /var/www. Now I have two directories set up, /var/www/PK and /var/www/FSF and I'm trying to set up virtual hosts to serve those two directorys to their respective web addresses, pinkkittens.org and freespeech-forum.com. Neither site is currently working.
I have two files in /etc/apache2/sites-avaiable

pinkkittens
```
<virtualhost pinkkittens.org>
ServerAdmin [email]TekMuzik@gmail.com[/email]
ServerName pinkkittens.org
ServerAlias [www.pinkkittens.org](www.pinkkittens.org)

DocumentRoot /var/www/PK/
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

<Directory /var/www/PK/>
Options -Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

<FilesMatch "access_log|error_log">
    Order allow,deny
    Deny from all
</FilesMatch>



ErrorLog /var/log/apache2/error.log
LogLevel debug
CustomLog /var/log/apache2/access.log combineddefault


</VirtualHost>


```
and
freespeech-forum
```
<virtualhost freespeech-forum.com>
ServerAdmin [email]TekMuzik@gmail.com[/email]
ServerName FreeSpeech-Forum.com
ServerAlias [www.freespeech-forum.com](www.freespeech-forum.com)

DocumentRoot /var/www/FSF/
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

<Directory /var/www/FSF/>
Options -Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
</Directory>

<FilesMatch "access_log|error_log">
    Order allow,deny
    Deny from all
</FilesMatch>



ErrorLog /var/log/apache2/error.log
LogLevel debug
CustomLog /var/log/apache2/access.log combineddefault


</VirtualHost>

```

Both of which were enable using a2ensite and apache was restarted as well as server rebooted. No errors were displayed during enabling, or during apache restart.

Any help please?

EDIT: It might be worth noting I can connect over SSH using putty using freespeech-forum.com or pinkkittens.org as address

EDIT2: My /var/log/apache2/error.log has 
```

[Fri Jul 09 01:09:36 2010] [error] [client ip.address.51.110] File does not exist: /htdocs

```
listed several times. Of course...without the "ip.address" part.

---

### Post by TekMuzik on 2010-07-09
Anyone?

---

### Post by volkswagner on 2010-07-10
I have never seen the syntax for your servername as virtualhost.

Try changing 

<virtualhost pinkkittens.org>


to

<VirtualHost *>

The restart apache2.  The error indicates apache2 is looking for /htdocs

What type of site are you trying to run?  Perhaps there is some .php code or otherwise looking for that folder /htdocs.

---

### Post by volkswagner on 2010-07-14
Just marking a thread solved is not most effective.  To help others in the future, feel free to mention what actions solved your issue.

---

