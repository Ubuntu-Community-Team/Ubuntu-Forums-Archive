---
title: "How to Create a Domain Name for Static IP"
date: 2011-04-26
forum: Server Platforms
---

### Post by thoufiq on 2011-04-26
Hi All,
           I am a new user of ubuntu and I want to set a domain name for my static ip address. If i am giving my static ip, i got output but i cant create a domain name instead of giving ip address.


Anyone help me....

Thanks

---

### Post by Ryan Dwyer on 2011-04-26
Sounds like you want to set up a free account at dyndns.org.

Alternatively, you can pay a registrar for a real domain name like yoursite.com.

---

### Post by elico on 2011-04-26
you need to buy one..
you can try godaddy.com or other domain Registrars.
or use DYNDNS as a starter.

---

### Post by AllGamer on 2011-04-26
**@thoufiq**

In case you are just trying to do this locally on your TEST environment, and not for real internet usage as suggested above.

You can always edit your HOST file with the local Doman Name that you want to use, with the associated IP, and then configure BIND9 to offer DNS resolution for your local machines connected to it.

so they can all resolve the same set of custom IP & DNS entries

---

### Post by TheFu on 2011-04-26
> **thoufiq said:**
> Hi All,
           I am a new user of ubuntu and I want to set a domain name for my static ip address. If i am giving my static ip, i got output but i cant create a domain name instead of giving ip address.
Anyone help me....
Thanks

edit the /etc/hosts file on every Linux/UNIX machine on your network and put the name you want in there.  On MS-Windows, this same file is buried under system32/drivers/etc/hosts.txt (I think).  Obviously, this will only work for systems with YOUR updates to these files AND it won't work for random people on the internet.

If you want this machine on the internet, it is more complicated. You need
a) purchase a domain name from an internet "registrar"
b) purchase DNS service from a DNS service provider
c) setup the DNS service to point YOUR "purchased domain name" to your static IP

Simple, but there are technical details that you'll want to research in advance.  You can buy the domain name AND DNS service from 1 place, but I wouldn't.  

You'll want to setup the "A" record in DNS and perhaps a few CNAME records and maybe an MX record to support email.  Most DNS providers have a web interface that you'll figure out.  Your DNS updates will take 4 hours to 2 days to propagate around the world.  Don't expect them to be instantaneous.

---

### Post by thoufiq on 2011-04-27
> **TheFu said:**
> edit the /etc/hosts file on every Linux/UNIX machine on your network and put the name you want in there.  On MS-Windows, this same file is buried under system32/drivers/etc/hosts.txt (I think).  Obviously, this will only work for systems with YOUR updates to these files AND it won't work for random people on the internet.

If you want this machine on the internet, it is more complicated. You need
a) purchase a domain name from an internet "registrar"
b) purchase DNS service from a DNS service provider
c) setup the DNS service to point YOUR "purchased domain name" to your static IP

Simple, but there are technical details that you'll want to research in advance.  You can buy the domain name AND DNS service from 1 place, but I wouldn't.  

You'll want to setup the "A" record in DNS and perhaps a few CNAME records and maybe an MX record to support email.  Most DNS providers have a web interface that you'll figure out.  Your DNS updates will take 4 hours to 2 days to propagate around the world.  Don't expect them to be instantaneous.


Hello TheFu & AllGamer,
            Thanks for your valuable suggestions. I am not creating domain name for real internet usage, i am trying to do in my localmachines for testing purpose. As u told, I have edited and changed the /etc/hosts file like this
[COLOR=Red]127.0.0.1  localhost
123.201.137.218 myosm.org dhcppc4 (dhcppc4 is a hostname)[/COLOR]

But still, i cant run my domain name in my localhost. Also while restarting bind9, i got error like this
[COLOR=Red]*stopping domain name service...  bind9
rndc: connect failed: 127.0.0.1#953: connection refused               [ok]
*starting domain name service...  bind9                                           [fail]
[COLOR=Black]
I want to clarify another thing that, Should i edit [COLOR=Red]/etc/bind/named.conf.local [COLOR=Black]and[/COLOR] /etc/bind/named.conf.option[/COLOR] and modify or add any commands to create a domain name for test environment in my localmachines.
[/COLOR][/COLOR]

---

