---
title: "Need help with apache2 default-ssl"
date: 2009-05-27
forum: Server Platforms
---

### Post by Jive Turkey on 2009-05-27
What I am trying to do is get the login and admin pages of a wordpress blog to use ssl, and seriously I dont mind if the whole thing uses ssl.  I am pretty sure my last hitch is in my default-ssl file.  I have been all over the wordpress docs and various other places, all of the guides assume you have ssl working correctly to begin with.

I implemented the steps in this guide to make a cert ([link]("http://beginlinux.com/blog/2009/01/ssl-on-ubuntu-810-apache2/")) and to enable ssl.  I know its for intrepid, but I'm using jaunty on a headless server, if that makes any difference.

It *almost* works, i get prompted to accept the certificate but then go to a "page not found" error when navigating to any of the admin functions.  Part of my problem might be that I have the default-ssl document root set to a sub folder as my regular default (port80) document root, I am not sure at all.  If someone can show me what I'm doing wrong and how to fix it I will be very happy.

default-ssl(commented lines stripped out)
```
<IfModule mod_ssl.c>
NameVirtualHost *:443
<VirtualHost *:443>
	ServerAdmin admin@localhost
	ServerName https://domainname.org/blag/wp-admin
	DocumentRoot /var/www/blag
	
	.......

</VirtualHost>
</IfModule>
```

*the sites-enabled "default" file is pristine I havent changed it at all since installing (LAMP option at OS install time 2 days ago)

It turns out I had some extra junk at the top where my httpd serverroot and my document root were in disagreemnt.  It now works as intended with http:// for the general public and logins and admin pages are https:// with a self signed cert.  Thanks if you you were looking to help :)

After some additional hardening measures I'll have some things to share in mi blag with you all.

---

