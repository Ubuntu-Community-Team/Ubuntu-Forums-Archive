---
title: "Can't see LAMP from internet"
date: 2011-02-10
forum: Server Platforms
---

### Post by DrReaper on 2011-02-10
Hi Everyone,

I have a lamp server setup running a Wordpress blog. The problem I am encountering is I can access the blog on the local network but I cannot access through the internet. 

If I try to access the external ip 76.89.114.72 and plug in port 80 IE [http://76.89.114.72:80](http://76.89.114.72:80) I can see the default Apache is working page. If I add /blog/ 
IE ([http://76.89.114.72:80/blog/](http://76.89.114.72:80/blog/)) nothing loads. 

Any help would be great.

---

### Post by acelino on 2011-02-10
Hi,


Try to edit your host file. Put the ip address and your website name " " not included. Then open your IE and type your website name.


 76.89.114.72 "website_name" 


Cheers

---

### Post by DrReaper on 2011-02-10
I added my Ubuntu computer to the DMZ on my router and I still can't get to the Wordpress blog from the internet. Is there a file I can look at that controls access or something? Anything? I have been scanning web pages for hours.

I also called my ISP and they told me they are not blocking any ports to my computer.

---

### Post by acelino on 2011-02-10
i forgot to mention, edit your host file on the client side.

---

### Post by pytheas22 on 2011-02-10
Do your /var/log/apache2/access.log or /var/log/apache2/error.log files show anything pertinent?  Do they show attempts to GET anything in the blog directory or is it not mentioned?  If it's not mentioned anywhere in the logs, that probably means it's a networking issue and your requests aren't even reaching the server.  If it's showing attempts to access the blog URL but something's going wrong when it tries to serve those files, it's probably an issue with your server configuration (and in that case the error.log might be able to point you to the specific problem).

Also, when you say the blog page doesn't load, do you mean you get a blank page or something, or a server-not-found type of error?

Are you sure it's not an issue with the browser loading a cached version of the page?  You could clear your cache or try a different browser to be sure.

---

### Post by DrReaper on 2011-02-10
I am pretty sure I am getting to the server as i can open the default apache2 webpage. 

When I setup wordpress the instructions had me make a directory in /var/www/blog/
and put everything inside it. My index.php is inside that folder. 

If I address the folder on my local network url/blog it loads. If I try from the internet I can load the default apache2 webpage but nothing else. 

I guess I need to know how to get the lamp to send all requests to the /var/www/blog/ folder instead of the /var/www/ folder.

---

### Post by cariboo on 2011-02-10
Have you tried accessing the blog from outside your home network?

You should have a configuration file in /etc/apache2/sites-enabled to tell apache2 where to look for the document root.

---

### Post by DrReaper on 2011-02-10
I have been troubleshooting the setup using myremotebrowser.com

Anyway I am going back to my image after trying to copy everything from /var/www/blog to /var/www/

It didn't work. I am not sure what to put into the 000-default file. It's blank right now.

---

### Post by pytheas22 on 2011-02-11
This should work for the 000-default file:

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
```

Then the default Apache page would be available at [http://your-ip-address](http://your-ip-address) and the blog would be at [http://your-ip-address/blog](http://your-ip-address/blog)

You could also try moving everything in /var/www/blog up a directory, which would then make your blog accessible at [http://your-ip-address](http://your-ip-address).  Does that work?

I'd also still highly recommend looking more closely at the log files in /var/log/apache2.  Unless it's simply a networking issue and the http requests for the blog site from external hosts are not reaching your server at all, the log files would probably tell you why the stuff in /var/www/blog is not being served.

---

### Post by DrReaper on 2011-02-11
This is in my sites-available/default

[PHP]<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www >
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
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
[/PHP]My sites-available/default-ssl 

[PHP]       
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www >
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
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

        CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

        Alias /doc/ "/usr/share/doc/"
        <Directory "/usr/share/doc/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

        #   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
        SSLEngine on

        #   A self-signed (snakeoil) certificate can be created by installing
        #   the ssl-cert package. See
        #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
        #   If both key and certificate are stored in the same file, only the
        #   SSLCertificateFile directive is needed.
        SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

         # Clip a lot of text instruction

        #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>

[/PHP]and of course my sites-enabled/000-default has this in it.

[PHP]             
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www >
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
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


[/PHP]I thought it was empty but it isn't.

---

### Post by DrReaper on 2011-02-11
This is in the error log a lot 

[Thu Feb 10 19:18:42 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)

---

### Post by pytheas22 on 2011-02-11
That seems strange, but at least now we're getting a better idea of what it could be.  What is the output of:
```

ls -l /var/www/blog
```

That might be the key.

---

### Post by DrReaper on 2011-02-11
[PHP]ls -l /var/www/blog[/PHP]

total 324
-rw-r--r-- 1 www-data www-data  3503 2011-01-28 14:01 \
-rw-r--r-- 1 www-data www-data     0 2011-02-10 15:04 apache2.conf
-rw-r--r-- 1 www-data www-data  2354 2011-01-31 10:48 bb-config.php
-rw-r--r-- 1 www-data www-data   397 2008-05-25 13:33 index.php
-rw-r--r-- 1 www-data www-data 15410 2008-12-05 23:47 license.txt
-rw-r--r-- 1 www-data www-data  9120 2010-12-29 13:07 readme.html
-rw-r--r-- 1 www-data www-data  4391 2010-04-19 05:01 wp-activate.php
drwxr-xr-x 7 www-data www-data  4096 2010-12-29 13:15 wp-admin
-rw-r--r-- 1 www-data www-data 40284 2010-07-25 00:34 wp-app.php
-rw-r--r-- 1 www-data www-data   220 2008-10-13 23:22 wp-atom.php
-rw-r--r-- 1 www-data www-data   274 2008-05-25 08:50 wp-blog-header.php
-rw-r--r-- 1 www-data www-data  3926 2010-05-06 08:38 wp-comments-post.php
-rw-r--r-- 1 www-data www-data   238 2008-10-13 23:22 wp-commentsrss2.php
-rw-r--r-- 1 www-data www-data  3512 2011-01-28 14:02 wp-config.php
drwxr-xr-x 6 www-data www-data  4096 2011-02-10 18:10 wp-content
-rw-r--r-- 1 www-data www-data  1255 2010-03-16 21:39 wp-cron.php
-rw-r--r-- 1 www-data www-data   240 2010-04-19 05:03 wp-feed.php
drwxr-xr-x 7 www-data www-data  4096 2010-12-29 13:15 wp-includes
-rw-r--r-- 1 www-data www-data  2002 2010-03-18 01:39 wp-links-opml.php
-rw-r--r-- 1 www-data www-data  2441 2010-02-28 04:19 wp-load.php
-rw-r--r-- 1 www-data www-data 26059 2010-06-01 08:54 wp-login.php
-rw-r--r-- 1 www-data www-data  7774 2010-05-25 19:42 wp-mail.php
-rw-r--r-- 1 www-data www-data   487 2009-04-20 14:50 wp-pass.php
-rw-r--r-- 1 www-data www-data   218 2008-10-13 23:22 wp-rdf.php
-rw-r--r-- 1 www-data www-data   316 2008-05-25 08:50 wp-register.php
-rw-r--r-- 1 www-data www-data   220 2008-10-13 23:22 wp-rss2.php
-rw-r--r-- 1 www-data www-data   218 2008-10-13 23:22 wp-rss.php
-rw-r--r-- 1 www-data www-data  9177 2010-05-02 15:18 wp-settings.php
-rw-r--r-- 1 www-data www-data 18695 2010-07-21 13:10 wp-signup.php
-rw-r--r-- 1 www-data www-data  3702 2010-02-24 12:13 wp-trackback.php
-rw-r--r-- 1 www-data www-data 95481 2010-12-08 09:58 xmlrpc.php

---

### Post by pytheas22 on 2011-02-12
None of the files have executable permissions, which is probably at least part of the problem.  Since they're PHP scripts they need to be executed in order to work (unlike static html files, on which you only need read permissions).

Does anything change if you run this command to make all the files executable:
```

sudo chmod -R 755 /var/www/blog
```

Also, did you change the ownership of those files to www-data yourself?  I'm not positive, but I thought that on Ubuntu by default root would own everything inside /var/www and its subdirectories.  That's how it's set up on my machine, at least (although all I host is a wiki that I access locally).

---

### Post by DrReaper on 2011-02-12
-rwxr-xr-x 1 root root  3503 2011-01-28 14:01 \
-rwxr-xr-x 1 root root     0 2011-02-10 15:04 apache2.conf
-rwxr-xr-x 1 root root  2354 2011-01-31 10:48 bb-config.php
-rwxr-xr-x 1 root root   397 2008-05-25 13:33 index.php
-rwxr-xr-x 1 root root 15410 2008-12-05 23:47 license.txt
-rwxr-xr-x 1 root root  9120 2010-12-29 13:07 readme.html
-rwxr-xr-x 1 root root  4391 2010-04-19 05:01 wp-activate.php
drwxr-xr-x 7 root root  4096 2010-12-29 13:15 wp-admin
-rwxr-xr-x 1 root root 40284 2010-07-25 00:34 wp-app.php
-rwxr-xr-x 1 root root   220 2008-10-13 23:22 wp-atom.php
-rwxr-xr-x 1 root root   274 2008-05-25 08:50 wp-blog-header.php
-rwxr-xr-x 1 root root  3926 2010-05-06 08:38 wp-comments-post.php
-rwxr-xr-x 1 root root   238 2008-10-13 23:22 wp-commentsrss2.php
-rwxr-xr-x 1 root root  3512 2011-01-28 14:02 wp-config.php
drwxr-xr-x 6 root root  4096 2011-02-10 18:10 wp-content
-rwxr-xr-x 1 root root  1255 2010-03-16 21:39 wp-cron.php
-rwxr-xr-x 1 root root   240 2010-04-19 05:03 wp-feed.php
drwxr-xr-x 7 root root  4096 2010-12-29 13:15 wp-includes
-rwxr-xr-x 1 root root  2002 2010-03-18 01:39 wp-links-opml.php
-rwxr-xr-x 1 root root  2441 2010-02-28 04:19 wp-load.php
-rwxr-xr-x 1 root root 26059 2010-06-01 08:54 wp-login.php
-rwxr-xr-x 1 root root  7774 2010-05-25 19:42 wp-mail.php
-rwxr-xr-x 1 root root   487 2009-04-20 14:50 wp-pass.php
-rwxr-xr-x 1 root root   218 2008-10-13 23:22 wp-rdf.php
-rwxr-xr-x 1 root root   316 2008-05-25 08:50 wp-register.php
-rwxr-xr-x 1 root root   220 2008-10-13 23:22 wp-rss2.php
-rwxr-xr-x 1 root root   218 2008-10-13 23:22 wp-rss.php
-rwxr-xr-x 1 root root  9177 2010-05-02 15:18 wp-settings.php
-rwxr-xr-x 1 root root 18695 2010-07-21 13:10 wp-signup.php
-rwxr-xr-x 1 root root  3702 2010-02-24 12:13 wp-trackback.php
-rwxr-xr-x 1 root root 95481 2010-12-08 09:58 xmlrpc.php

Yes someone else suggested I change the file to www-data so I did. I changed the permission and it didn't work. I changed back to root and it still isn't loading.

---

### Post by pytheas22 on 2011-02-12
hmmm, would you mind trying to visit the blog from an external computer a few times, then post the output of:
```

tail -50 /var/log/apache2/error.log
tail -50 /var/log/apache2/access.log
```

Seeing the actual log files could help.

---

### Post by DrReaper on 2011-02-12
Ok here is the error.log

[Thu Feb 10 18:25:23 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 18:25:24 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 18:25:32 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 18:25:33 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 18:43:34 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 18:43:35 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 18:45:08 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 18:45:09 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 18:45:20 2011] [error] [client 192.168.1.154] File does not exist: /var/www/favicon.ico
[Thu Feb 10 18:45:26 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 18:46:13 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 18:46:39 2011] [error] [client 192.168.1.148] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 18:46:39 2011] [error] [client 192.168.1.148] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 18:59:44 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 18:59:45 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 18:59:52 2011] [error] [client 192.168.1.154] File does not exist: /var/www/favicon.ico
[Thu Feb 10 18:59:56 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 18:59:57 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 19:08:04 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 19:08:05 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 19:08:13 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.
[Thu Feb 10 19:10:46 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 19:10:47 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 19:10:57 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.
[Thu Feb 10 19:15:08 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 19:15:09 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 19:15:15 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.
[Thu Feb 10 19:15:18 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.
[Thu Feb 10 19:16:01 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 19:16:02 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 19:16:14 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.
[Thu Feb 10 19:16:16 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.
[Thu Feb 10 19:18:32 2011] [notice] caught SIGTERM, shutting down
[Thu Feb 10 19:18:33 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 10 19:18:41 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Thu Feb 10 19:18:42 2011] [error] [client 192.168.1.154] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace., referer: [http://192.168.1.154/blog/](http://192.168.1.154/blog/)
[Fri Feb 11 01:00:59 2011] [error] [client 58.218.199.147] script '/var/www/proxyheader.php' not found or unable to stat
[Fri Feb 11 05:37:52 2011] [error] [client 66.249.71.2] File does not exist: /var/www/robots.txt
[Fri Feb 11 08:13:02 2011] [error] [client 58.218.199.147] script '/var/www/proxyheader.php' not found or unable to stat
[Fri Feb 11 10:37:27 2011] [error] [client 58.218.199.147] script '/var/www/proxyheader.php' not found or unable to stat
[Fri Feb 11 20:14:13 2011] [error] [client 58.218.199.147] script '/var/www/ip.php' not found or unable to stat
[Fri Feb 11 20:24:08 2011] [error] [client 109.230.246.172] File does not exist: /var/www/config
[Fri Feb 11 22:37:41 2011] [error] [client 58.218.199.147] script '/var/www/proxyheader.php' not found or unable to stat
[Sat Feb 12 01:00:14 2011] [error] [client 58.218.199.147] script '/var/www/proxyheader.php' not found or unable to stat
[Sat Feb 12 01:51:44 2011] [error] [client 109.230.246.172] File does not exist: /var/www/config
[Sat Feb 12 04:29:28 2011] [error] [client 75.99.102.74] File does not exist: /var/www/favicon.ico
[Sat Feb 12 05:49:25 2011] [error] [client 58.218.199.147] script '/var/www/proxyheader.php' not found or unable to stat
[Sat Feb 12 08:13:06 2011] [error] [client 58.218.199.147] script '/var/www/judge.php' not found or unable to stat
[Sat Feb 12 09:31:38 2011] [notice] caught SIGTERM, shutting down
[Sat Feb 12 13:02:54 2011] [notice] Apache/2.2.16 (Ubuntu) PHP/5.3.3-1ubuntu9.3 with Suhosin-Patch configured -- resuming normal operations

and here is the access.log

192.168.1.154 - - [10/Feb/2011:19:08:13 -0800] "GET /blog HTTP/1.1" 500 640 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:10:57 -0800] "GET /blog HTTP/1.1" 500 640 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:15:15 -0800] "GET /favicon.ico HTTP/1.1" 500 640 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:15:18 -0800] "GET /blog HTTP/1.1" 500 640 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:16:14 -0800] "GET /favicon.ico HTTP/1.1" 500 640 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:16:16 -0800] "GET /blog HTTP/1.1" 500 640 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:41 -0800] "GET /blog HTTP/1.1" 301 557 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:41 -0800] "GET /blog/ HTTP/1.1" 200 3892 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:41 -0800] "GET /blog/wp-includes/js/jquery/jquery.js?ver=1.4.2 HTTP/1.1" 304 215 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:41 -0800] "GET /blog/wp-content/plugins/agegate/style/style.css HTTP/1.1" 500 640 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:41 -0800] "GET /blog/?itx=js&ver=3.0.4 HTTP/1.1" 200 4805 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:41 -0800] "GET /blog/?itx=css&ver=3.0.4 HTTP/1.1" 200 5062 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:42 -0800] "GET /blog/wp-content/plugins/agegate/style/style.css HTTP/1.1" 500 640 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:42 -0800] "GET /blog/wp-includes/js/jquery/ui.core.js?ver=1.7.3 HTTP/1.1" 304 213 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:42 -0800] "GET /blog/wp-includes/js/jquery/ui.tabs.js?ver=1.7.3 HTTP/1.1" 304 213 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:42 -0800] "GET /blog/wp-includes/js/jquery/jquery.color.js?ver=2.0-4561m HTTP/1.1" 304 212 "http://192.168.1.154/blog/" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.154 - - [10/Feb/2011:19:18:42 -0800] "GET /blog/?itx=css&ver=3.0.4 HTTP/1.1" 200 5062 "http://192.168.1.154/blog/?itx=css&ver=3.0.4" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
58.218.199.147 - - [11/Feb/2011:01:00:59 -0800] "GET [http://piceducation.com/proxyheader.php](http://piceducation.com/proxyheader.php) HTTP/1.1" 404 536 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
66.249.71.2 - - [11/Feb/2011:05:37:52 -0800] "GET /robots.txt HTTP/1.1" 404 505 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
66.249.71.2 - - [11/Feb/2011:05:37:52 -0800] "GET /blog/ HTTP/1.1" 302 333 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
58.218.199.147 - - [11/Feb/2011:08:13:02 -0800] "GET [http://www.infodownload.info/proxyheader.php](http://www.infodownload.info/proxyheader.php) HTTP/1.1" 404 541 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [11/Feb/2011:10:37:27 -0800] "GET [http://98.126.15.13/proxyheader.php](http://98.126.15.13/proxyheader.php) HTTP/1.1" 404 532 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
69.175.71.234 - - [11/Feb/2011:12:20:27 -0800] "GET / HTTP/1.1" 200 461 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [11/Feb/2011:12:20:36 -0800] "GET /blog/ HTTP/1.1" 302 232 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
58.218.199.147 - - [11/Feb/2011:20:14:13 -0800] "GET [http://www.travelimgusa.com/ip.php](http://www.travelimgusa.com/ip.php) HTTP/1.1" 404 531 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
109.230.246.172 - - [11/Feb/2011:20:24:08 -0800] "GET [http://66.196.106.201/config/pwtoken_get?](http://66.196.106.201/config/pwtoken_get?) HTTP/1.0" 404 499 "-" "-"
58.218.199.147 - - [11/Feb/2011:22:37:41 -0800] "GET [http://www.infodownload.info/proxyheader.php](http://www.infodownload.info/proxyheader.php) HTTP/1.1" 404 541 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
58.218.199.147 - - [12/Feb/2011:01:00:14 -0800] "GET [http://www.eduju.com/proxyheader.php](http://www.eduju.com/proxyheader.php) HTTP/1.1" 404 533 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
109.230.246.172 - - [12/Feb/2011:01:51:44 -0800] "GET [http://209.191.92.75/config/login?](http://209.191.92.75/config/login?) HTTP/1.0" 404 492 "-" "-"
95.76.37.120 - - [12/Feb/2011:04:26:14 -0800] "GET / HTTP/1.0" 200 454 "-" "-"
75.99.102.74 - - [12/Feb/2011:04:29:28 -0800] "GET / HTTP/1.1" 200 485 "http://ubuntuforums.org/showthread.php?t=1685398" "Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13"
75.99.102.74 - - [12/Feb/2011:04:29:28 -0800] "GET /favicon.ico HTTP/1.1" 404 504 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13"
75.99.102.74 - - [12/Feb/2011:04:29:34 -0800] "GET /blog/ HTTP/1.1" 302 333 "http://ubuntuforums.org/showthread.php?t=1685398" "Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13"
58.218.199.147 - - [12/Feb/2011:05:49:25 -0800] "GET [http://www.infodownload.info/proxyheader.php](http://www.infodownload.info/proxyheader.php) HTTP/1.1" 404 541 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
67.231.70.22 - - [12/Feb/2011:07:16:32 -0800] "GET / HTTP/1.0" 200 454 "-" "-"
77.64.158.100 - - [12/Feb/2011:07:56:38 -0800] "GET / HTTP/1.0" 200 454 "-" "-"
58.218.199.147 - - [12/Feb/2011:08:13:06 -0800] "GET [http://ppcfinder.net/judge.php](http://ppcfinder.net/judge.php) HTTP/1.1" 404 527 "-" "Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)"
69.175.71.234 - - [12/Feb/2011:13:04:20 -0800] "GET / HTTP/1.1" 200 461 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:13:04:25 -0800] "GET /blog/ HTTP/1.1" 302 232 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:13:16:14 -0800] "GET / HTTP/1.1" 200 461 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:13:16:21 -0800] "GET /blog HTTP/1.1" 301 540 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:13:16:21 -0800] "GET /blog/ HTTP/1.1" 302 232 "http://76.89.114.72/blog" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:13:20:12 -0800] "GET /blog/ HTTP/1.1" 302 232 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:17:53:43 -0800] "GET /blog/ HTTP/1.1" 302 232 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:17:58:01 -0800] "GET / HTTP/1.1" 200 461 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:17:58:02 -0800] "GET / HTTP/1.1" 200 461 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:17:58:19 -0800] "GET / HTTP/1.1" 200 461 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:17:58:28 -0800] "GET /blog/ HTTP/1.1" 302 232 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:18:01:38 -0800] "GET /blog HTTP/1.1" 301 540 "-" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"
69.175.71.234 - - [12/Feb/2011:18:01:38 -0800] "GET /blog/ HTTP/1.1" 302 232 "http://76.89.114.72/blog" "Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US; rv:1.9.2.13) Gecko/20101203 Firefox/3.6.13 (.NET CLR 3.5.30729)"

When I try to access the server from myremotebrowser.com I can load the page that says "It works!"
When I try to access the ip/blog it never loads. The progress bar goes half way across the screen and stops. I loaded the "it works page a few times and switched to partial load."

---

### Post by pytheas22 on 2011-02-13
Thanks for the logs; they help a lot.  I'm pretty sure the issue is that you have a rewrite rule somewhere that's telling the server to rewrite the URL [http://76.89.114.72/blog](http://76.89.114.72/blog) to [http://192.168.1.154/blog--this](http://192.168.1.154/blog--this) would explain why you have all those errors in the logs about "Request exceeded the limit of 10 internal redirects due to probable configuration error," as well as why when I try to open [http://76.89.114.72/blog](http://76.89.114.72/blog) in a browser it fails and tells me, "Firefox can't establish a connection to the server at 192.168.1.154."  Of course, from within your local network, this would not be a problem because 192.168.1.154 would be reachable.

Normally there would only be two places where you could have a rewrite rule: in your site configuration files inside the /etc/apache2/sites-enabled directory, or in a .htaccess file inside the /var/www/blog directory.  You've already posted the latter files and I don't see any rewrites there.  If you have a .htaccess file, could you please post that?  Otherwise, you could probably find the offending file with commands like:

```
sudo grep -iR 192.168.1.154 /var/www
sudo grep -iR 192.168.1.154 /etc/apache
```

which would return the names of all files inside /var/www and /etc/apache containing "192.168.1.154" and should locate the offending rewrite rule.

---

### Post by elico on 2011-02-13
in wordpress system you must use a domain name for the system.
get into the admin panel and on the site info\settings change the site name to your domain name.

---

### Post by DrReaper on 2011-02-13
.htaccess

[PHP]
RewriteEngine On
RewriteBase /blog/
RewriteRule ^index\.php$ - [L]

# uploaded files
RewriteRule ^([_0-9a-zA-Z-]+/)?files/(.+) wp-includes/ms-files.php?file=$2 [L]

# add a trailing slash to /wp-admin
RewriteRule ^([_0-9a-zA-Z-]+/)?wp-admin$ $1wp-admin/ [R=301,L]

RewriteCond %{REQUEST_FILENAME} -f [OR]
RewriteCond %{REQUEST_FILENAME} -d
RewriteRule ^ - [L]
RewriteRule ^([_0-9a-zA-Z-]+/)?(wp-(content|admin|includes).*) $2 [L]
RewriteRule ^([_0-9a-aA-Z-]+/)?(.*\.php)$ $2 [L]
RewriteRule . index.php [L]

[/PHP]

I had to add the rewrite rule to get wordpress with buddypress working. The buddypress links would fail to a 404 error if I didn't redirect them. 

chris@ubuntulocal:/var/www/blog$ sudo grep -iR 192.168.1.154 /var/www

/var/www/blog/bb-config.php:$bb->uri = 'http://192.168.1.154/blog/wp-content/plugins/buddypress/bp-forums/bbpress/';
/var/www/blog/\:define( 'DOMAIN_CURRENT_SITE', '192.168.1.154' );
/var/www/blog/wp-config.php:define( 'DOMAIN_CURRENT_SITE' , '192.168.1.154' );
chris@ubuntulocal:/var/www/blog$ sudo grep -iR 192.168.1.154 /etc/apache

elico - I went into the site admin for wordpress and the option you said to change is ghosted. I cannot change it from there.

---

### Post by elico on 2011-02-14
in wordpress admin panel you have SETTINGS>GENERAL.
in general you have "install address"
and BLOG ADRESS
these are what i am talking about.

---

### Post by DrReaper on 2011-02-14
I installed the wordpress multi-user verson in order to get buddypress working. I go to Settings/ General and the options your talking about are not there.

I get the following options...
Site Title 
Tagline
E-mail Address
Timezone
Date Format
Time Format
Week Starts On

---

### Post by elico on 2011-02-14
well you will need to check it using the mysql database.
in the wp_options table you should have these

option_id     blog_id     option_name     option_value                                    autoload
  4                   0             siteurl      [http://.](http://.)...       yes
 39                  0              home      [http://.](http://.)...       yes


and make sure they are not set to your ip address

---

### Post by DrReaper on 2011-02-14
I already have a website running. Can I configure new server to use the existing domain name before I redirect it to this IP?

I am going to look for these entries now.

---

### Post by pytheas22 on 2011-02-15
> I had to add the rewrite rule to get wordpress with buddypress working. The buddypress links would fail to a 404 error if I didn't redirect them.


So it sounds like you're redirecting all requests for [http://76.89.114.72/blog](http://76.89.114.72/blog) to [http://192.168.1.154/blog](http://192.168.1.154/blog).  Is there a reason you can't reverse this and just redirect everything to the external IP?  That way both internal and external connections should work, and your problem should be solved.  I'm not familiar with buddypress but hopefully this would work.

I wouldn't think it would make sense for buddypress to force you to redirect everything to a private IP address, because in many cases you might be running WordPress on a server that has no private IP.

Also, any luck finding the siteurl in the mysql database?

---

### Post by DrReaper on 2011-02-15
[SIZE=4][SIZE=3]I got phpmyadmin running after a lot of trying. I edited the database and changed every instance of 192.168.1.154 in my wordpress database to my external IP. 

If I try the external bowser I get the wordpress login screen!

Is this progress? I wanted to see a website.

I login and view the website I get a ERROR ESTABLISHING DATABASE CONNECTION message. [/SIZE]
[/SIZE]

---

### Post by DrReaper on 2011-02-15
I tried removing the redirect in the .htaccess and that also failed.

---

### Post by DrReaper on 2011-02-16
[SIZE=4]I went back to my image so I can access the website. Here are the entries in the wordpress database that have to do with ip address.

wp-blogs (domain: 192.168.1.154)
wp-options (siteurl: 192.168.1.154/blog)
wp-site (domain: 192.168.1.154)
wp-sitemeta (siteurl: 192.168.1.154/blog)
wp-usermeta (siteurl: 192.168.1.154)

It looks like all the posts are also pointing to 192.168.1.154
[/SIZE]

---

### Post by DrReaper on 2011-02-16
I changed all the ip address entries to my external ip, including the post ips. Now when i put the external ip address I get the default apache2 page showing it's responding to external requests. If I pull the external ip /blog I get the wordpress login screen. I also get this link in the error window

[http://76.89.114.72/blog/wp-login.php?redirect_to=http%3A%2F%2F76.89.114.72%2Fblog%2Fwp-admin%2F&reauth=1](http://76.89.114.72/blog/wp-login.php?redirect_to=http%3A%2F%2F76.89.114.72%2Fblog%2Fwp-admin%2F&reauth=1)

I still can't browse the website even after I log into the wordpress admin page.

---

### Post by pytheas22 on 2011-02-16
> I got phpmyadmin running after a lot of trying. I edited the database and changed every instance of 192.168.1.154 in my wordpress database to my external IP.

If I try the external bowser I get the wordpress login screen!

Is this progress? I wanted to see a website.

I login and view the website I get a ERROR ESTABLISHING DATABASE CONNECTION message. 

Yes, I would say it's a sign of progress that you got the login screen.  It means you solved the networking issue that was preventing your site from being served properly.

You probably got the login screen because you have WordPress configured to require logins in order to view any content.  You can change that easily enough.

As for the "error establishing database connection," are you sure mysql was running and that WordPress is configured with the correct database name and the correct password?  If not, did the error message provide any more information to pinpoint the problem?  Otherwise, I'd check /var/log/mysql/error.log for clues.

> I still can't browse the website even after I log into the wordpress admin page. 

Because it's still giving you the error about failing to establish a database connection, or because of a different error?  It would be helpful to know the exact error message(s) you're getting.

---

### Post by DrReaper on 2011-02-16
The sql error log is empty. Also I didn't have a problem loading the website on the LAN. It never asked to login first. I tried it on three workstations to be sure. Whatever is causing this error it's surreal.

---

### Post by pytheas22 on 2011-02-16
Thinking about this more, if WordPress is trying to connect to your database over the network rather than locally, changing the IP address could be causing the database errors.  I'd check the wp-config.php file and see what value you have set for 'DB_HOST' (on my WordPress setup, this is on the sixth line of wp-config.php).

Otherwise, I'm not sure what's wrong, if you're positive mysql is running and things seem to be working alright when you access the site from a local computer.  Your best bet may be simply to try reinstalling WordPress from scratch, making sure to use only the external IP address this time when configuring it.  You certainly wouldn't be the first Linux user to have to go back to square one...

---

### Post by DrReaper on 2011-02-16
I think we are making progress as I can see the site now from the internet!!!

I changed all the DB IP's to the external. I then did a search of the files on the computer and low and behold Buddypress had my ip as 192.168.1.154. So did some other files. I changed everything to the external and its responding.

For some reason my formatting went crazy. I am going to restore it, fix it again and see if fixing it somehow effected the theme.

---

### Post by DrReaper on 2011-02-16
Pytheas22 and Elico You guys rock. Thanks a lot! I was able to fix it thanks to your help. 

Here is the site in its infancy... [http://76.89.114.72/blog](http://76.89.114.72/blog)

I was able to fix the formatting error by changing themes. It took hours to figure that one out... :)

---

### Post by pytheas22 on 2011-02-17
Glad you finally got it straightened out.  Thanks for your patience through all the shooting in the dark until we got on the right path.  Happy blogging!

---

