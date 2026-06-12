---
title: "updating from Ubuntu Server 11.1 to 12.04, no more https?"
date: 2012-07-16
forum: Server Platforms
---

### Post by Redsting on 2012-07-16
Hi,

I'm new to the forums but have been using Ubuntu for over a year now. I recently updated to Ubuntu server from 11.1 to 12.04. After doing so I was relieved that everything still worked. Only later did I realize that https was no longer working. When I attempt to connect it times out and no errors are thrown in the apache2 logs. It was working before the update.

I'm not sure what has changed since, but I have gone through a few steps to try and figure out the problem but have not found anything yet.

Here's what I've tried.

```
netstat -lp | grep apache2
tcp        0      0 *:http     *:*    LISTEN      7201/apache2
tcp        0      0 *:https    *:*    LISTEN      7201/apache2
```

```
openssl s_client -connect www.MYDOMAINNAME.com:443
connect: Connection timed out
connect:errno=110
```

```
s_client -connect localhost:443
( SSL certificate data as expected )
```

```
# default-ssl
<VirtualHost *:443>
	ServerName MYDOMAINNAME.com
	ServerAlias www.MYDOMAINNAME.com
	ServerAdmin support@MYDOMAINNAME.com
	DocumentRoot /var/www
	
	ErrorLog ${APACHE_LOG_DIR}/error.log
	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn
	CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined
	
	#   SSL Engine Switch:
	#   Enable/Disable SSL for this virtual host.
	SSLEngine on
	SSLProtocol -all +TLSv1 +SSLv3
	SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM
	SSLCertificateFile	/root/ssl/MYDOMAINNAME.com.crt
	SSLCertificateKeyFile	/root/ssl/MYDOMAINNAME.com.key
	SSLCACertificateFile	/root/ssl/MYDOMAINNAME.com.csr
	
	BrowserMatch "MSIE [2-6]" \
		nokeepalive ssl-unclean-shutdown \
		downgrade-1.0 force-response-1.0
	# MSIE 7 and newer should be able to use keepalive
	BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>
```

```
# ports.conf
NameVirtualHost *:80
Listen 80
<IfModule mod_ssl.c>
    Listen 443
</IfModule>
<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```

```
a2ensite default-ssl
Site default-ssl already enabled
a2enmod ssl
Module ssl already enabled
```

```
Apache/2.2.22
Ubuntu 12.04 LTS
```

Any suggestions would be appreciated.

Thanks,
~Redsting

[edit notes: Forgot to add that I double checked mod_ssl and default-ssl were enabled]

---

### Post by AnrDaemon on 2012-07-16
Check 
apache2ctl -MS

I'm pretty sure you're missing
NameVirtualHost *:443

in block

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

thus Apache HTTPd don't see your SSL host.

Would also suggest you to use _default_:443 instead of *:443 for host definition. But that's a nitpick.

---

### Post by Redsting on 2012-07-16
I checked apache2ctl and it appears to be correct. *:443 and *:80 are both valid, and all necessary modules are loaded.

I added NameVirtualHost *:443 and modified to _default_ in the definition, but no avail.

Thank you for the suggestions.

---

### Post by Redsting on 2012-07-16
Found the solution, but I'm not sure how it was working before if this is the case.

The router had every port necessary open except 443, which begs the question how it could have worked before?
I know it was properly encrypting the connection before, but I'm not sure how connections could have been allowed in this case.

---

