---
title: "Apache2 gives timout"
date: 2008-03-18
forum: Server Platforms
---

### Post by Stom on 2008-03-18
I've installed apache2 but can't get a page to display when trying to connect to either:

- [http://localhost](http://localhost)
- [http://127.0.0.1](http://127.0.0.1)
- [http://127.0.1.1](http://127.0.1.1)
- [http://192.168.0.9](http://192.168.0.9)

Firefox gives a timeout error instead.

I've tried adding adding [FONT="Courier New"]ServerName localhost[/FONT] to* /etc/apache2/httpd.conf*.

I've run [FONT="Courier New"]sudo netstat -plant[/FONT],it gives the following:

```
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     5148/mysqld         
tcp        0      0 127.0.1.1:80            0.0.0.0:*               LISTEN     5719/apache2        
tcp        0      0 127.0.0.1:80            0.0.0.0:*               LISTEN     5719/apache2        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5048/cupsd          
tcp        1      0 192.168.0.9:33050       72.14.253.83:80         CLOSE_WAIT 6350/npviewer.bin   
tcp        0      0 192.168.0.9:57645       66.249.93.19:80         ESTABLISHED6290/firefox-bin    
tcp        0      0 192.168.0.9:40285       64.4.36.56:1863         TIME_WAIT  -                   
tcp        1      0 192.168.0.9:47315       74.208.9.80:80          CLOSE_WAIT 6350/npviewer.bin   
tcp        0      1 192.168.0.9:41778       127.0.1.1:80            SYN_SENT   6290/firefox-bin    
tcp        0      1 192.168.0.9:56816       127.0.0.1:80            SYN_SENT   6290/firefox-bin    
tcp        1      0 192.168.0.9:41538       66.249.93.83:80         CLOSE_WAIT 6350/npviewer.bin   
tcp        0      0 192.168.0.9:52170       207.46.111.94:1863      ESTABLISHED6238/pidgin         
tcp        0      1 192.168.0.9:50669       192.168.0.9:80          SYN_SENT   6290/firefox-bin    
tcp        1      0 192.168.0.9:34735       74.208.13.210:80        CLOSE_WAIT 6350/npviewer.bin   
tcp        1      0 192.168.0.9:41537       66.249.93.83:80         CLOSE_WAIT 6350/npviewer.bin   
tcp        0      0 192.168.0.9:56742       66.249.93.18:80         ESTABLISHED6290/firefox-bin    
tcp        0      0 192.168.0.9:46436       72.14.253.125:5222      ESTABLISHED6238/pidgin         
tcp        0      0 192.168.0.9:57646       66.249.93.19:80         ESTABLISHED6290/firefox-bin 
```


If i try to restart apache2 using [FONT="Courier New"]sudo /etc/init.d/apache2 restart[/FONT] i get the following error:

```

stom@igorina:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                httpd (no pid file) not running
(99)Cannot assign requested address: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]


```

*/etc/apache2/sites-available/default* contains the following:

```

NameVirtualHost *
<VirtualHost *>
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
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
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
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.1/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Does anyone have any suggestions? Many thanks in advance!

---

### Post by sreilly on 2008-03-19
Make sure nothing else is already running on port 80 (netstat -an | grep \:80)

Also check the ownership of the log files directory (/var/log/apache2). Should be www-data:www-data

Are there any clues in the messages log file?

---

### Post by Stom on 2008-03-19
I don't think there's anything local running on port 80. The contents of the error log file are below.

```
[Mon Mar 17 18:56:26 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Mon Mar 17 21:03:25 2008] [warn] (101)Network is unreachable: connect to listener on [::]:80
[Mon Mar 17 21:03:25 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 21:03:36 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Mon Mar 17 21:09:08 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Mon Mar 17 21:09:08 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Mar 17 22:31:46 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Tue Mar 18 00:19:31 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Tue Mar 18 00:19:31 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Mar 18 00:19:42 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Tue Mar 18 01:59:04 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Tue Mar 18 01:59:04 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Mar 18 02:02:31 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Tue Mar 18 02:59:49 2008] [notice] caught SIGWINCH, shutting down gracefully
[Tue Mar 18 12:10:24 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 configured -- resuming normal operations
[Tue Mar 18 12:36:07 2008] [notice] caught SIGWINCH, shutting down gracefully
```

Something has changed though, apache2 is not running when i boot and attempting to start it is gving me the same error as above, "could not bind to address 127.0.0.1:80"

Should wiping out apache2 etc and reinstalling solve the problem?

---

### Post by twistedtwig on 2008-03-19
apache is not running because it is throwing an error (as seen in your first post) when you try and start / restart it.

---

### Post by Stom on 2008-03-19
Thank you twistedtwig, i'm aware that when attempting to restar apache it throws an error. What is your suggestion?

---

### Post by twistedtwig on 2008-03-20
curious what results you get if you netstat your IP.  what ports are open and what is running on those ports.

---

