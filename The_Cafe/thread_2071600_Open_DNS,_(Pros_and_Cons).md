---
title: "Open DNS, (Pros and Cons) ?"
date: 2012-10-15
forum: The Cafe
---

### Post by cbanakis on 2012-10-15
Just learned something new about the internet. :)

I've been reading about it, but I can't seem to be able to find any facts about it.

Allegedly, using open dns instead of your isp's dns, makes your internet faster and more secure?

Is there a downside?

If you know about this, and have experience with it, please share any pro's and con's you have experienced.

I guess I can start this off with...

Pro - a p2p site I use regularly stopped working recently (appeared to be down), but switching to open dns made it work again, somehow.

(Also, if someone could explain why that fixed it, that would be super)

---

### Post by Welly Wu on 2012-10-15
I purchased OpenDNS Home VIP service for one year for $20 USD. OpenDNS is the largest DNS service provider in the world. It helps to give you a clean surfing experience by replacing your ISP's DNS servers with OpenDNS servers.

If you do p2p, then you should consider paying for VPN service provider. WiTopia is a good combination with OpenDNS.

---

### Post by samalex on 2012-10-16
I use the freebie OpenDNS at home, and it's nice, especially since Time Warner often does DNS hijacking which irritates the heck out of me.  I can't say it's any faster though.

---

### Post by juancarlospaco on 2012-10-16
Benchmarking with [http://code.google.com/p/namebench](http://code.google.com/p/namebench) theres no faster DNS than the google's 8.8.8.8.

OpenDNS is not DNS. It does not follow the DNS standard, since if some name dont exist it MUST return an Error, opendns returns their own web search page with ads.

---

### Post by sammiev on 2012-10-16
> **juancarlospaco said:**
> Benchmarking with [http://code.google.com/p/namebench](http://code.google.com/p/namebench) theres no faster DNS than the google's 8.8.8.8.

OpenDNS is not DNS. It does not follow the DNS standard, since if some name dont exist it MUST return an Error, opendns returns their own web search page with ads.

Google's DNS 8.8.8.8 and 8.8.4.4 are both great, been using them for more than a year now with no problems. Works great with my VPN from WiTopia

---

### Post by zombifier25 on 2012-10-16
I use DNSCrypt, which only works with OpenDNS. I agree that OpenDNS's search page is a real PITA, but for now I turn it off in my account's setting.

---

### Post by Dr. C on 2012-10-16
I simply prefer to run my own DNS. Three steps:
1)```
sudo apt-get install bind9
```
2)
Set your DNS to 127.0.0.1
3)```
sudo /etc/init.d/bind9 restart
```
If one is runing other computers or devices on the network particularly those running an OS that does not have bind9 built in such as Microsoft Windows or IOS then one simply sets those computers or devices to use the DNS provided by an Ubuntu or other GNU/Linux box either directly or via the router or other DHCP server.

---

### Post by sammiev on 2012-10-16
> **Dr. C said:**
> I simply prefer to run my own DNS. Three steps:
1)```
sudo apt-get install bind9
```
2)
Set your DNS to 127.0.0.1
3)```
sudo /etc/init.d/bind9 restart
```
If one is runing other computers or devices on the network particularly those running an OS that does not have bind9 built in such as Microsoft Windows or IOS then one simply sets those computers or devices to use the DNS provided by an Ubuntu or other GNU/Linux box either directly or via the router or other DHCP server.

Seen this before but never played with it. Will play this weekend with these settings. :)

---

### Post by Warprunner on 2012-10-16
> **samalex said:**
> I use the freebie OpenDNS at home, and it's nice, especially since Time Warner often does DNS hijacking which irritates the heck out of me.  I can't say it's any faster though.

I agree and the exact reason I use it also!!!!

---

### Post by 1clue on 2012-10-16
Don't know about OpenDNS or Google DNS.  I've used ZoneEdit for free dns at work, and use its servers as backups on my home network.

Frankly having your own DNS server inside your LAN is a huge help for a number of reasons.

First, you're not susceptible to an outage by an ISP or any other service.  Conversely, you ARE susceptible to an outage on your own hardware, and that's much more likely if you discount deliberate outages by your ISP.

Second, DNS makes a significant bit of traffic for web browsing.  If you have a caching DNS on your LAN, there is one lookup per domain name per NETWORK rather than one lookup per computer, and that lookup survives reboots of the client systems.

Third, you can redirect ad sites to be a local box which doesn't even listen, just refuses traffic.  That might look uglier but it's way faster than loading a bunch of irritating ads, and more secure if you throw sites you don't trust in there too.

---

### Post by ikt on 2012-10-17
> **juancarlospaco said:**
> Benchmarking with [http://code.google.com/p/namebench](http://code.google.com/p/namebench) **theres no faster DNS than the google's 8.8.8.8.**

Hrmmm?

Internode AU-2 is 94.4% Faster than your current primary DNS server

Primary Server 192.231.203.3 Internode AU-2 (My isp's backup DNS server)
Secondary Server 127.0.0.1 SYS-127.0.0.1 (My ISP's primary DNS server)
Tertiary Server	192.168.0.72 (my local dns server)

8.8.4.4 comes in 5th place after a rival ISP's DNS server.

---

### Post by SlugSlug on 2012-10-17
in a default install - where does bind9 retrieve it's information from?

---

### Post by 1clue on 2012-10-17
From root dns servers, same as any other DNS

---

### Post by juancarlospaco on 2012-10-19
> **ikt said:**
> Hrmmm?

8.8.4.4 comes in 5th place after a rival ISP's DNS server.

We both are right, since my ISP != your ISP.

---

### Post by lykwydchykyn on 2012-10-19
> **juancarlospaco said:**
> 
OpenDNS is not DNS. It does not follow the DNS standard, since if some name dont exist it MUST return an Error, opendns returns their own web search page with ads.

This is why I quit using opendns.  I have a server at home that does its own dns, and when it went down and I'd try (not knowing it was down) to ssh in, my client would try to ssh into opendns's server and I'd just get "connection refused".  Sent me barking up the wrong tree one too many times.

---

### Post by juancarlospaco on 2012-10-19
> **lykwydchykyn said:**
> This is why I quit using opendns.  I have a server at home that does its own dns, and when it went down and I'd try (not knowing it was down) to ssh in, my client would try to ssh into opendns's server and I'd just get "connection refused".  Sent me barking up the wrong tree one too many times.

I code Python stuff, and a non-standard DNS cause several problem, that should not be.

---

### Post by lykwydchykyn on 2012-10-19
> **juancarlospaco said:**
> I code Python stuff, and a non-standard DNS cause several problem, that should not be.

I can see that.  In my case, it was a security issue as well because my credentials were being sent to someplace other than where they were supposed to.

---

