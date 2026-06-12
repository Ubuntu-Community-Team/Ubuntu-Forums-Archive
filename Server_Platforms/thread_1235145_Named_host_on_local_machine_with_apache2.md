---
title: "Named host on local machine with apache2"
date: 2009-08-08
forum: Server Platforms
---

### Post by tomkane1 on 2009-08-08
I am trying to create an Apache2-based web site using a named site and link to the website from the same computer that the server is running on. After I do that, I will try to do the same with a dynamic dns service.

I can manipulate my web page through localhosts and 127.0.0.1. And I am writing this while connected through FireFox loaded on my server (with the gnome GUI).  

My problem is in using the host name in my browser. I am trying this with a dummy name: [www.sfaq.com](www.sfaq.com).

Here is my hosts file:

```
127.0.0.1	localhost
192.168.1.110	sfaq.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

The apache2.conf file is unchanged as per the original installation. Likewise, the default file in sites-available directory is unchanged. 

The httpd.conf file was changed automatically when I installed Perl and mod_perl.

The only other thing that I have been changing has been the file that I've created in the /etc/apache2/sites-available directory, namely, the file named sfaq:

```

<VirtualHost *:80>

	ServerName	sfaq.com
	ServerAlias	www.sfaq.com
	ServerAdmin 	webmaster@sfaq.com
	DocumentRoot 	"/srv/www/sfaq"

	<Directory 	"/srv/www/sfaq">
		Options 	Indexes FollowSymLinks MultiViews
		AllowOverride 	None
		Order 		allow,deny
		allow 		from all
	</Directory>

	ScriptAlias 	/cgi-bin/ 	/srv/www/sfaq/cgi-bin/
	<Directory 	"/srv/www/sfaq/cgi-bin">
		AllowOverride 	None
		Options 	+ExecCGI -Includes
		Order 		allow,deny
		Allow 		from all
	</Directory>

	ErrorLog /srv/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

</VirtualHost>
```

When I restart/reload apache2 with this file in place, I get an OK status. But when I type the URL [www.sfaq.com](www.sfaq.com) in the address line in my browswer, all I get is a parking server address instead.

When I look through the Apache website at the link for VirtualHost Examples I find information about what to put into httpd.conf, but when I try it, it usually causes apache2 to fail. (I've been trying so many combinations that my head is spinning.)

I am definitely missing something, and I'm sure it is probably minor, but I haven't hit the right combination yet. If anyone can spot something, I will be very appreciative.

Thanks.

---

### Post by tomkane1 on 2009-08-09
I finally figured out the problem. It seems that I was trying to use the host name sfaq.com in the URL address incorrectly, namely, I had defined it in the hosts file as sfaq.com but was using the prefix 'www.' when I used it in the address field. I don't know where I came up with the idea that I needed the www. at the beginning but that was the problem. When I entered just the 'sfaq.com' string as the address, it loaded just like expected.

Then I added the line for the [www.sfaq.com](www.sfaq.com) to my hosts file and I was then able to reach the 'www.sfaq.com' address just as well.

My hosts file now:

```
127.0.0.1	localhost
192.168.1.110	sfaq.com
192.168.1.110	www.sfaq.com
```

I'm too far along as a developer to have these difficulties, but it is not always clear as to which parts of configuration items are relative addresses and which are absolute addresses. :confused: Consequently, the 'www' part is still not quite clear. 

But I'll never give up.

---

