---
title: "dnsmasq's dhcp-range"
date: 2009-06-06
forum: Server Platforms
---

### Post by makara.aktee.sok on 2009-06-06
Hi, 
I'm using an ubuntu box as a dhcp server. 
My ubuntu box's ip is 192.168.3.1. The DHCP-Range is 192.168.3.50 to 192.168.3.250. 

I need more than 200 addresses. I tried changing it to.. 
192.168.3.50,192.168.10.250,1h 
but that didn't really work out - the DHCP didnt work (all clients had 169.x.x.x IP)

Am I doing something wrong? =/

A little bit more details: 
192.168.3.1 = ubuntu box
192.168.3.2 to 192.168.3.50 = reserved for access points (they have static ips configured to them)
I am using wifidog as an access point auth server. 
My wireless does not have any protection to it, but when they connect and try to go to a website, they are redirected to a login page.
Problem is: wandering iPhones are taking all the IP. 
Whenever I check my dnsmasq.leases, I see iphone everywhere. 
I tried putting a lease of 5minutes, but, that doesn't seem too smart. Alot of disconnection issues came with that. 
Then I thought, maybe if I put a lease of 12 hours, but have a big big range, like, 10x255, I won't have this problem anymore. I then changed the dnsmasq.conf, restarted.. and, no one couldn't connect anymore. 

I heard about the 172.16.x.x range, but I think 1 million ip is a little bit too much. 

Please ubuntu gurus! what should I do? :(

---

### Post by koenn on 2009-06-06
Did you change the subnet accordingly ?
and do you really need 4000 addresses ?

---

### Post by makara.aktee.sok on 2009-06-06
Subnet.. hmm, I don't think I have changed that. I will google that.

As for 4000 addresses, no, maybe 1000 is enought. Will 4000 put a big strain on the server??

---

### Post by Iowan on 2009-06-07
The standard 255.255.255.0 won't be enough for your range.  I found [this]("http://www.aboutmyip.com/AboutMyXApp/SubnetCalculator.jsp?ipAddress=192.168.3.50&cidr=23") online subnet calculator that might be useful.

---

### Post by bab1 on 2009-06-07
That's a great calculator Iowan.  It shows how the bits are flipped.

@ makara.aktee.sok

Both 192.168 and 172.16 have a 16 bit subnet mask limit.  You can expand the range of the 192.168.0.0 network to gain hosts. You are not forced to use 172.16.0.0 network to gain hosts.  

If you worry about the load on the server from to many host attaching, then limit the network to 4094 hosts with a 192.168.0.0/20 network.  This is 192.168.0.0 with a subnet mask of 255.255.240.0.  The range would be 192.168.0.0 to 192.168.15.255.

---

### Post by Iowan on 2009-06-07
Hopefully the [CIDR ]("Classless Inter-Domain Routing") notation (/24 instead of 255.255.255.0) won't cause problems for router or DHCP server - most can handle it.  It can certainly be handy to use "non-standard" subnets...

---

### Post by bab1 on 2009-06-07
> **Iowan said:**
> Hopefully the [CIDR ]("Classless Inter-Domain Routing") notation (/24 instead of 255.255.255.0) won't cause problems for router or DHCP server - most can handle it.  It can certainly be handy to use "non-standard" subnets...

If you can use /20 then 255.255.240.0 is the same.

---

