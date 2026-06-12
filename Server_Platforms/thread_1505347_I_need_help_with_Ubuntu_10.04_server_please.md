---
title: "I need help with Ubuntu 10.04 server please"
date: 2010-06-09
forum: Server Platforms
---

### Post by syphax922 on 2010-06-09
So a couple days ago I decided to try my hand at servers (yeah that's how big of a noob I am at this) and so I am converting my old desktop to a dedicated server. I have been using [this guide]("http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p5") and I am on the page the link is to (5). So far everything has been great, but I have run into an issue: My computer has the same response for any package I attempt to install:   _[COLOR=Black]No candidate version found for [name of package][/COLOR]_.... so I am confused... and lost... please help...

---

### Post by lisati on 2010-06-09
*Thread moved to  Server Platforms*

Have you applied system updates yet? You can do this with:
```
sudo apt-get update && sudo apt-get upgrade && sudo-apt-get dist-upgrade
```

---

### Post by syphax922 on 2010-06-09
Hmmm... I can not even update... it says "failed to fetch..."
I changed the adresses in /etc/apt/sources.list from us.archive... to de.archive... as the tutorial said, and then changed them back, thinking it was region specific, but I got even more "failed to fetch"es
Also, thank you for putting this in the right spot...

---

### Post by syphax922 on 2010-06-09
The light n the back of my computer that indicates an internet connection is on... but is it possible that I somehow disabled the internet? such as when I gave myself a static IP address? I am going to reset m router in hopes that that is it.

---

### Post by syphax922 on 2010-06-09
Resetting the router didn't work... really starting to wonder if I completely screwed this up...

---

### Post by Black_Prince on 2010-06-09
Can you paste your 

**ifconfig**[B]

cat /etc/resolv.conf[/B]

[B]cat /etc/network/interfaces

[/B]output?

---

### Post by syphax922 on 2010-06-09
> **Black_Prince said:**
> Can you paste your 

**ifconfig**[B]

cat /etc/resolv.conf[/B]

[B]cat /etc/network/interfaces

[/B]output?

1. Where is ifconf? simply typing it into the command line returns "No command isconf found, did you mean..." I assume that ifconf is a file and I am missing something on the front end of the command

2. 
nameserver 192.168.0.1
domain hsd1.ga.comcast.net.
search hsd1.ga.comcast.net

3.
#  This file desribes the network interfaces available on your system
#  and how to activate them, for more information, see interfaces (5).

#  The loopback network interface
auto lo
iface lo inet loopback

#  The primary network interface
auto eth1
iface eth1 inet static
           address 192.168.0.1
           netmask 255.255.255.0
           network 192.168.0.1
           broadcast 192.168.0.255
           gateway 192.168.1.1




Should the broadcast have 3 digits in the last set?

---

### Post by kextyn on 2010-06-09
The command is "ifconfig" not "ifconf" or "isconf" (I'm assuming that was a typo).  If you're familiar with Windows ifconfig is similar to ipconfig.

Your netmask says you're on a class c network but your gateway is on a different class c than your server.  If your gateway (your router) is really 192.168.1.1 then your server should be something in the realm of 192.168.1.2-192.168.1.254.

---

### Post by syphax922 on 2010-06-09
> **kextyn said:**
> The command is "ifconfig" not "ifconf" or "isconf" (I'm assuming that was a typo).  If you're familiar with Windows ifconfig is similar to ipconfig.

Your netmask says you're on a class c network but your gateway is on a different class c than your server.  If your gateway (your router) is really 192.168.1.1 then your server should be something in the realm of 192.168.1.2-192.168.1.254.

Alright... well I am REALLY new at this so... when you say the SERVER should be 192.168.1.2-192.168.1.254 you are referring to the spot labeled address, correct?

---

### Post by syphax922 on 2010-06-09
My laptop lists its connetion thusly:
Connection-specific DNS Suffix: hsd1.ga.comcast.net.
Description: Intel(R) PRO/Wireless 3945ABG Network Connection
Physical Address: &#8206;00-13-02-87-CA-8E
DHCP Enabled: Yes
IPv4 Address: 192.168.0.101
IPv4 Subnet Mask: 255.255.255.0
Lease Obtained: Wednesday, June 09, 2010 7:34:04 AM
Lease Expires: Thursday, June 10, 2010 7:34:04 AM
IPv4 Default Gateway: 192.168.0.1
IPv4 DHCP Server: 192.168.0.1
IPv4 DNS Server: 192.168.0.1
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: Yes
Link-local IPv6 Address: fe80::8494:ea35:4473:4232%12
IPv6 Default Gateway: 
IPv6 DNS Server: 


So gateway is 192.168.0.1, I must have had a typo... that means that stuff is most likely the source of the problem, correct? I have no clue how the addreses are supposed to relate, so if someone were to take the time to correct the list is the post above it would be greatly appreciated.

---

### Post by 1serveyou on 2010-06-09
> **syphax922 said:**
> 1
2. 
nameserver 192.168.0.1
domain hsd1.ga.comcast.net.
search hsd1.ga.comcast.net
 
 
 

 
I'm wondering this myself, and hopefully this how syphax as well, but if you notice the domain ends with a period, should it be like that for the search and anytime the domain is used? I asked a friend about it once(he wasn't near the computer), and he said that shouldn't be there, but I wondering if anyone knows abuot this.

---

### Post by syphax922 on 2010-06-09
[http://en.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)
that is why it had a period... I think...

---

### Post by 1serveyou on 2010-06-10
> **syphax922 said:**
> [http://en.wikipedia.org/wiki/Fully_qualified_domain_name](http://en.wikipedia.org/wiki/Fully_qualified_domain_name)
that is why it had a period... I think...

Thanks for the info

---

