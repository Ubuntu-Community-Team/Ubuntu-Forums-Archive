---
title: "apache virtual host by ip address"
date: 2008-10-30
forum: Server Platforms
---

### Post by tgatewood on 2008-10-30
Hi! I'm having trouble figuring this one out.

I run a hotspot for a hotel, and we want to be able to serve a different webpage for users inside the network.

For instance,
10.2.1.0/24 would be for the guests 
192.168.100/22 is for office use 

Is it possible when someone from 10.2.1.0/24 accesses [www.mysite.com](www.mysite.com) it serves up a page different from someone accessing on the office network or a public IP?

Any help is greatly appreciated!!!

---

### Post by alienprdkt on 2008-10-30
this is the httpd.conf file:

NameVirtualHost *:80

<VirtualHost 192.168.100:80>
   ServerName [http://site1.com]("http://site1.com/")
   ServerAdmin webmaster@localhost
   DocumentRoot "/var/www/site1"
</VirtualHost>

<VirtualHost 10.2.1.0:80>
   ServerName [http://site2.com]("http://site2.com/")
   ServerAdmin webmaster@localhost
   DocumentRoot "/var/www/site2"
</VirtualHost>

I believe that is how you do it.

---

### Post by tgatewood on 2008-10-30
I'll give it a go a little later.  The only difference is that the domain will remain the same, [www.mysite.com](www.mysite.com) for both.  Also, the 192.168.100 network will be the same site as for external guests.  Maybe I just need to add:

<VirtualHost 10.2.1.0:80>
ServerName [http://site2.com](http://site2.com)
ServerAdmin webmaster@localhost
DocumentRoot "/var/www/site2"
</VirtualHost>

---

### Post by alienprdkt on 2008-10-30
> **tgatewood said:**
> I'll give it a go a little later.  The only difference is that the domain will remain the same, [www.mysite.com]("http://www.mysite.com") for both.  Also, the 192.168.100 network will be the same site as for external guests.  Maybe I just need to add:

<VirtualHost 10.2.1.0:80>
ServerName [http://site2.com](http://site2.com)
ServerAdmin webmaster@localhost
DocumentRoot "/var/www/site2"
</VirtualHost>

don't know if they can both have the same domain name (you can try)... hmmm you can make it [www.guests.mysite.com](www.guests.mysite.com) though

---

### Post by tgatewood on 2008-10-30
The idea is that the user knows the address [www.mysite.com](www.mysite.com).  It's much easier to tell them that, than [www.guests.mysite.com](www.guests.mysite.com) or what have you.  Also, they would be more likely to find [www.mysite.com](www.mysite.com) on their own.

I might just try setting up another web server and using a static dns entry on the guest-side DNS server.

---

### Post by Thirtysixway on 2008-10-30
You could use something like PHP to serve different content based on the IP address of the user.

---

### Post by lykwydchykyn on 2008-10-30
How are you going to determine which IP the domain resolves to?

Once you set up virtual hosts via IP, it's really up to DNS from that point to send clients to the right IP.

---

### Post by alienprdkt on 2008-10-30
Agreed and I don't think you can give 2 ip addresses the same domain name? Think it conflicts.

---

### Post by lykwydchykyn on 2008-10-30
Actually, you can give two IP's to the same host/domain name, at least with BIND.  It just alternates which one it gives back, as sort of a simple load-balancing arrangment.

---

### Post by alienprdkt on 2008-10-30
your right I did read that, thanks for the correction

goes along with primary and secondary dns right?

think I also read that its a guessing game which ip it loads from? (maybe wrong on that too though ;)

---

