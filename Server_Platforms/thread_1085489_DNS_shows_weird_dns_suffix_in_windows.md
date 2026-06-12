---
title: "DNS shows weird dns suffix in windows"
date: 2009-03-03
forum: Server Platforms
---

### Post by Josh1 on 2009-03-03
Using Ubuntu 8.10 Server as the host, here is what I want to do:
On the linux server machine, provide every PC in the house with DNS, DHCP, Safesquid etc etc. I'm working slowly towards this, with testing and such in my free time.

Here is what I have so far:
I have setup BIND9, with the fake domain name "homeserver.com". It is this domain that I want all the PC's in the house to connect to, and be able to type into firefox/ie as the proxy (instead of typing 192.168.0.170, but I don't mind typing the IP in for now :P).
When I try to access a page, it works fine, it routes through the SafeSquid service and allows me to do it that way. When I go into the Network Connections on windows, and then change the DNS Server to my server (192.168.0.170), and then do an ipconfig /renew on the command line, it will then show homeservers.com as the domain suffix. I have checked through every single file I have edited on the server, and nowhere I have written homeservers.com, only homeserver.com. I have tested this out on a few PC's, and it still shows as homeservers.com.

When I try and ping another address on the network (192.168.0.x), it won't see that the PC is there and will return nothing. I am truly stuck.. I have tried everything I can think of but I'm out of luck.

If anyone can help me, or point me in the right direction I would be very grateful.

Sorry this has turned out sort of long winded. :P

---

### Post by netztier on 2009-03-03
> **Josh1 said:**
> 
I have setup BIND9, with the fake domain name "homeserver.com". 

Not that it'll help to resolve your problem as such, but:

```
marc@blaze:~$ **whois homeserver.com**
[...]
Domain name: HOMESERVER.COM


 Administrative Contact:
    Corporation, Microsoft  domains@microsoft.com
    1 Microsoft Way
    Redmond, WA 98052
    US
    +1.4258828080
 Technical Contact:
    Corporation, Microsoft  msnhst@microsoft.com
    One Microsoft Way
    Redmond, WA 98052
    US
    +1.4258828080
[...]

```

Don't do that, or you won't be able to connect to homeserver.com from your local network. And now don't say that "but I'll never have to do that" - because you just can't tell. A friend of yours might turn up at your home, trying to show you how he connects via Internet to his Microsoft Home Server he's running at his home - which will result in his PC looking for somename.homeserver.com - and your local DNS will say: "oh yes, I am authoritative for *.homeserver.com, but I don't know any host called 'somename'" and return an NXDOMAIN error code, which is a false negative answer.

It's not proper internetworking if you use someone else's DNS domain locally.

regards

Marc

---

### Post by netztier on 2009-03-03
> **Josh1 said:**
> I have checked through every single file I have edited on the server, and nowhere I have written homeservers.com 

Try this to search: grep will look for the string "homeserver" in every file (*) in /etc and all subdirs (-R):

```

user@server:~$ **cd /etc**
user@server:/etc$ **sudo grep -R homeserver ***
[sudo] password for user: <password>

```

output will look like:
```
...
subdirectory/filename:FullTextLineThatContainsTheString"homeserver"
subdirectory/filename:FullTextLineThatContainsTheString"homeserver"
subdirectory/filename:FullTextLineThatContainsTheString"homeserver"
...
```

So you should be able to see every line that contains "homeserver" anywhere, including the one that contains "homeserver**s**"

regards

Marc

---

### Post by Josh1 on 2009-03-03
Hey Marc,

Thanks for your reply. I considered this, and did think it was bad. So i decided to go with the suffix TLD .local since I think it's only for a local network and won't interrupt any "real" domains..

I also reformatted (since I'm just playing around to get a better hang of things for uni) and changed to homecontrol.local to less confuse me if I need to play around with Microsoft Homeserver in the future if I decide to get a certain cert or something.

Everything is working really well now, thanks for your help and advice. I now just need to get everything else working smoothly by fiddling some more, and I should be set.

Thanks.:KS

---

### Post by netztier on 2009-03-03
> **Josh1 said:**
> Hey Marc,

Thanks for your reply. I considered this, and did think it was bad. So i decided to go with the suffix TLD .local since I think it's only for a local network and won't interrupt any "real" domains..


Good thinking, but of all the seemlingly sensible options, you found a wrong one ;-). Darn - should've told you from the start, my apologies.

Using .local as your local domain conflicts with avahi, and it might hinder it from properly working:

[http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

You *can* run a .local domain in your network, and as long as you won't use any mDNS based name resolution, you'll never notice any side effects.

Macs for instance love finding each other on a LAN using multicast based name resolution (mDNS) and querying for "otherBoxName.local" - Apple call it "Bonjour", others call it "Zeroconf", it's Open Source implementation is called Avahi.

It even works by default in Ubuntu. Put two Ubuntus on a LAN without a DNS; you'll notice that you can ping one from the other using "ping ubuntubox.local". If however Avahi detects that your DNS server has an SOA record for .local, it disables itself. 

I spotted this on a fresh installation of Debian 5.0 Lenny, and it took me two hours to find out why. I was absolutely sure that my local DNS was *not* authoritative for .local. In the end, it turned out that my ISPs servers that I had configured as forwarders in fact were. In all the years I had never realised that I was using what probably were the ISPs internal DNSs instead of the supposed-to-face-the-customer ones. :-) Now why my ISP would make their own DNS authtoritative for .local is a mistery to me...

regards

Marc

---

