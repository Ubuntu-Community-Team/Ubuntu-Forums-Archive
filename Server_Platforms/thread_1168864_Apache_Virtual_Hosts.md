---
title: "Apache Virtual Hosts"
date: 2009-05-24
forum: Server Platforms
---

### Post by X96 Design on 2009-05-24
Hi,

I have a working network set up with Apache, I have multiple sub-domains to one IP address. I noticed just now, that though they all work on my computer, only the default address will work on other computers in my network.

For example, I have *http://files.testserver/* and *http://testserver/*. Only *http://tesetserver* will load, I get an "address not found" for [I]files.testserver.

[/I]Everything works perfectly on my local computer (the one with Apache), but other computers have trouble loading the subdomains.

Any advice or help would be appreciated.

BTW - I use Rapache to edit/create vhosts.

thanks
X96

---

### Post by Girl™ on 2009-05-24
Could you post your apache config?

---

### Post by X96 Design on 2009-05-24
Here's what the httpd.conf file says:
> ErrorDocument 404 /404.php

ServerName 127.0.1.1 
 
<VirtualHost *:80> 
ServerName testserver
ServerAlias testerver *.testerver
DocumentRoot /var/www/testserver
</VirtualHost> 
 
<VirtualHost *:80> 
ServerName files.testserver
DocumentRoot /var/www/files.testserver
</VirtualHost>

Cheers,
X

---

### Post by X96 Design on 2009-05-30
Can anyone throw in a suggestion or solution?

Thanks
X

---

### Post by cariboo on 2009-05-30
You might get some better results here.

---

### Post by roman_platonov on 2009-05-30
> **X96 Design said:**
> Hi,

For example, I have *[http://files.testserver/](http://files.testserver/)* and *[http://testserver/](http://testserver/)*. Only *[http://tesetserver](http://tesetserver)* will load, I get an "address not found" for [I]files.testserver.

[/I]

check dns maybe other stations on you network can't resolve *files.testserver*

---

### Post by X96 Design on 2009-08-21
How do I check my DNS? I found out that if I visit my IP address, the main Virtualhost will load, but I only have 1 IP, so IP-based Virtualhosts are out of the question...

Thanks,
X96

---

### Post by windependence on 2009-08-22
I doubt this is a DNS issue. The problem is the weird way Apache2 is configured in Ubuntu. The vhosts are configured in /etc/apache2/sites-available. The httpd.conf file that you and I love is deprecated and not used at all. Here is a great article on setting this all up.

[http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting](http://beginlinux.com/server_training/web-server/994-ubuntu-804-named-based-hosting)

-Tim

---

### Post by AlexDudko on 2009-08-22
> **X96 Design said:**
> How do I check my DNS?
How do other computers in your network "know" that [http://testserver](http://testserver) name belongs to your server's ip address?

---

### Post by X96 Design on 2009-08-22
I edited my /etc/hosts file so that my IP is beside "testserver", and I can access that server, but if I put the same IP address beside "testserver2", it goes to "testserver".

In the article Tim Posted, I quote:
> [...][FONT=Arial, sans-serif][SIZE=2]this technique may or may not work on your organization's LAN[/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]

Could it be my LAN?

Or, could it be that my "server" is also my personal computer? Would it make any difference if I used a dedicated box with Ubuntu server edition on it?

I also use Rapache for all my VHost stuff... Could this be a factor?

Thanks,
X96
[/SIZE][/FONT]

---

### Post by AlexDudko on 2009-08-23
Check your apache configs. The problem must be in configuration.
Try to use > /etc/apache2/sites-enabled/000-default  for configuring virtual hosts.
Just add your virtual hosts there in this way:
```
<VirtualHost testserver:80>
ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/testserver
	<Directory />
		Options FollowSymLinks
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>
<VirtualHost testserver2:80>
ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/testserver2
	<Directory />
		Options FollowSymLinks
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>
```
restart server and test how it works.

---

### Post by windependence on 2009-08-23
I don't think it's your LAN. Also, it doesn't matter if it's your personal computer or not. How is your network set up? Is the "server" a different PC or is this all being done on one box? Also, what is Rapache? After I have an idea how you are set up we can work on the problem.

-Tim

---

### Post by X96 Design on 2010-06-13
Forget everything I said I had used and/or configured - I have a completely new setup now (sorry)... My main PC is an iMac and I have a dedicated box running Ubuntu Server 10.04.

My modem assigns each computer on the network a dynamic IP. This IP changes frequently and gets annoying. So I can access my server from [FONT=Courier New]192.168.1.68[/FONT], but I'd like to be able to access it from [FONT=Courier New]alex-server.lan[/FONT].

Here's my Virutalhost code now:
```

ServerName alex-server.lan
NameVirtualHost alex-server.lan:80
<VirtualHost alex-server.lan:80>
        ServerName alex-server.lan
        ServerAlias www.alex-server.lan
        ServerAdmin alex@x96design.com
        DocumentRoot /var/www
</VirtualHost>

```And my httpd.conf file says:
```
ServerName alex-server.lan
NameVirtualHost *:80
```My[FONT=Courier New] /etc/hosts[/FONT] file has an entry assigning [FONT=Courier New]alex-server.lan[/FONT] to [FONT=Courier New]127.0.0.1[/FONT].

I've dumped all software and am now writing these config files by hand in nano.

Whenever I restart Apache, it tells me that [FONT=Courier New]NameVirtualHost *:80 has to VirtualHosts[/FONT].

Hopefully I've clarified enough... Sorry for the delay in response, I've been very busy...

Thanks,
Alex

---

### Post by Ryan Dwyer on 2010-06-13
You can give yourself a static private address by changing your network config on the server. Don't use DHCP. Set a manual address that is outside the range your DHCP server uses to minimise conflicts.

Change this in your default vhost:
ServerName alex-server.lan
NameVirtualHost alex-server.lan:80
<VirtualHost alex-server.lan:80>

To this:
<VirtualHost *:80>

Remove the NameVirtualHost line from your http.conf.

Your client machines (iMac) probably won't know what IP address alex-server.lan is supposed to resolve to. You can either configure this manually on all machines using their hosts files, or set up a local DNS server.

---

### Post by X96 Design on 2010-06-13
Awesome! Thanks so much!

I got the name-based to work... Tried the DNS server but couldn't get it to work. Since it's only 5 computers on the network, I'll edit their hosts files manually.

Thanks,
Alex

---

