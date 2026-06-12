---
title: "Virtual Hosting on External Harddrive"
date: 2008-08-20
forum: Server Platforms
---

### Post by nasp on 2008-08-20
Hi, to begin i want to let you know I just switched to Ubuntu and my knowledge of unix and apache is kinda limited.

The main reason why i want to map an host on my harddrive is because i often have to switch computer or os and I mainly use it for developping and testing. But after following tutorials i keep getting a error 403 message:
Forbidden

Forbidden

You don't have permission to access / on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch Server at dev Port 80


In order to install apache i followed those steps:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_for_local_web_development]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_for_local_web_development")

In order to add a virtual host i followed those steps:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Adding_a_virtual_host_to_your_LAMP_server]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Adding_a_virtual_host_to_your_LAMP_server")

this is my /etc/hosts:
```
127.0.0.1 localhost dev
127.0.1.1 simon-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

this my httpd.conf:

```
<VirtualHost *>
   ServerName dev
   DocumentRoot /media/DATA/dev
   <Directory "/media/DATA/dev/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride None
     Order allow,deny
     allow from all
   </Directory>
</Virtualhost>
```


this is the error logged in /var/log/apache2/error.log:
```
[Wed Aug 20 20:38:00 2008] [crit] [client 127.0.0.1] (13)Permission denied: /media/DATA/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
```

Plus, when I restart apache "/etc/init.d/apache2 restart" i get this error message on shutdown and on restart:
```
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

Thanks a lot for sharing idea on how to resolve my problem :)

Simon

---

### Post by cariboo on 2008-08-21
It would be a ;ot easier if you created a symbolic link from your removeable media to /var/www then trying to set it up in a config file. to do this in /var/www do something like this:

```
ln -s /media/DATA/dev html

```

Then modify the /etc/apache2/sites-available/default to reflect the document root change eg:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/html
```

Jim

---

### Post by windependence on 2008-08-21
The issue is most likely ownership of /media/DATA. It's probably owned by your user and Apache has no access.

-Tim

---

### Post by nasp on 2008-08-21
I still get a 403, how do i give apache access to this folder?

I get this new error after adding a symbolic link:
```
[Thu Aug 21 19:23:31 2008] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www/dev
```

And modifying httpd.conf to
```
<VirtualHost *>
   ServerName dev
   DocumentRoot /var/www/dev/
</Virtualhost>

```

I still have the same error on shutdown and restart of apache:
```
<VirtualHost *>
   ServerName dev
   DocumentRoot /var/www/dev/
</Virtualhost>

```

Whats the difference between allowed sites and the httpd.conf

---

### Post by nasp on 2008-08-21
I tried to ```
sudo chmod -R +rx /media/DATA/dev
``` with no success :(

---

### Post by windependence on 2008-08-22
httpd.conf is the conf file from Apache 1.3. It is only there for compatibilty purposes. You should have nothing in there. Your conf should go in your apache2.conf file, and the /etc/apache2/sites-available files.

The error you are getting on startup can be solved by running the coomand below (with your actual domain and server name) and restarting Apache:

```
echo "ServerName dev.yourdomain.com" | sudo tee /etc/apache2/conf.d/fqdn
```

More info here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

-Tim

---

### Post by nasp on 2008-08-23
Ok, so erased all my httpd.conf and followed the instructions in the link you gave me.

now sites-avaibles/dev looks like:
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName dev
	DocumentRoot /media/DATA/dev
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/DATA/dev>
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

	ErrorLog /var/www/dev/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

</VirtualHost>
```

and then i did
```
sudo a2dissite default && sudo a2ensite dev
```
which worked.

One weird thing is that it created the error.log file at /media/DATA/dev but when i type [http://dev](http://dev) it still get  a 403 and /media/DATA/dev logs 
```
[Sat Aug 23 13:55:51 2008] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
```

If it can write the in log file it has write access, no?
Does it mean apache has no read access?

Edit: The reason why the log file points to /var/www/dev/ is because i have a symbolic link that points to /media/DATA/dev there.

Edit2: Changing DocumentRoot or Directory to /var/www/dev/ result in this error instead
```

[Sat Aug 23 14:05:33 2008] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www/dev

```

---

### Post by windependence on 2008-08-23
It's definitely a permissions issue.

Look at this:

[http://wiki.apache.org/httpd/13PermissionDenied](http://wiki.apache.org/httpd/13PermissionDenied)

-Tim

---

### Post by nasp on 2008-08-23
I did
```
sudo chmod -R 644 /media/DATA/dev
```
And now I can't access it, and all my filea are hidden...

---

### Post by windependence on 2008-08-23
Wel that's probably because of who owns it. You would be perfectly OK to set those files at 755. Actually I am not too sure you want to do this recursively in that directory either. I have a great book on Apache security here. Let me take a look and see what is recommended. I have most of my stuff at 755 but then I have some other things in place also for security.

-Tim

---

### Post by nasp on 2008-08-23
Thanks a lot for your fast support, I really appreciate it :)

---

### Post by windependence on 2008-08-23
No problem. Can you give me the output of 
```

ls -la /media/DATA/dev

ls -la /media/DATA
```

and

```
ls -la /media
```

I want to find out who owns those directories.

-Tim

---

### Post by nasp on 2008-08-24
ls -la /media/DATA/dev
```

total 288
drwx------  5 simon root 32768 2008-08-23 13:52 .
drwx------ 37 simon root 32768 1969-12-31 19:00 ..
-rwx------  1 simon root   704 2008-08-23 14:05 error.log
-rwx------  1 simon root   477 2008-08-23 13:47 error.log~
-rwx------  1 simon root     0 2008-08-23 13:43 index.html
-rwx------  1 simon root    23 2008-08-17 20:37 index.php
-rwx------  1 simon root    23 2008-08-17 20:37 index.php~
drwx------  3 simon root 32768 2008-08-21 19:53 .metadata
drwx------  2 simon root 32768 2008-08-21 20:05 preferences
drwx------  2 simon root 32768 2008-08-23 13:44 PUI
```

ls -la /media/DATA
```
drwx------ 37 simon root    32768 1969-12-31 19:00 .
drwxr-xr-x  6 root  root     4096 2008-08-24 00:04 ..
drwx------  2 simon root    32768 2008-08-11 19:50 alumini
drwx------  2 simon root    32768 2008-06-15 17:42 $AVG8.VAULT$
drwx------  2 simon root    32768 2008-03-22 19:33 _BACKUP
drwx------  8 simon root    32768 2008-08-11 19:47 Compagnie
drwx------  2 simon root    32768 2008-08-11 19:50 corpg
drwx------  5 simon root    32768 2008-04-13 16:08 DataGrid
drwx------  2 simon root    32768 2008-08-11 19:50 depenses_ecole
drwx------  5 simon root    32768 2008-08-23 13:52 dev
-rwx------  1 simon root    15364 2008-03-25 09:48 .DS_Store
drwx------  5 simon root    32768 2007-08-30 13:07 École
drwx------  2 simon root    32768 2008-08-11 19:50 etudeff07
drwx------  2 simon root    32768 2008-08-11 19:50 etudiant2
drwx------  2 simon root    32768 2007-09-07 17:12 Films
drwx------  2 simon root    32768 2008-04-08 20:18 FOUND.000
drwx------  7 simon root    32768 2008-06-21 01:36 framework
-rwx------  1 simon root 18874368 2008-08-02 23:22 ibdata1
-rwx------  1 simon root 10485760 2008-08-02 23:22 ib_logfile0
-rwx------  1 simon root 10485760 2007-01-24 18:36 ib_logfile1
drwx------  7 simon root    32768 2008-03-30 02:55 Icons
drwx------  2 simon root    32768 2008-08-17 19:49 Images
drwx------  2 simon root    32768 2008-08-11 19:50 katya_portfolio
drwx------  7 simon root    32768 2008-05-08 16:58 lib
-rwx------  1 simon root       55 2008-07-25 20:15 loyer.txt
-rwx------  1 simon root     1635 2007-05-09 11:20 MTLDINW2K-100.err
drwx------ 47 simon root    32768 2008-08-19 19:11 Musique
dr-x------ 10 simon root    32768 2008-08-11 19:59 My Pictures
drwx------  2 simon root    32768 2008-08-11 19:50 mysql
-rwx------  1 simon root     1740 2008-05-25 18:36 numtel.txt
drwx------  2 simon root    32768 2008-03-03 10:05 Polices
drwx------  2 simon root    32768 2008-08-11 19:50 portfolio
drwx------  9 simon root    32768 2008-08-23 14:34 Programmes
drwx------  7 simon root    32768 2008-02-13 02:33 Projets
drwx------  6 simon root    32768 2008-03-03 23:14 $RECYCLE.BIN
drwx------  2 simon root    32768 2007-08-30 14:05 Recycled
drwx------ 13 simon root    32768 2007-08-30 13:07 System Volume Information
drwx------  5 simon root    32768 2007-09-19 09:05 .TemporaryItems
-rwx------  1 simon root       82 2007-09-19 09:05 ._.TemporaryItems
-rwx------  1 simon root    19456 2008-05-25 15:23 Thumbs.db
drwx------  4 simon root    32768 2008-08-09 10:19 .Trash-1000
-rwx------  1 simon root     4096 2007-09-04 11:30 ._.Trashes
drwx------  2 simon root    32768 2008-08-11 19:50 vitresimpec
drwx------  2 simon root    32768 2008-08-11 19:50 _vitresimpec
drwx------  5 simon root    32768 2008-03-04 23:58 vitresimpec.com
drwx------  7 simon root    32768 2008-05-16 00:12 vitresimpec_v2
-rwx------  1 simon root   188547 2008-06-30 11:30 wubildr
-rwx------  1 simon root     8192 2008-06-30 11:30 wubildr.mbr
drwx------ 12 simon root    32768 2008-08-11 19:50 www
```

ls -la /media
```
total 56
drwxr-xr-x  6 root  root  4096 2008-08-24 00:04 .
drwxr-xr-x 21 root  root  4096 2008-08-17 09:37 ..
lrwxrwxrwx  1 root   999     6 2008-08-17 13:24 cdrom -> cdrom0
drwxr-xr-x  2 root   999  4096 2008-08-17 13:24 cdrom0
drwxr-xr-x  2 root   999  4096 2008-08-17 13:24 cdrom1
drwx------ 37 simon root 32768 1969-12-31 19:00 DATA
lrwxrwxrwx  1 root   999     7 2008-08-17 13:24 floppy -> floppy0
drwxr-xr-x  2 root   999  4096 2008-08-17 13:24 floppy0
-rw-r--r--  1 root  root   110 2008-08-24 00:04 .hal-mtab
-rw-------  1 root  root     0 2008-08-24 00:04 .hal-mtab-lock
```

---

### Post by windependence on 2008-08-26
OK, according to *"Apache, the Definitive Guide"* from O'Reilly, your document root should be owned by anyone EXCEPT the Apache user. This is so that if someone gains access as the Apache user, they cannot change the files. They suggest it be owned by root and the wheel group. Since wheel doesn't exist in Ubuntu, we'll use admin.

So we should then do this:

```
sudo chown -R root:admin /media/DATA/dev
```

Then, we need to give others (the Apache user) permission to enter (x) and permission to read the files, so we do this:

```
sudo chmod -R o+rx /media/DATA/dev
```

Then, do an ls -la and make sure the permissions and ownership have applied, and then restart Apache. Let me know if you can now reach your site.

-Tim

---

### Post by nasp on 2008-08-26
i get the same error :(
```
[Tue Aug 26 20:10:55 2008] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
```

And my ls are still the exact same thing :(

---

### Post by windependence on 2008-08-26
If your listings are the same, then the permissions did not apply for some reason. 

Your directory should look something like this:

```
drwxr-xr-x  2 root admin  4096 2008-08-26 15:14 test
```

And your files should look like this:

```
-rw-r--r-x 1 root admin     0 2008-08-26 15:11 test
```

Show me your ls -la on /media/DATA/dev

-Tim

---

### Post by nasp on 2008-08-27
ls -la /media/DATA/dev
```

total 288
drwx------  5 simon root 32768 2008-08-23 13:52 .
drwx------ 35 simon root 32768 1969-12-31 19:00 ..
-rwx------  1 simon root  1296 2008-08-26 20:10 error.log
-rwx------  1 simon root   477 2008-08-23 13:47 error.log~
-rwx------  1 simon root     0 2008-08-23 13:43 index.html
-rwx------  1 simon root    23 2008-08-17 20:37 index.php
-rwx------  1 simon root    23 2008-08-17 20:37 index.php~
drwx------  3 simon root 32768 2008-08-21 19:53 .metadata
drwx------  2 simon root 32768 2008-08-21 20:05 preferences
drwx------  2 simon root 32768 2008-08-26 00:55 PUI

```

Argh and it seems like my apache doesn't auto-start anymore :(
sudo /etc/init.d/apache2 restart
```

* Restarting web server apache2
httpd (no pid file) not running

```

---

### Post by windependence on 2008-08-27
Hmmmm.... your permissions definitely did NOT change. Can you try the commands again and let me know if you get any errors?

We didn't change anything that would have to do with the Apache startup script so I am at a loss there. There may be an old pid file laying around that we will need to get rid of.

-Tim

---

### Post by nasp on 2008-08-31
Arhhhgg, I just realised i get
**Permission Denied** on every single file when i do
```
sudo chown -R root:admin /media/DATA/dev

```

But
```

sudo chmod -R o+rx /media/DATA/dev
```
works just fine.

Any idea why I get this error?

---

