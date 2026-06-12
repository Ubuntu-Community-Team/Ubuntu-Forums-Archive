---
title: "Help in sourcing a vhost/Port (?) problem"
date: 2011-05-24
forum: Server Platforms
---

### Post by cje on 2011-05-24
I really need some guidance in finding the source of the following problem;

1) I set up a site - my.com - (just a wallpaper for this test) in site-available with port 85
2) enable it with a2ensite
3) put in listen 85 in ports.conf
4) restart apache
5) open port 85 on my ISP router

When visiting the 1.23.456.789:85 from the outside I only get a blank white page.

When testing the same page 192.168.10.30:85 on my LAN the page display fine. 

So, when browsing from the outside the router direct my request to my server (and vhost to the correct folder). But my server doesn't send anything else than a blank  page back....?

Can anyone help me with this problem?

This is my interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet static
address 192.168.10.20
netmask 255.255.255.0
gateway 192.168.10.1

# Virtual networks interface

auto eth0:0
iface eth0:0 inet static
address 192.168.10.30
netmask 255.255.255.0
gateway 192.168.10.1

```

This is my virtual host
```

<VirtualHost 192.168.10.30:85>

	ServerAdmin my@mail.com

	ServerName www.my.com
	ServerAlias *.my.com

	DocumentRoot /var/www2/my/

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www2/my/>
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

This is my ISP router setup: 
```

TCP
external port from 85 to 85
internal port from 85 to 85
Internal IP 192.168.10.30

```

Pls note; services running (on primary network) w/o port routing is running just fine. Service running on primary network w/ port routing have the same problem

---

### Post by cje on 2011-05-26
Anyone....?

---

### Post by cje on 2011-05-29
I just found that Bind9 fail to start.... could this be the issue?
Anyone have any comments on this?

In named.conf I've defined a zone to home.lan

```

zone "home.lan" {
	type master;
	file "/etc/bind/db.home.lan";

zone "10.168.192.in-addr.arpa" {
	type master;
        notify no;
	file "/etc/bind/db.192";

```

I find that a haven't set up a secondary master. Is that a problem?

This is my db.home.lan
```

$TTL	604800
@	IN	SOA	ns.home.lan. root.home.lan. (
		     2009031220		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.home.lan.
@	IN	A	192.168.10.30
ns	IN	A	192.168.10.30
;
www	IN 	CNAME 	localhost.
www	IN 	CNAME 	mydomain.com.

```

And this is my db.192
```

$TTL	604800
@	IN	SOA	ns.home.lan. root.home.lan. (
		     2009031219		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800		; Negative Cache TTL
			)
@	IN	NS	ns.
30	IN	PTR	ns.home.lan

```

Thanks for any suggstions

---

