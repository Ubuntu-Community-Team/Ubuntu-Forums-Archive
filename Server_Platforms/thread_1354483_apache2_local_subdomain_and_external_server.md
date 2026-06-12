---
title: "apache2 local subdomain and external server"
date: 2009-12-13
forum: Server Platforms
---

### Post by rekahsoft on 2009-12-13
Hi all, I am looking to host a pos system internally on my LAN but also want to host a website; both on different ports. My external ip is updated by ddns by my roughter running dd-wrt (to host: rekahsoft.homelinux.org). I want to accept connections on port 80 for this site and then have a pos system accessible over my network on port 8080 (i have dhcp reserves on my roughter for my server so it has static ip). What would my /etc/apache2/httpd.conf look like? This was what i was trying but it didn't seem to work :( ```
Listen 80
Listen 8080

NameVirtualHost localhost:80
NameVirtualHost localhost:8080

<VirtualHost localhost:80>
     ServerName rekahsoft.homelinux.org
     DocumentRoot /var/www
</VirtualHost>

<VirtualHost localhost:8080>
     ServerName pos.rekahsoft.local
     DocumentRoot /var/www/pos
</VirtualHost>
``` Thanks everyone :)

---

### Post by HighCommander540 on 2009-12-13
> **rekahsoft said:**
> Hi all, I am looking to host a pos system internally on my LAN but also want to host a website; both on different ports. My external ip is updated by ddns by my roughter running dd-wrt (to host: rekahsoft.homelinux.org). I want to accept connections on port 80 for this site and then have a pos system accessible over my network on port 8080 (i have dhcp reserves on my roughter for my server so it has static ip). What would my /etc/apache2/httpd.conf look like? This was what i was trying but it didn't seem to work :( ```
Listen 80
Listen 8080

NameVirtualHost localhost:80
NameVirtualHost localhost:8080

<VirtualHost localhost:80>
     ServerName rekahsoft.homelinux.org
     DocumentRoot /var/www
</VirtualHost>

<VirtualHost localhost:8080>
     ServerName pos.rekahsoft.local
     DocumentRoot /var/www/pos
</VirtualHost>
``` Thanks everyone :)

Its because you have it in the wrong, it has to be in order. You can't do it like that. Plus you don't need the "Listen *" statements if you are doing a virtual host.

It should look like this:

```

NameVirtualHost localhost:80

<VirtualHost localhost:80>
     ServerName rekahsoft.homelinux.org
     DocumentRoot /var/www
</VirtualHost>

NameVirtualHost localhost:8080

<VirtualHost localhost:8080>
     ServerName pos.rekahsoft.local
     DocumentRoot /var/www/pos
</VirtualHost>
```

Also you need at least one Directory statement. Like this:

```
<Directory /var/www/>
		Options FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>
```

---

### Post by rekahsoft on 2009-12-14
Alright so everything works except for accessing the LAN only sub-domain..(by going to pos.rekahsoft.local but i can access the restricted directory from rekahsoft.local/pos..here is my httpd.conf:```
NameVirtualHost localhost:80

<Directory /var/www>
     Options FollowSymLinks MultiViews
     AllowOverride None
     Order allow,deny
     Allow from all
</Directory>

<VirtualHost localhost:80>
     ServerName rekahsoft.homelinux.org
     DocumentRoot /var/www
</VirtualHost>

NameVirtualHost localhost:8080

<Directory /var/www/pos>
     Options FollowSymLinks MultiViews
     AllowOverride None
     Order deny,allow
     Allow from 192.168.1.100
     Deny from all
</Directory>

<VirtualHost localhost:8080>
     ServerName pos.rekahsoft.local
     DocumentRoot /var/www/pos
</VirtualHost>
```What do i need to do to make the local subdomain work (eg. pos.rekahsoft.local)

---

### Post by rekahsoft on 2009-12-14
Also how would i restrict the directory /var/ww/pos to the ip range 192.168.1.100-192.168.1.111?

---

### Post by rekahsoft on 2009-12-19
Anyone? :(

---

### Post by Lars Noodén on 2009-12-19
Maybe something like 

Allow 192.168.1.100/28

See
[http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow)

[http://www.pantz.org/software/tcpip/subnetchart.html](http://www.pantz.org/software/tcpip/subnetchart.html)

---

### Post by BkkBonanza on 2009-12-19
You need to add the local subdomain to your router DNS. DD-WRT runs dnsmasq for this so just add correct entry there. Rigth now your subdomain isn't getting resolved to the correct local IP. 

You won't need to block IPs for that subdomain - just make sure that your router does not forward for port 8080 so that public users cannot get to that port anyway.

Your order directive for pos doesn't make sense either. You should use,

Order allow,deny
Allow from 192.168.1.100/28

This gives you 4 bits open = 16 ip block from .96 to .112
If you need to really open only 100 to 111 then you may have to list them one by one as the notation only support block of binary multiples.

The "order allow,deny" means match allows first, denys second and deny by default. Your ip range will match and be allowed, all else denied.

---

