---
title: "[SOLVED] Apache2 SSL Setup"
date: 2008-11-07
forum: Server Platforms
---

### Post by Dr Small on 2008-11-07
Greetings there,
I just installed apache2 (and the whole kit and kaboodle) for my server (I have previous ran XAMPP, so I am reading documentation on how to do this effectively).

So far, I have been unsuccessful at getting SSL to work for my host, so I'll go down the steps I have taken and hopefully you will be able to see what I have done wrong and help me out.

1) Installed Apache2, Php5, MySQL, etc. OpenSSL came with this, I do believe. But either way, I have it.

2) Enabled mod_ssl by running:
```
sudo a2enmod ssl
```

3) Copied /etc/apache2/sites-available/default to /etc/apache2/sites-available/https

4) Edited the 'https' site to read:
```
	SSLEngine On
	SSLCertificateFile /etc/ssl/certs/https.cert
	SSLCertificateKeyFile /etc/ssl/private/https.key

```
After DocumentRoot

5) I also changed "NameVirtualHost" and "VirtualHost" to read:
```
NameVirtualHost *:443
<VirtualHost *:443>
```

6) Created my ssl key, by running:
```
openssl genrsa -out https.key 1024
```

7) Created my CSR by running:
```
openssl req -new -key https.key -out https.csr
```

8) Created my certificate by running:
```
openssl x509 -req -days 365 -in https.csr -signkey https.key -out https.cert
```

9) Copied the key and the certificate to the appropriate directories:
```
sudo cp https.cert /etc/ssl/certs/https.cert
sudo cp https.key /etc/ssl/private/https.key
```

10) Restarted Apache2:
```
sudo /etc/init.d/apache2 force-reload
```


And this is where the problem begins.
I attempt to access the HTTPS site, and I get this Firefox Error:
```
Secure Connection Failed

An error occurred during a connection to mycroftserver.homelinux.org.

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)
```

Here is my error from /var/log/apache2/error.log:
```
[Fri Nov 07 13:08:38 2008] [notice] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c configured -- resuming normal operations
[Fri Nov 07 13:08:43 2008] [error] [client *ipaddress*] Invalid method in request \x16\x03\x01
[Fri Nov 07 17:38:32 2008] [error] [client *ipaddress*] Invalid method in request \x16\x03\x01

```


Any help?

---

### Post by windependence on 2008-11-08
> Your SSL website may fail to load and display the error 

Error code: ssl_error_rx_record_too_long

This usually means the implementation of SSL on your server is not correct. It can also be caused by the way Firefox interprets redirects to SSL enabled websites. The error is usually caused by a server side problem which the server administrator will need to investigate.

Below are some things we recommend trying.

- Ensure that port 443 is open and enabled on your server. This is the standard port for https communications.
 
- If using Apache2 check that you are using port 443 for SSL. This can be done by setting the ports.conf file as follows
 
&#8212; clip &#8212;
Listen 80
Listen 443 https
&#8212; clip &#8212; 

- Make sure you do not have more than one SSL certificate sharing the same IP. Please ensure that all SSL certificates utilise their own dedicated IP.

- If using Apache2 check your vhost config. Some users have reported changing <VirtualHost> to _default_ resolved the error.

Also, is your port 443 forwarded to the server? I know, sounds stupid but hey I have to ask.

Also try this thread:

[http://forums.mozillazine.org/viewtopic.php?t=509553](http://forums.mozillazine.org/viewtopic.php?t=509553)

-Tim

---

### Post by Dr Small on 2008-11-08
> **windependence said:**
> Also, is your port 443 forwarded to the server? I know, sounds stupid but hey I have to ask.

Also try this thread:

[http://forums.mozillazine.org/viewtopic.php?t=509553](http://forums.mozillazine.org/viewtopic.php?t=509553)

-Tim
Thanks for your reply.
Yes, port 443 is forwarded to the server's IP address (192.168.0.70) from the router. I just nmapped my external IP, and it shows port 443 open.

I forgot to mention that I had edited /etc/apache2/ports.conf and added "Listen 443" to the end of the file, but I just tried "Listen 443 https", restarted apache2, and it didn't seem to have an effect on it.

Here is an exact copy of my "https" site in sites-available:
```
<VirtualHost localhost:433>
	ServerAdmin drsmall@mycroftserver.homelinux.org
	DocumentRoot /var/www/mycroft/

	SSLEngine On
	SSLCertificateFile /etc/ssl/certs/https.cert
	SSLCertificateKeyFile /etc/ssl/private/https.key


	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/mycroft/>
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
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

</VirtualHost>
```

I only have one SSL certificate, so that can't be the problem. If you see any mistakes I have made, please let me know.

Dr Small

---

### Post by oddeirik on 2008-11-08
Have you enabled the virtual host site?

I got the same errors trying to use the default-ssl site.

After a lot of cursing, reading docs and editing configuration files, all it took was this:

```
sudo a2ensite default-ssl
sudo /etc/init.d/apache2 reload
```

(Which in your case would be "http" instead of "default-ssl" I guess :)

---

### Post by Dr Small on 2008-11-08
> **oddeirik said:**
> Have you enabled the virtual host site?

I got the same errors trying to use the default-ssl site.

After a lot of cursing, reading docs and editing configuration files, all it took was this:

```
sudo a2ensite default-ssl
sudo /etc/init.d/apache2 reload
```

(Which in your case would be "http" instead of "default-ssl" I guess :)
Yes, the site has been enabled, and apache2 restarted.
Here is a question for you though. Do the key or certificate files need to have certain permissions in order for mod_ssl to use them correctly? I never changed any permissions, so that's why I ask.

---

### Post by Dr Small on 2008-11-09
I finally solved it... This just proves how dyslexic I am. In the VirtualHost container, I had:
```
localhost:433
```

Just look at that a second. Now you should begin to realize why it wasn't working. I looked at that and thought, "Hey... wait a second!". Sure enough. I had "433" instead of "443".

Problem Resolved.
My SSL Connections now work correctly :)

---

