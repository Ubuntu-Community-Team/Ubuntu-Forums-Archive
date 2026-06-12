---
title: "lamp web server"
date: 2007-09-14
forum: Server Platforms
---

### Post by dbldown768 on 2007-09-14
I was following this web site ([http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06))  in order to setup a simple web server.  I wanted to try and run a source forge program called statfink that can be using to track fantasy football scores.  I have setup a virtual console using QEMU.  I installed Ubuntu server 6.06 and then I am using the XFCE as my gui.  I then downloaded and installed the Webmin application as the tutorial says.  Since this version of webmin is much newer than the pictures I and kinda on my own.  I created a virtual server to host my web page.  I setup the document root to be /http/statfink.  This is where i have the working php code.  I have chmod to 755 recursively on /http and I have chown to my username in ubuntu.  However, when i try to view my web page locally ([http://localhost](http://localhost)) i keep ketting Forbidden 403 for /.   I have viewed the access.log and error.log files from apache.  I am not at home at the moment so i can't post them.  but i believe it keeps complaining about access to some apache-sites-available directory.  I dont know why it is trying to access this directory when i setup the document root to /http/statfink.   Does anyone have any suggestions?

---

### Post by WorldTripping on 2007-09-14
If I remember rightly it goes something like this.

The configuration file is /etc/apache2/sites-available/default

It should look like this.

[I]DocumentRoot /var/www
<Directory />
Options Indexes FollowSymLinks
AllowOverride None
</Directory>[/I]

Copy this and rename it [www.YourDomain.com](www.YourDomain.com)

The make sure that you have a reference to this in the hosts file.

Sorry can't be more explicit, but I'm at work at the moment.

---

### Post by dbldown768 on 2007-09-14
i dont care at this point about outside connections.  if i can just connect to the web server locally that would be just fine by me since it it running under QEMU.  what do i rename to [www.yourdomain.com?](www.yourdomain.com?) the document root?

---

### Post by WorldTripping on 2007-09-14
Sorry, I thought that you were setting up a virtual directory for your project.
(Hence the apache-sites-available tips)

The Apache homepage ([http://localhost](http://localhost)) is located at /var/www/

What happens when you got [http://localhost/statfink](http://localhost/statfink).

Assuming that there is an index.html file there?

---

### Post by dbldown768 on 2007-09-14
i am setting up a virtual directory, but maybe thats the problem.  the virtual directory root is at /http/statfink, however your saying when i go to my browser and enter in [http://localhost](http://localhost) i am directed to the /var/www/ directory???  I thought the virtual server would redirect this request to my document root?

---

### Post by CyberBob on 2007-09-14
I suggest you check the contents of the following:

File: /etc/apache2/httpd.conf               configuration file for the webserver

should contain stuff like this ...

NameVirtualHost 192.168.1.XXX    this should match your servers IP address

<VirtualHost 192.168.1.XXX>
DocumentRoot /var/www/YourWebsiteFolder
ServerName YourWebsite.com
<Directory "/var/www/YourWebsiteFolder">
allow from all
Options +Indexes
</Directory>
</VirtualHost>


File: /etc/apache2/sites-available/YourWebsite.com.conf

should contain stuff like this ...

<VirtualHost *>
DocumentRoot "/var/www/YourWebsiteFolder"
ServerName YourWebsite.com
<Directory "/var/www/YourWebsiteFolder">
allow from all
Options +Indexes
</Directory>
</VirtualHost>


File: /etc/apache2/sites-enabled/YourWebsite.com.conf

... should be a symbolic link to the file above ( /etc/apache2/sites-available/YourWebsite.com.conf)

just do

```


/etc/apache2/sites-enabled>$ ls -l


```

and if you see the file listed with a pointer -> /etc/apache2/sites-available/YourWebsite.com.conf
then this is OK.  Let us know if you see something different.

Make any necessary changes to make your config files look like this then restart the webserver with the following command:

```


$ /etc/init.d/apache2 restart


```

... and you should be good to go.

Good luck, and let us know what happens ...

---

### Post by dbldown768 on 2007-09-14
thanks.  ill check later when i get home and post back.

---

### Post by WorldTripping on 2007-09-14
hmmm,

You'll have to change the 'Document Root' path in the file apache2.conf file.

e.g. DocumentRoot /http/statfink

---

### Post by dbldown768 on 2007-09-14
this is what my httpd file has in it:
```
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

```

this is the virtual server config under the sites-available

```
<VirtualHost *:80>
DocumentRoot "/http/statfink"
ServerName stat
<Directory "/http/statfink">
allow from all
Options +Indexes
</Directory>
</VirtualHost>
```

the site has a soft link:
lrwxrwxrwx 1 root root 38 2007-09-13 16:37 stat.conf -> /etc/apache2/sites-available/stat.conf

this was in the /var/log/apache directory error.log

```
[Tue Sep 11 15:03:23 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Tue Sep 11 15:04:01 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Tue Sep 11 15:04:56 2007] [notice] caught SIGTERM, shutting down
[Thu Sep 13 13:32:27 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2 configured -- resuming normal operations
[Thu Sep 13 13:42:36 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 13:55:33 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 13:55:39 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 13:56:03 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 13:56:05 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 14:03:21 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 14:03:25 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 14:11:46 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 16:38:17 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 16:48:17 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/
[Thu Sep 13 16:52:16 2007] [error] [client 127.0.0.1] Directory index forbidden by rule: /etc/apache2/sites-available/

```

---

### Post by dbldown768 on 2007-09-14
i got it working! i didnt change anything, but thanks to those who suggested something :)

---

### Post by lajevardi on 2008-05-04
> **dbldown768 said:**
> i got it working! i didnt change anything, but thanks to those who suggested something :)
May I know what you have done to get it to work?

---

