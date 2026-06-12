---
title: "How does IP allocation work?"
date: 2011-12-11
forum: The Cafe
---

### Post by mamamia88 on 2011-12-11
I am trying to follow these directions.  [http://www.dd-wrt.com/wiki/index.php/Client_Bridged](http://www.dd-wrt.com/wiki/index.php/Client_Bridged)  but am having a hard time figuring out how to chose the right ip.   My routers main routers configuration page is at 192.168.1.254  DHCP range is 192.168.1.64 to 192.168.1.253  now i have 3 devices that are .65,.66,.67 then it jumps to 2 devices that are .100 and .101.  This doesn't seem logical to me.  Why would it not go .68,.69 etc?   Also when configuring the client bridge I would have to set the secondary router to something greater than .254?  So as long as it's greater than 254 it should work?    Please networking gurus help me out

---

### Post by e79 on 2011-12-11
> Why would it not go .68,.69 etc?As far as I'm concerned, you DHCP reservation is too big for your needs; unless you really need a range of 189 IP address for you purposes, bring it down to 15-25 IP (192.168.0.64-192.168.0.89). The router choose on its own which address to lease unless you make DHCP reservation (MAC address --> specefic IP).

Avoiding getting into to much details, you cannot get further than 192.168.0.254 as it ends at 192.168.0.255 which would be the broadcast address for that kind of subnet (I'm assuming here you choose the default subnet mask 255.255.255.0).

Hope this helps

---

### Post by 3Miro on 2011-12-11
The DHCP routers give off IP addresses at random, there is no way to predict which device would get which IP. You can specify a range and in some cases routers have the option to map a MAC address to an IP (i.e. some devices would always get certain IP), but this is rare and a it redundant. If you want static IP then you should just set things up as static IP.

IP addresses are made of 4 bytes i.e. 1.2.3.4. Each byte has 8 bits and a bit can be either 0 or 1. This means that 8 bits can store 2^8 = 256 values from 0 to 255. This is for general number, in the case of IP, 255 is reserved, so you can only assign values from 0 to 254.

---

### Post by mamamia88 on 2011-12-11
So would i be better off just setting my main router to 192.168.1.1 so that it's exactly the same as the directions?

---

### Post by e79 on 2011-12-11
That is up to you. Choose w/e IP address for your router, define your DHCP range as you see fit and let the router do the rest, but I personally prefer assigning static IP addresses to the most used machine (preferably out of your DHCP scope).

Example:

Router IP : 192.168.1.1
Machine A: 192.168.1.2
Machine B: 192.168.1.3
Machine C: 192.168.1.4
.....
DHCP Scope : 192.168.1.20-192.168.1.30

Of course, you can leave the subnet as it is : 255.255.255.0

---

### Post by Iowan on 2011-12-11
My network uses the low addresses (.1 to .9) for servers,printers, etc., then uses the next ones (.10 to .20) for DHCP clients. My network is not so large that I need more than 11 clients. (I could always change DHCP range, if required). I have assigned some static leases - mostly for practice. You could use a similar strategy by saving the top 5-10 addresses for servers, routers, etc., by changing the top end of your DHCP range to .250 (or .245) - or lower if you don't need the additional addresses.

---

