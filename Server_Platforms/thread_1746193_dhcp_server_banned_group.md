---
title: "dhcp server banned group"
date: 2011-05-01
forum: Server Platforms
---

### Post by jlittle on 2011-05-01
Here is the situation, I am setting up dhcp server for my public library and need to divide  clients into a number of pools on the same network. The different ranges  will be for different filtering requirements via squid/dansguard proxy.  I have inhouse clients: staff, adult patron, and child patron, that have  different filtering requirements and wireless guests that I want to  shorter lease times to handle the rapid turnover rate. Trying to  understand the terse manual, you assign pools via allow/deny members of  classes, but classes are assigned by matching on mac address or vendor  ids. Unfortunately as a poor rural library we have a hodge-podge of  hardware with no matchable pattern. So I can solve the inhouse clients  by using fixed-address, and remove them from the dynamic pool. Now the  dhcp server would be serving only the short term wireless guests from  the pool. 

A common problem at libraries, you always get a few that are compelled  to misbehave and break the libraries TOS. In the past the librarians  would kick the offenders out of the library only to have them link in  from the step or parking lot. Since I have their mac address in their  initial lease I would like to prevent them from reestablishing a  connection when they are banned. 

My thinking is this; the library's computers are static and not part of  the pool, the wireless clients would be unknown-clients, so set the pool  to allow only unknown-clients, and for the "bad-boys" add their hosts in  a group directive would make them "known" and therefore unable to get a  IP from the dhcp server. 

group { 
    host banned1 { hardware ethernet 00:00:00:00:00:01; } 
    host banned2 { hardware ethernet 00:00:00:95:a6:c1; } 
    host banned3 { hardware ethernet 0c:f1:b6:fe:00:01; } 
} 

subnet 192.168.0.0 netmask 255.255.255.0 { 
    pool { 
        allow unknown-clients 
        range 192.168.0.200 192.168.0.250; # 
        default-lease-time 3600;    # 1 hr 
        max-lease-time 10800;        # 3 hrs 
    } 
    # inhouse static clients 
    host circulation1 { 
        hardware ethernet 0f:f0:b6:fe:00:01; 
        fixed-address 192.168.0.50 
    } 

    ... 
} 

Would this work? Is there a better approach? I tried using groups to  assign a custom identifier, and then assign a classes by matching the  identifier value and used that to assign the pools, but could not seem  to get it to work. It also seemed too complicated. 

# my identifer 
option local-dept code 200 = text; 

group { 
    host foo { hardware ethernet 00:00:00:00:00:01; } 
    host bar { hardware ethernet 00:00:00:95:a6:c1; } 
    ... 
    option local-dept "staff"; 
} 

... 
class "staff" { 
    match if option local-dept code = "staff" 
} 

pool { 
    allow members of "staff"; 
    ...

---

### Post by elico on 2011-05-01
i would got for a more complex idea but more likely will work.
to fake a MAC address is fairy simple so...
what is the major problem with the users?
the boy that dont gets ip will set the IP manually so..
you can use 2 ways.
1. authentication(with interception proxy)
2. banning users using iptables rules and not in the dhcp server.
let say limiting number of connections allowed..
redirecting to a block page with warning about bad usage. 
i have seen in a internet coffee that has a captive portal and the internet access opens with code or agree to usage license and after 30 minutes ends the web surfing asking you to agree again.

---

### Post by jlittle on 2011-05-03
> **elico said:**
> i would got for a more complex idea but more likely will work.
to fake a MAC address is fairy simple so...
what is the major problem with the users?
the boy that dont gets ip will set the IP manually so..


Yes I thought of that, most will not be able to it but some might.

> **elico said:**
> 
you can use 2 ways.
1. authentication(with interception proxy)


I never done proxies before, but is setting up interception proxy difficult? A good resource?

> **elico said:**
> 
2. banning users using iptables rules and not in the dhcp server.
let say limiting number of connections allowed..
redirecting to a block page with warning about bad usage. 
i have seen in a internet coffee that has a captive portal and the internet access opens with code or agree to usage license and after 30 minutes ends the web surfing asking you to agree again.

Not sure and timed limit would be best for us, we are poor rural area. Some patrons come in to get work done because that have no real internet connection at home. 

How you you ban users via IP tables? I am using Shorewall on the gateway so I would need in in Shorewall-ese Seems each fontend for IP tables does not make IP Tables less confusing just confusing in different ways! ;-)

---

### Post by Cheesehead on 2011-05-03
I have four groups of IP addresses on my network. The router uses dnsmasq for serving addresses. IPTables provides different levels of access to each group.

I use a subnet mask of 255.255.255.224 to provide 30 available nodes in each group.

Yeah, a MAC spoofer can jump into a different group if they really want to...but they are currently very rare. And they need to do some homework to figure out the subnets. Most guests simply want network access.

Nothing - x.x.x.0 /255.255.255.224

Whitelisted - x.x.x.32 / 255.255.255.224     Reserved IPs only, Server access

Nothing - x.x.x.64 / 255.255.255.224

Guest - x.x.x.96 / 255.255.255.224     Network access only

Blacklist - x.x.x.128 / 255.255.255.224    (Still in development) Deliberately throttled (very slow) network access, randomly dropped packets and connections, and other annoyances.

Nothing - x.x.x.160 / 255.255.255.224

Server, Router, Printer - x.x.x.192 / 255.255.255.224    Static IPs only

Nothing - x.x.x.224 / 255.255.255.224

dnsmasq's .conf files makes it easy to filter large numbers of MAC addresses, and to move a MAC address from one group to another. I have one .conf.d/whitelist file and another .conf.d/blacklist file, and a couple scripts to monitor the guests.

---

