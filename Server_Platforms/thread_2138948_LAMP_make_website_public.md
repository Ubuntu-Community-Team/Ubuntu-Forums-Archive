---
title: "LAMP make website public"
date: 2013-04-25
forum: Server Platforms
---

### Post by drakoumel on 2013-04-25
Hello all,
As the title describes i am trying to make my website public from a LAMP setup.
I trying but i am failing... so if you could give that extra push it would be much appreciated!
My setup:
-VMWARE 9.0.2 
-Ubuntu server 12.10
-apache2 (2.2 i think?)
-php5
-mysql
-phpmyadmin

Standard stuff i guess. So where am i?
My website is accessible from LAN connections in [http://192.168.1.147/test.php](http://192.168.1.147/test.php) where i have the phpinfo() function and in [http://192.168.1.147/](http://192.168.1.147/) i have the it works!

I set up port forwarding on the router on port :80 with the VM's local ip address checked if the port is on (OK).

Now i was thinking next step is to change the ports.conf file?
FROM:
> 
NameVirtualHost *:80
List *:80
<ifModule mod_ssl.c>
Listen 443
</ifModule>

<ifModule mod_gnutls.c>
listen 443
</ifModule>


TO:
> 
NameVirtualHost My.IP.Add.ress:80
List My.IP.Add.ress:80
<ifModule mod_ssl.c>
Listen 443
</ifModule>

<ifModule mod_gnutls.c>
listen 443
</ifModule>


but then i should change the virtual host file of the /etc/apache2/sites-available/default to use the same IP and port right? thats when i get the following (after i restart or try to restart apache)

[Date] [error] (EAI 2) name or service unknown: failed to resolve server name for (check dns) or etc..
And then (99)Cannot assign requested address: make_sock: could not bind to address 1.2.3.4 no listening sockets available shutting down.

I have put my internet ip address not the local ip.

Thats my stop :P
Thanks even for reading!

---

### Post by darkod on 2013-04-25
No, leave the ports.conf file as it is. The router port forwarding will take care to forward all traffic incoming on port 80 of the public IP to the server private IP.

Your ISP might be blocking port 80 to prevent running services. Otherwise, if you browse the public IP you should see the It Works page.

Go to a website that checks ports from any computer in your network, and check the port 80. Something like: [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

See if it says your port 80 is open.

---

### Post by drakoumel on 2013-04-25
the port is open as the site suggests.
i changed the port.conf to *:80 and the /etc/apache2/sites-available/default --> to <VirtualHost *:80>
but when i access my ipaddress:80 i get "Server requires username and password. the server says level_15_access

P.S ofc restarted apache

---

### Post by darkod on 2013-04-25
Something got messed up. Do you have a VM image with the basic setup? You can simply restore it and not waste time repairing this.

Apache was working fine and the site was opening from the LAN. You need to reach that point again.

---

### Post by drakoumel on 2013-04-25
i can still reach it in a LAN using [http://192.168.1.147/](http://192.168.1.147/) but when i try with 62.254.165.178 i get the access errors

---

### Post by CharlesA on 2013-04-25
The router is probably forwarding it's web admin page to the internet. That would explain the username/password prompt.

---

### Post by drakoumel on 2013-04-25
if thats the case any ideas? also if it would point to its admin page wouldn't the same username/pass i use for 192.168.1.1 be valid? (i tried got a 401)

---

### Post by CharlesA on 2013-04-25
> **drakoumel said:**
> if thats the case any ideas? also if it would point to its admin page wouldn't the same username/pass i use for 192.168.1.1 be valid? (i tried got a 401)

Hmmm...

If you try to access it via your external IP from a different network (phone, starbucks, etc), what happens?

---

### Post by drakoumel on 2013-04-25
from phone (on 3g) same thing :P

---

### Post by CharlesA on 2013-04-25
Check the apache logs to see if you are actually hitting the web server.

```
tail /var/log/apache2/access.log
```

---

### Post by drakoumel on 2013-04-25
i am seeing my local ip (the non-server machine) already had checked that by watching the tcp traffic

---

### Post by drakoumel on 2013-04-25
ohh god.. would being behind another router cause this? my building provides the internet and probably have a router downstairs in some dungeon to split to each room

---

### Post by darkod on 2013-04-25
Of course. In that case the public IP is not on your home router, it's on the building router. Most probably.

---

### Post by mobo on 2013-04-25
Hate to but in here but something to check on is if the router has a DMZ zone (Demilitarized) for the Servers ip so it can be accessed from outside the lan.

---

### Post by darkod on 2013-04-26
First make sure you don't have another router in front, as you suspect. If you do, whatever you do on your home router is pointless. You would need control of the "building" router, and forward port 80 to the WAN IP of oyur home router. So the traffic will go from one to another, then again forwarded to your server.

---

### Post by drakoumel on 2013-04-26
yes thats the case, the building router is redirecting to a proxy or a firewall thus getting the level_15_access prompt. Thanks a lot everyone !

---

