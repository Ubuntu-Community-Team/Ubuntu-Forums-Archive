---
title: "Unable to restart apache"
date: 2014-03-22
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-03-22
When I try to restart apache I get the following error
```

root@server11362:~# sudo service apache2 restart
 * Restarting web server apache2                                                                              (98)Address already in use: make_sock: could not bind to address 111.90.150.93:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.

```
In fact the apache log contains no more information.

netstat -tulpn returns the following
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1098/mysqld     
tcp        0      0 127.0.0.1:6379          0.0.0.0:*               LISTEN      1414/redis-server
tcp        0      0 111.90.150.93:53        0.0.0.0:*               LISTEN      1068/named      
tcp        0      0 111.90.150.92:53        0.0.0.0:*               LISTEN      1068/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1068/named      
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      1194/postgres   
tcp        0      0 0.0.0.0:44888           0.0.0.0:*               LISTEN      845/sshd        
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1395/master     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1068/named      
tcp        0      0 0.0.0.0:6081            0.0.0.0:*               LISTEN      1435/varnishd   
tcp        0      0 127.0.0.1:6082          0.0.0.0:*               LISTEN      1434/varnishd   
tcp6       0      0 :::53                   :::*                    LISTEN      1068/named      
tcp6       0      0 :::44888                :::*                    LISTEN      845/sshd        
tcp6       0      0 :::25                   :::*                    LISTEN      1395/master     
tcp6       0      0 ::1:953                 :::*                    LISTEN      1068/named      
tcp6       0      0 :::6081                 :::*                    LISTEN      1435/varnishd   
udp        0      0 111.90.150.93:53        0.0.0.0:*                           1068/named      
udp        0      0 111.90.150.92:53        0.0.0.0:*                           1068/named      
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1068/named      
udp6       0      0 :::53      

```
There is nothing on port 80 but I still cannot restart

Help please!

---

### Post by CharlesA on 2014-03-22
You don't need sudo if you are running as root. ;)

Try stopping apache first and starting it back up and see if it throws the same error.

---

### Post by astarmathsandphysics on 2014-03-23
Yes it does, and if I reboot too

I have reinstalled apache - same problem

---

### Post by Lars Noodén on 2014-03-23
How is the configuration looking?

```

apache2ctl configtest
a2query -s 

```

---

### Post by astarmathsandphysics on 2014-03-23
apache2ctl configtest

syntax OK

a2query -s

a2query: command not found

It also says 

root@server11362:~# sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 111.90.150.93:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.

---

### Post by Lars Noodén on 2014-03-23
Maybe you could try running it in the foreground with increased logging.

```

. /etc/apache2/envvars
/usr/sbin/apache2 -X -e debug 2>&1 |less

```

Also, is the ip address mentioned in your error message the same on that is used on any of your network interfaces?

---

### Post by CharlesA on 2014-03-23
> **Lars Noodén said:**
> 
Also, is the ip address mentioned in your error message the same on that is used on any of your network interfaces?

Should be considering bind is listening on the same interface: 111.90.150.93

---

### Post by astarmathsandphysics on 2014-03-23
At the moment the only ip address condigured is 111.90.150.92

Everything was working until Friday morning, when I was changing some .htaccess settings 

I did not change any network settings

---

### Post by Doug S on 2014-03-23
Well, I think you have many of us stumped. Please post your /etc/apache2/ports.conf file. Mine is the default:```
doug@s15:~/docs-1404/ubuntu-docs/ubuntu-help$ [COLOR=#ff0000]cat /etc/apache2/ports.conf[/COLOR]
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```I ask because I can create your error message by adding another attempt to use port 80 in ports.conf (even though I didn't do it right, the point is that it is apache itself trying to bind to the port twice):```
doug@s15:/etc/apache2$ [COLOR=#ff0000]sudo service apache2 restart[/COLOR]
 * Restarting web server apache2       [Sun Mar 23 13:52:48 2014] [warn] NameVirtualHost 192.168.111.112:80 has no VirtualHosts
 ... waiting [Sun Mar 23 13:52:49 2014] [warn] NameVirtualHost 192.168.111.112:80 has no VirtualHosts
[COLOR=#ff0000](98)Address already in use: make_sock: could not bind to address 0.0.0.0:80[/COLOR]
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
```To create the above error, I added this to ports.conf:```
NameVirtualHost 192.168.111.112:80
Listen 80
```

---

### Post by astarmathsandphysics on 2014-03-23
here is /etc/apache2/ports.config

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

---

### Post by Doug S on 2014-03-23
O.K. so your ports.conf file is the default. The point I was trying to make is, I suggest, still valid. The reason you don't see anything with "netstat -tulpn" is because it is apache itself binding to the port and then trying to bind to it again. Why? I don't know, but I would suggest to continue looking at your config files.

---

### Post by astarmathsandphysics on 2014-03-23
That sounds possible. I had the same issue on Friday, then for some reason after a couple of hours, everything started working again.

---

### Post by Doug S on 2014-03-23
For example: I was able to create the same error by messing with /etc/apache2/sites-available/default.```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]sudo service apache2 restart[/COLOR]
 * Restarting web server apache2         (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
```

---

### Post by astarmathsandphysics on 2014-03-24
This is /etc/apache2/sites-avai;lablexxxxxxxx.info

can you identity any possible errors

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
ServerName courseworkbank.info
ServerAlias [www.xxxxxxx.info](www.xxxxxxx.info)
	DocumentRoot /var/www/courseworkbank
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/courseworkbank/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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

---

### Post by volkswagner on 2014-03-24
Perhaps you can explain your setup a bit more.  Is this a virtual machine?  How many physical/virtual network adapters?  Can you post /etc/network/interfaces?
Do you have a service bound to a specific adapter?

I see you have at least two public ip addresses. *.*.*.92 responds to pings and is hosting website at the moment. *.*.*.93 does not respond to pings.
Are both ip's behind the same firewall/non firewall?  I think your problem is not with Apache2.

According to your website, it does seem apache or a different web server is running.  Do you have Nginx or something else installed.

What's the output of:
```
 ps aux | grep apache2
```

---

### Post by astarmathsandphysics on 2014-03-24
Found the issue.
While trying to configure a website for a different ip address I inserted this at the top of /etc/apache2/sites-enabled/website.file

Listen *:80
Listen 1.2.3.4:80

Fixed now and thanks all

---

