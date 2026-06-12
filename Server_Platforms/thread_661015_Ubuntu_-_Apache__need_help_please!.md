---
title: "Ubuntu - Apache  need help please!"
date: 2008-01-07
forum: Server Platforms
---

### Post by Salcka on 2008-01-07
Please, help me!
Four days I  fighting with apache and cannot find a solution. I tried all what I find on forums and tutorials. :(

Im trying to host a website using Apache. Everything is working fine, but only local. I see my side, but it cannot be see from other.

I have fix IP.
I do not have router.
Port 80 is open. (I try other ports and it is the same.)
Apache listen port 80.
I set access to web directory (750).
My default site available:

<VirtualHost 82.149.19.211:80>
	ServerAdmin salcka@localhost
	ServerName salcka.org
	DocumentRoot /var/www/salcka
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/salcka/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
	ErrorLog /var/log/apache2/error.log
	LogLevel warn
	CustomLog /var/log/apache2/access.log combined
	ServerSignature On
</VirtualHost>

---

### Post by foolsh on 2008-01-07
you're right I cant see [http://82.149.19.211](http://82.149.19.211) either, but I can ping your address all day at 0% packet loss. hmm?
Are you behind a router?
have installed firestarter or any other iptables frontend?

---

### Post by Salcka on 2008-01-07
No, I do not have a ruoter.
I install only Apache and Webmin. And you can see webmin page [https://salcka.org:10000](https://salcka.org:10000)

---

### Post by cdenley on 2008-01-07
You can check to see if you have firewall rules by running "sudo iptables -L". Also, post the output of:
```

cat /etc/apache2/ports.conf
netstat -an|grep :80

```

---

### Post by Salcka on 2008-01-07
# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


# cat /etc/apache2/ports.conf
Listen *:80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>


# netstat -an|grep :80
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN

---

### Post by cdenley on 2008-01-07
So you tried changing it to a different port, like 8000, you have no router or firewall, and your server can see the website at [http://localhost/](http://localhost/)? If that is correct, then I think your ISP must be blocking it, but then I don't know why your webmin page would work, though.

---

### Post by Salcka on 2008-01-07
Yes, I try other ports like 8080.

I can see webside at [http://82.149.19.211/](http://82.149.19.211/) or [http://www.salcka.org/](http://www.salcka.org/)

Edit:
Now I try port 9999 and it is work. So, you probably are right: ISP must be blocking port 80
Thank you!

---

