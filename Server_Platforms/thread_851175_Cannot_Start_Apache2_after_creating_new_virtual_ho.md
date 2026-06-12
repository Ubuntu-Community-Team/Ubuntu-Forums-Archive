---
title: "Cannot Start Apache2 after creating new virtual host?"
date: 2008-07-06
forum: Server Platforms
---

### Post by sil3nt on 2008-07-06
Hi Guy's
          I just installed a new virtual host and I can no longer restart/start apache2.

When I attempt to start I get :
```
* Starting web server apache2      [fail] 

```

A restart :
```
 * Restarting web server apache2 httpd (no pid file) not running

```

I don't want to do a physical reboot because I have a client working on one of my VM's.

Any ideas how I can get this up and running again?

Cheers :confused:**[B][B][B][B][B]**[/B][/B][/B][/B][/B]

---

### Post by sil3nt on 2008-07-06
For reference I am using Ubuntu Server 8.04.

Any help would be appreciated.

---

### Post by windependence on 2008-07-06
Something in your virtual host syntax is wrong. Can you post your config file?

Also try:

```
sudo /usr/sbin/apachectl -t 
```
which is a syntax check


-Tim

---

### Post by sil3nt on 2008-07-06
/etc/apache2/sites-enabled/

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
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

```

That syntax check wont work, wont recognize the command ie path is not available :(

---

### Post by sil3nt on 2008-07-06
I created the new virtual host using Webmin, so I am assuming that it would not be a syntax issue ?

---

### Post by windependence on 2008-07-06
Check your log files in /var/log/messages and /var/log/httpd. Let me know if you see anything funny.

-Tim

---

### Post by sil3nt on 2008-07-06
> **windependence said:**
> Check your log files in /var/log/messages and /var/log/httpd. Let me know if you see anything funny.

-Tim

Nothing in /var/log/messages and /var/log/httpd does not exist

---

### Post by windependence on 2008-07-06
Is there an apache log in /var/log?

-Tim

---

### Post by sil3nt on 2008-07-06
yeah an error log and access log neither show anything interesting other than failing to fine a SSL cert

---

### Post by windependence on 2008-07-07
Can you comment out the virtual host section and try to start apache?

-Tim

---

### Post by sil3nt on 2008-07-07
Tried that didnt work, maybe I should try a physical reboot :(

---

### Post by windependence on 2008-07-07
On a Linux box you should never have to reboot for something like this. 

You're sure there are no log entries in any of the logs when you try to start apache? What is the command you are using to start it?

-Tim

---

### Post by sil3nt on 2008-07-07
> **windependence said:**
> On a Linux box you should never have to reboot for something like this. 

You're sure there are no log entries in any of the logs when you try to start apache? What is the command you are using to start it?

-Tim

Thanks Tim I appreciate your time, I was using :
```
 sudo /etc/init.d/apache2 start

```

I checked the /var/log/apache2/error.log and it is complaining of a SSL cert which it cant find```
[Mon Jul 07 13:16:19 2008] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]

```

I changed the config for the virtual host not to use SSL and apache now starts ok

```
* Starting web server apache2             [ OK ] 

```


Again thanks for your time.

---

### Post by windependence on 2008-07-07
> [B]Why can't I use SSL with name-based/non-IP-based virtual hosts?
[/B]
The reason is very technical, and a somewhat "chicken and egg" problem. The SSL protocol layer stays below the HTTP protocol layer and encapsulates HTTP. When an SSL connection (HTTPS) is established Apache/mod_ssl has to negotiate the SSL protocol parameters with the client. For this, mod_ssl has to consult the configuration of the virtual server (for instance it has to look for the cipher suite, the server certificate, etc.). But in order to go to the correct virtual server Apache has to know the Host HTTP header field. To do this, the HTTP request header has to be read. This cannot be done before the SSL handshake is finished, but the information is needed in order to complete the SSL handshake phase. Bingo!

**Why is it not possible to use Name-Based Virtual Hosting to identify different SSL virtual hosts?**

Name-Based Virtual Hosting is a very popular method of identifying different virtual hosts. It allows you to use the same IP address and the same port number for many different sites. When people move on to SSL, it seems natural to assume that the same method can be used to have lots of different SSL virtual hosts on the same server.

It comes as rather a shock to learn that it is impossible.

The reason is that the SSL protocol is a separate layer which encapsulates the HTTP protocol. So the SSL session is a separate transaction, that takes place before the HTTP session has begun. The server receives an SSL request on IP address X and port Y (usually 443). Since the SSL request does not contain any Host: field, the server has no way to decide which SSL virtual host to use. Usually, it will just use the first one it finds, which matches the port and IP address specified.

You can, of course, use Name-Based Virtual Hosting to identify many non-SSL virtual hosts (all on port 80, for example) and then have a single SSL virtual host (on port 443). But if you do this, you must make sure to put the non-SSL port number on the NameVirtualHost directive, e.g.

NameVirtualHost 192.168.1.1:80

Other workaround solutions include:

Using separate IP addresses for different SSL hosts. Using different port numbers for different SSL hosts.


[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html)

-Tim

---

