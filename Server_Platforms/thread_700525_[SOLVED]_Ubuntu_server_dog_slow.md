---
title: "[SOLVED] Ubuntu server dog slow"
date: 2008-02-18
forum: Server Platforms
---

### Post by timboellis on 2008-02-18
I have been using Ubuntu as a webserver for about 3 months but today the server is so slow even just to bring up a html page talking minutes.

However done all the usual rebooted the server switch, router etc. however if i go the the server and load the page up it is fine only when accessing it from another computer on the network.

However I also have Webmin installed if I go to the webmin page it is perfect no speed issues at all just when I go to the web page it is very very slow

There has been no changed other than yesterday I added another ip to the allow list in Sites Enabled but I have now removed this still the same thing

Any help

---

### Post by cdenley on 2008-02-18
So the page loads slow only when accessed from the server itself? Is it slow to load the page when you open [http://mydomain.com](http://mydomain.com), [http://localhost](http://localhost), or [http://127.0.0.1](http://127.0.0.1)? My initial thought is a name resolution problem. Did you recently configure winbind?

---

### Post by timboellis on 2008-02-18
Right I now have time to explain a bit better....thanks for the response

I have a Ubuntu server in office A with an internal address of 192.168.1.235 I then on the router port forwarded port 80 so that the WAN IP can see it, however I also use the WAN IP to connect from office A as well as office B.

SO if I connect to the device from Office B over the internet everything is fine, but if i connect to the server from office A over the internet address it is dog slow.

Diags I have done,

Checked the ADSL all okay

Unplugged all un nessesary kit from the switch still the same

Just plugged the server and a lone PC into the router bypassing the switch same thing

Reloaded the server

Restarted Apache

Restarted MY SQL

Reloaded router

Reloaded Switch

All still dog slow from office A but office B fast as ever

All okay from office A with internal address

The only changes made was last night I added an ip address to the allow from  into the etc/apache2/sites-enabled, and found out this was wrong so I copied the config from sites-enabled to site-available##########

This i think coudl be the only failure point. but cannot see anything in there here is my config

Sites-available
[PHP]NameVirtualHost *
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
		Order deny,allow
		Deny from all
Allow from WAN
Allow from WAN
Allow from WAN
Allow from WAN
Allow from WAN
Allow from WAN
Allow from 192.168.1.*
Allow from 192.168.0.0
Allow from 127.0.0.1
Allow from WAN
Allow from 192.168.1.12
Allow from 192.168.1.11
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order deny,allow
		Deny from all
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
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

[/PHP]
Sites-enabled
[PHP]NameVirtualHost *
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
		Order deny,allow
		Deny from all
Allow from WAN
Allow from WAN
Allow from WAN
Allow from WAN
Allow from WAN
Allow from WAN
Allow from 192.168.1.*
Allow from 192.168.0.0
Allow from 127.0.0.1
Allow from WAN
Allow from 192.168.1.12
Allow from 192.168.1.11
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order deny,allow
		Deny from all
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
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

[/PHP]

---

### Post by timboellis on 2008-02-18
Here is some of my error logs

[PHP][Sun Feb 17 07:35:24 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 07:35:24 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 16:10:16 2008] [error] [client 211.154.135.232] client denied by server configuration: /var/www/prx1.php
[Sun Feb 17 19:36:21 2008] [error] [client 86.131.169.100] client denied by server configuration: /var/www/call/auth/login.php
[Sun Feb 17 19:45:39 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 8174 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 5660 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 5661 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 5662 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 4627 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 8172 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 28296 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6040 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 29156 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 8175 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 6733 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 29159 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 8176 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] (10)No child processes: cannot send signal 10 to pid 8173 (non-child or already dead)
[Sun Feb 17 19:51:35 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:46 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Sun Feb 17 19:51:50 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:52 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:53 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:53 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:53 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:54 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:54 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:54 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:55 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:55 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:55 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:55 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:56 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:56 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:56 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:56 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:56 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:51:57 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:52:04 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:52:05 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:52:22 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:52:24 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Feb 17 19:53:23 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Sun Feb 17 19:53:24 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:25 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:25 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:53:26 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:54:12 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:54:12 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:57:44 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:57:45 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:57:45 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:57:46 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:57:46 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:57:46 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:57:46 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:49 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:50 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Feb 17 19:58:51 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:51 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:52 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:52 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:53 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:53 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:53 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:58:53 2008] [error] [client 86.165.163.87] client denied by server configuration: /var/www/
[Sun Feb 17 19:59:02 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Sun Feb 17 19:59:35 2008] [error] [client 86.165.163.87] File does not exist: /var/www/favicon.ico
[Mon Feb 18 01:24:41 2008] [error] [client 67.19.246.130] client denied by server configuration: /usr/lib/cgi-bin/firmwarecfg
[Mon Feb 18 08:33:21 2008] [error] [client 81.149.209.236] File does not exist: /var/www/favicon.ico
[Mon Feb 18 09:03:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 09:03:17 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 09:03:18 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 09:03:19 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 09:03:20 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 09:03:56 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 09:12:05 2008] [error] [client 213.120.115.73] File does not exist: /var/www/favicon.ico
[Mon Feb 18 09:21:09 2008] [error] [client 211.154.135.232] client denied by server configuration: /var/www/prx1.php
[Mon Feb 18 09:36:25 2008] [error] [client 81.149.209.236] File does not exist: /var/www/favicon.ico
[Mon Feb 18 10:11:17 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 11:56:08 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 11:56:18 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 12:16:08 2008] [error] [client 85.17.141.27] client denied by server configuration: /usr/lib/cgi-bin/firmwarecfg
[Mon Feb 18 12:50:56 2008] [error] [client 193.113.57.167] client denied by server configuration: /var/www/
[Mon Feb 18 12:52:37 2008] [error] [client 81.149.209.236] File does not exist: /var/www/favicon.ico
[Mon Feb 18 14:00:13 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 14:06:59 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 15:28:43 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 16:21:31 2008] [error] [client 211.154.135.232] client denied by server configuration: /var/www/prx1.php
[Mon Feb 18 17:04:50 2008] [error] [client 213.120.115.73] File does not exist: /var/www/favicon.ico
[Mon Feb 18 18:11:09 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:11:09 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:13:09 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Mon Feb 18 18:17:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:17:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:17:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:17:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:17:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:17:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:17:35 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Feb 18 18:17:35 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:17:45 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Mon Feb 18 18:19:44 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:23:23 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Feb 18 18:26:35 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 18:32:17 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 18:32:25 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 18:32:27 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 18:32:28 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 18:32:29 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 18:32:30 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 18:55:56 2008] [error] [client 192.168.1.66] client denied by server configuration: /var/www/
[Mon Feb 18 18:58:37 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:58:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:58:39 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:58:40 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:58:41 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 18:58:42 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:03:37 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:11:50 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:12:01 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Mon Feb 18 19:12:16 2008] [error] [client 192.168.1.12] client denied by server configuration: /var/www/
[Mon Feb 18 19:12:17 2008] [error] [client 192.168.1.12] client denied by server configuration: /var/www/
[Mon Feb 18 19:12:18 2008] [error] [client 192.168.1.12] client denied by server configuration: /var/www/
[Mon Feb 18 19:12:19 2008] [error] [client 192.168.1.12] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:13:12 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Feb 18 19:13:22 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Mon Feb 18 19:19:28 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 19:41:39 2008] [error] [client 192.168.1.12] File does not exist: /var/www/favicon.ico
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:16 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Feb 18 19:44:26 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Mon Feb 18 19:44:42 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:45 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:47 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:48 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 19:44:49 2008] [error] [client 192.168.1.11] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [error] [client ::1] client denied by server configuration: /var/www/
[Mon Feb 18 19:45:38 2008] [notice] caught SIGWINCH, shutting down gracefully
[Mon Feb 18 19:45:48 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Mon Feb 18 19:45:56 2008] [error] [client 192.168.1.11] File does not exist: /var/www/favicon.ico
[Mon Feb 18 20:13:55 2008] [error] [client 192.168.1.13] client denied by server configuration: /var/www/[/PHP]


The deny messages are from my other PC on a dynamic IP address

---

### Post by cdenley on 2008-02-18
Are "Office A" and "Office B" on the same local network? Are there multiple computers in "Office A" you are having problems with, or just the server? Are you actually connecting to the web server with your WAN IP, or a domain name that resolves to your WAN IP?

---

### Post by timboellis on 2008-02-18
> **cdenley said:**
> Are "Office A" and "Office B" on the same local network? Are there multiple computers in "Office A" you are having problems with, or just the server? Are you actually connecting to the web server with your WAN IP, or a domain name that resolves to your WAN IP?


Office A and B are in two totaly different locations different WAN IP addresses and not connected any any way.

It is mulitple computers that are having the issues connecting to the server however if I connect the the control panel on the server "Webmin" on port 10000 there is no issues at all.

I do not use a domain name at all its just IP's.

The only thing I can think of is possibly changing the port to comthing else like for 50 just to see if t is a port issue being blocked for some reason

---

### Post by cdenley on 2008-02-18
I would try a high port like 8080. If it worked before, but was extremely slow, I would guess it is either a problem with your router, or your ISP is limiting bandwith for web servers.

---

### Post by timboellis on 2008-02-18
> **cdenley said:**
> I would try a high port like 8080. If it worked before, but was extremely slow, I would guess it is either a problem with your router, or your ISP is limiting bandwith for web servers.

Well thats what i first  thought however it work over the internet from site B but not Site AM so the ISP cannto be throttling the service and I did ask as well.



Then the router i doubt as again office B has no issues.

So what I am going to do is build another server just to prove the case maybee see what is different when doing this maybe i did muck up the sites enabled config I will change them to the one I am creating a server with so it has no security this may be a fix

---

### Post by faulkes on 2008-02-18
Depending on the router you are using, I know that linksys routers had an issue with port forwarding in 
that local requests would get sent to the router and in turn port forwarded back to web server and 
then back to the client.

That may be the situation you are encountering.  Check your router vendors website for a firmware 
upgrade or if that is actually the issue.

Faulkes

---

### Post by timboellis on 2008-02-19
Thats me fixed it, the problem was with the sites_available config, what I do not knwo

However I built the same server build on another machine copied the same files accross the the other server and workign perfectly

Thanks for all your help

---

