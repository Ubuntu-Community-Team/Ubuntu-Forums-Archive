---
title: "VirtualHost problem"
date: 2009-07-02
forum: Server Platforms
---

### Post by ryy705 on 2009-07-02
Hello,

I recently Installed Apache on my computer to learn about it.

But I seemed to have screwed it up in no time.

When I restart the server I'm getting the following error message:
```
ryy@ryy:~$ sudo apache2ctl restart
sudo: unable to resolve host ryy
apache2: apr_sockaddr_info_get() failed for ryy
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Thu Jul 02 11:28:31 2009] [warn] NameVirtualHost *:80 has no VirtualHos
```

I have successfully moved the webroot to a directory under my home directory.  I have disabled default file and enabled a new file called Sites.

I am pasting the content of Sites files below:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/ryy/Sites/
	<Directory /home/ryy/Sites/>
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/ryy/Sites/>
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

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

Here is the content of /etc/hosts
```
127.0.0.1 ryy.com localhost
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

I google the error messages and found a solution [here]("http://www.wallpaperama.com/forums/starting-httpd-httpd-apr-sockaddr-info-get-failed-for-t5821.html")
But When I do sudo echo ryy.com > /etc/hostname
I get a bash: /etc/hostname: Permission denied
error.
I thought you could do anything with sudo.

I would like to make many more customizations to apache.  But I am scared to proceed without fixing the errors.  I would appreciate any help with this.

---

### Post by mbeach on 2009-07-02
so what happens when you browse in your browser to ryy.com on this machine?

something to read over:
/usr/share/doc/apache2/README.Debian.gz
particularly the part about the NameVirtualHost warning.

also, is there any particular reason you are not using:
sudo /etc/init.d/apache2 reload
or
sudo /etc/init.d/apache2 restart
instead of sudo apache2ctl restart

---

