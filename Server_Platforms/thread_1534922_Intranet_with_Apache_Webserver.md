---
title: "Intranet with Apache Webserver"
date: 2010-07-20
forum: Server Platforms
---

### Post by klaasvg on 2010-07-20
Hi,

I am configuring my Apache webserver under Ubuntu. I have my own domain drsklaus.nl referring to my  ISP IP-address and have configured some virtual hosts for the subdomains:
photoalbums.drsklaus.nl
intranet.drsklaus.nl

I would like to use the intranet as a private test environment for my PHP sites and courses. I configured the virtual hosts as follows:
[FONT="Courier New"]
<Directory /var/www/drsklaus.nl/subdomains/intranet>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride None
	Order deny,allow
	Deny from all
        Allow from 192.168.1.
</Directory>
[/FONT]

in an attempt to make the subdomain accessible only from the local network.
But it does not work, I guess when I type intranet.drsklaus.nl the name is resolved by DNS to my *external* IP address and therefore access is denied. This is confirmed by the entries in the logfile. 
So is there a way to use the intranet subdomain anyway? Or must I use another approach to make use of a private test environment under Apache?
Thanx for any help :)
Grtz Klaas

---

### Post by klaasvg on 2010-07-20
I think a possible solution could be adding the domain name to the local DNS system and mapping it to the right local IP address 192.168.1.100, but I cannot find an option on my router to do so...
Please any ideas???

---

### Post by cdenley on 2010-07-20
> **klaasvg said:**
> I think a possible solution could be adding the domain name to the local DNS system and mapping it to the right local IP address 192.168.1.100, but I cannot find an option on my router to do so...
Please any ideas???

Do you have a local DNS server? You could also add an entry in /etc/hosts on each client that will access the intranet site. You could use another method for host resolution like avahi.

When you access your server by WAN IP, do you get a 403 response? Some routers won't route the connection back to the LAN which would result in no response. If you can connect by WAN IP, you could simply allow that IP.

---

### Post by klaasvg on 2010-07-20
Yes I get a 403 response!
I have not tried to modify the /etc/hosts entries on all PC's and do not want to do so... And I have no local DNS server but thought I can configure that on my router but it seems my router does not have a DNS server onboard... 
I configured the WAN IP address in my sites-enabled/intranet Apache 2 configfile and this works indeed! But now I can only access the intranet using the URL name, but that is no big problem I guess... exc ept for I need an internet connection!

SO I think this all distilles to the following options:
-Running a local DNS server and allow the local subnet 192.168 (no internet connection required)
-Not running a DNS server and allow the WAN address of my ISP (internet connection required)
-Some other way to run a local virtual server which is not accessable from the outside world (the WAN)?????

Thanks and maybe there are some more tips?
Grtz Klaas

---

### Post by cdenley on 2010-07-20
As I said, you can also resolve hostnames another way besides DNS, such as avahi or netbios.

Avahi would require all windows clients have bonjour installed. Then they could access your web server with [http://yourhostname.local/](http://yourhostname.local/).

Netbios would require you to install samba and run the nmbd component on the server. Non-windows clients would need to install and configure winbind. Then clients could access your server with [http://yourhostname/](http://yourhostname/).

I guess you may also be able to create a new record on your actual DNS server for intranet.drsklaus.nl which resolves to a LAN address. Some DNS hosting services may not allow this, though. Also, this would require internet access in order to reach a DNS server. The only universally compatible method for hostname resolution is DNS.

---

### Post by ingeva on 2010-07-20
> **cdenley said:**
> As I said, you can also resolve hostnames another way besides DNS, such as avahi or netbios.The way I do it on my local server is with the hosts file. This may take some more work than using DNS, but you only need to do it on the server, except the server IP must be defined in the hosts file on every client.

Example for the clients (Server is Pantera, IP is 10.10.10.2:
```
10.10.10.1 Router
10.10.10.2 Pantera
10.10.10.3 Papa
10.10.10.5 aurora
10.10.10.10 printserver
```

For the server (Domains and subdomains):
```
10.10.10.2 eldjarn
10.10.10.2 egni
10.10.10.2 pinyl
10.10.10.2 golita
10.10.10.2 bg.golita
10.10.10.2 count.golita
10.10.10.2 digest.golita
```

Apache definitions (sites-enabled):
```
<VirtualHost *>
    ServerAdmin inge@intertrafico
    ServerName eldjarn
    DocumentRoot /Store/WEB/public_html/eldjarn
</VirtualHost>
<VirtualHost *>
    ServerAdmin inge@pinyl
    ServerName egni
    DocumentRoot /Store/PINYL
</VirtualHost>
<VirtualHost *>
    ServerAdmin inge@pinyl
    ServerName pinyl
    DocumentRoot /Store/PINYL
</VirtualHost>
<VirtualHost *>
    ServerAdmin inge@pinyl
    ServerName golita
    DocumentRoot /Store/PINYL
</VirtualHost>
<VirtualHost *>
    ServerAdmin inge@pinyl
    ServerName bg.golita
    DocumentRoot /Store/PINYL
</VirtualHost>
<VirtualHost *>
    ServerAdmin inge@pinyl
    ServerName count.golita
    DocumentRoot /Store/PINYL
</VirtualHost>
<VirtualHost *>
    ServerAdmin inge@pinyl
    ServerName digest.golita
    DocumentRoot /Store/PINYL
</VirtualHost>

```

You should get the picture .... :)

---

### Post by klaasvg on 2010-07-27
Thanx ingeva, not anything is completely clear. I added the following to the /etc/hosts on the PC running Apache, which I will call server:
192.168.1.100 intranet.drsklaus.nl

And indeed, from the server PC I can now access the intranet sudomain without internet connection, after adding 192.168 to the allow from clause, just to hide the intranet from the rest of the world. 
	Order deny,allow
	Deny from all
        Allow from 94.210.173.239
        Allow from 192.168

But it is still not reachable from the other PC's on the network! You say that you only need to add the server PC to the /etc/hosts files of the other PC's in the network, but this does not work for me. When I add the following the the /etc/hosts file of my laptop (my desptop PC is also my server):
192.168.1.100    ubuntu-desktop

I still canntot reach the subdomains with my laptop. And in fact this is not surprising for me because this extra rule has no functionaliy... the server is IP-name mapping is already known by the router.
So maybe I miss something or I just have to install a DNS implementation on my server?

---

