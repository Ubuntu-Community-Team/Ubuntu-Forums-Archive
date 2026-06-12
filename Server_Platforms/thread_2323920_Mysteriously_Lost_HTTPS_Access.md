---
title: "Mysteriously Lost HTTPS Access"
date: 2016-05-09
forum: Server Platforms
---

### Post by regnumimbriumx on 2016-05-09
Hi friends,

I have been running a 14.04 server since it was first released in April 2014. I run several web applications/sites, the most important of which is ownCloud. In summer 2015, after running fine for over a year, HTTPS mysteriously stopped working.

HTTP access continues to work. I have not changed ISPs or changed any router settings. I do not believe that I did anything immediately prior to HTTPS breaking to cause it. The server has been kept up to date with patches, but hasn't otherwise been used.

Can anyone recommend how to start troubleshooting this?

Thanks!

---

### Post by darkod on 2016-05-09
First I would check if apache is listening on port 443 at all. With something like:
```
sudo netstat -plunt | grep apache
```

Then check the .conf files in /etc/apache2/sites-available. Depending on your config, the 443 virtual host might be in your site .conf file, or it might be in the default file called default-ssl.conf.

You need to locate your 443 virtual host definition so you can check it out.

---

### Post by nerdtron on 2016-05-09
I'm guessing expired certificates? Or did you also updated the certificates and openssl packages as we have SSL vulnerabilities over the past few years. Also try restarting the apache2 package and look into the apache error log. If their a problem with https and SSL, it will surely be there.

---

### Post by regnumimbriumx on 2016-05-10
Thank you both for your help.


**darkon**, the result of the command was:


```
tcp6	0	0 :::443	:::*	LISTEN	3017/apache2
tcp6	0	0 :::80		:::*	LISTEN	3017/apache2

```

Within /etc/apache2/sites-available, I have multiple site config files. Within each of these files which requires https access, I have a virtual host definition. Here is my default-ssl.conf file:
```

<IfModule mod_ssl.c>


SSLStrictSNIVHostCheck off


<VirtualHost *:443>
		ServerAdmin mysite@mysite.com
		ServerName mysite.com
		DocumentRoot /var/www/


		LogLevel info ssl:warn
		ErrorLog ${APACHE_LOG_DIR}/error.log
		CustomLog ${APACHE_LOG_DIR}/access.log combined


		SSLEngine on


		SSLCertificateFile /home/mysite/cert-requests/CACert/mysite.com/mysite.com.crt
		SSLCertificateKeyFile /home/mysite/cert-requests/CACert/mysite.com/mysite.com.key
		SSLCertificateChainFile /home/mysite/cert-requests/CACert/CAcert_chain.pem


		#SSLCACertificatePath /etc/ssl/certs/
		#SSLCACertificateFile /home/mysite/cert-requests/CACert/CAcert_chain.pem


		# Self-signed (snakeoil) certificates:
		#SSLCertificateFile	/etc/apache2/ssl/apache.crt
		#SSLCertificateKeyFile /etc/apache2/ssl/apache.key


		<FilesMatch "\.(cgi|shtml|phtml|php)$">
				SSLOptions +StdEnvVars
		</FilesMatch>
		<Directory /usr/lib/cgi-bin>
				SSLOptions +StdEnvVars
		</Directory>


		BrowserMatch "MSIE [2-6]" \
				nokeepalive ssl-unclean-shutdown \
				downgrade-1.0 force-response-1.0
		BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
</VirtualHost>
</IfModule>

```

You'll notice that my SSLCACertificatPath and SSLCACertificateFile lines are commented out. I don't think that these are necessary for my certificates to work. Can you see anything else that might be wrong with my config?


Like I said, I also have multiple other .conf files for subdomains of the site. Those which require https access also have a <VirtualHost _default_:443> section. Is there any chance that those could be interferring?


**nerdtron**, I wondered about the certificates, too, but shouldn't that throw some kind of error? When I attempt to navigate to my site through https I only get ERR_CONNECTION_TIMED_OUT (after many seconds of waiting).


Also, shouldn't I be able to simply comment out my CSA-issued certificates and use my snakeoil certificate without problem? I tried that and it didn't work (although that certificate may be expired, too). Would expired certs really result in a connection timeout rather than something else?


I don't know what you mean by "did you also update the certificates", if you mean something different than getting new certificates. I, too, wondered about the SSL bugs (e.g. heartbleed) and whether something had gotten automatically disabled as a preventative measure. I've run "apt-get update" and "apt-get upgrade" and everything is (and has been) up to date. Is there some other way that I should be updating?


After issuing "sudo service apache2 restart", here are the results of /var/log/error.log:
```

[Tue May 10 10:46:08.705122 2016] [mpm_prefork:notice] [pid 4321] AH00169: caught SIGTERM, shutting down
[Tue May 10 10:46:09.711688 2016] [ssl:warn] [pid 4635] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.711996 2016] [ssl:warn] [pid 4635] AH01909: RSA certificate configured for survey.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.712498 2016] [ssl:warn] [pid 4635] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.712523 2016] [ssl:warn] [pid 4635] AH01909: RSA certificate configured for test.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.712950 2016] [ssl:warn] [pid 4635] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.713026 2016] [ssl:warn] [pid 4635] AH01909: RSA certificate configured for pma.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.713590 2016] [ssl:warn] [pid 4635] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.713599 2016] [ssl:warn] [pid 4635] AH01909: RSA certificate configured for news.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.716510 2016] [ssl:warn] [pid 4635] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.716532 2016] [ssl:warn] [pid 4635] AH01909: RSA certificate configured for critical.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.717607 2016] [ssl:warn] [pid 4635] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.717623 2016] [ssl:warn] [pid 4635] AH01909: RSA certificate configured for cherish.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.717828 2016] [ssl:warn] [pid 4635] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.717838 2016] [ssl:warn] [pid 4635] AH01909: RSA certificate configured for chat.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.717929 2016] [ssl:warn] [pid 4635] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Tue May 10 10:46:09.771968 2016] [ssl:warn] [pid 4636] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.772064 2016] [ssl:warn] [pid 4636] AH01909: RSA certificate configured for survey.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.772616 2016] [ssl:warn] [pid 4636] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.772625 2016] [ssl:warn] [pid 4636] AH01909: RSA certificate configured for test.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.773199 2016] [ssl:warn] [pid 4636] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.773208 2016] [ssl:warn] [pid 4636] AH01909: RSA certificate configured for pma.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.773774 2016] [ssl:warn] [pid 4636] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.773783 2016] [ssl:warn] [pid 4636] AH01909: RSA certificate configured for news.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.776918 2016] [ssl:warn] [pid 4636] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.776936 2016] [ssl:warn] [pid 4636] AH01909: RSA certificate configured for critical.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.777878 2016] [ssl:warn] [pid 4636] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.777901 2016] [ssl:warn] [pid 4636] AH01909: RSA certificate configured for cherish.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.778118 2016] [ssl:warn] [pid 4636] AH01906: RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)
[Tue May 10 10:46:09.778126 2016] [ssl:warn] [pid 4636] AH01909: RSA certificate configured for chat.mysite.com:443 does NOT include an ID which matches the server name
[Tue May 10 10:46:09.778239 2016] [ssl:warn] [pid 4636] AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
[Tue May 10 10:46:09.780326 2016] [mpm_prefork:notice] [pid 4636] AH00163: Apache/2.4.7 (Ubuntu) OpenSSL/1.0.1f configured -- resuming normal operations
[Tue May 10 10:46:09.780371 2016] [core:notice] [pid 4636] AH00094: Command line: '/usr/sbin/apache2'

```

The most serious warning appeared to be "Init: Name-based SSL virtual hosts...", which is why I added the "SSLStrictSNIVHostCheck off" option to my default-ssl.conf file. Does anything else appear off?


I should also mention that my ssl_access.log is completely blank and my ssl_access.log.1 has entries dating back to May 2015, which is probably the last time that ssl was working.


In my access.log.1 file, I am also seeing this repeated, apparently for each time that I try to securely access the website:


```
::1 - - [10/May/2016:09:10:42 -0500] "OPTIONS * HTTP/1.0" 200 110 "-" "Apache/2.4.7 (Ubuntu) OpenSSL/1.0.1f (internal dummy connection)"
```

Thanks again for your help!

---

### Post by darkod on 2016-05-10
I am no apache expert and I don't think I can help much, but I think this issue that showed up later (it worked and then it doesn't) might be related to apache being upgraded to 2.4. You said you have this 14.04 LTS server since 2014 but at that time it didn't come with apache 2.4 (if I'm not mistaken).

Try googling something like "ssl virtual hosts not working after upgrading to apache 2.4" and also I assume you have googled that Init: Name-based... error. That would be my first suspect too. It actually complains that name based ssl virtual hosts won't work, and you have exactly that.

---

### Post by darkod on 2016-05-10
Some investigation:
[https://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI](https://wiki.apache.org/httpd/NameBasedSSLVHostsWithSNI)
[http://serverfault.com/questions/644874/two-ssl-virtualhosts-on-same-ip-with-apache](http://serverfault.com/questions/644874/two-ssl-virtualhosts-on-same-ip-with-apache)

Don't forget you might need to adjust the .conf file. The piece of code in the first link does not look like a standard .conf file (for example you don't include Listen 443 in the .conf in sites-available).

But now that you know that multiple SSL sites should be used with something called SNI you can also google further...

---

