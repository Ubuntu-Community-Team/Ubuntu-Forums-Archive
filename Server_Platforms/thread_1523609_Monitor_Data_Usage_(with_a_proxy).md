---
title: "Monitor Data Usage (with a proxy)?"
date: 2010-07-03
forum: Server Platforms
---

### Post by burcyril10 on 2010-07-03
Hey,

I have a question to everyone who might know of software I don't know exists - is there something which can act as a fully fledged proxy (exactly like squid) but which can also monitor data usage?

At the moment what I do is I log data usage of IP addresses (allocated by DHCP) by using IPFM. Obviously getting a new IP address from a DHCP server isn't hard and this could be abused.

So I was thinking if I require proxy authentication and log usage that way, there is no way for anyone to abuse the system.

Does anyone know of a proxy server capable of logging data usage?

Frankly I'm surprised squid doesn't do it - perhaps it can, how do you set that up?

Thanks for any insight,
 - Cyril

---

### Post by DJYoshaBYD on 2010-07-03
ummmm.. damn.. good question..

for network monitoring, my NO. 1 fav tool is WireShark.. To me, that is probably the best network protocol analysis tool i have used.. I used to use Ethereal back in the day, before they had to change the name..

give that a shot, and see if that helps..

---

### Post by burcyril10 on 2010-07-03
Yeah, wireshark is awesome. The problem is I don't need that much information (although I think I will install it one day to monitor torrent usage) but I'm going from most urgent to least urgent.

At the end of the day my problem is that there is no way for me (at the moment) to authenticate who is who.

So I'm stuck - I can prevent access based on knowing who is who (squid can do that nicely), and I can log IP address data usage (IPFM does that well) but as far as I can see, there is no way for me to correlate both...

---

### Post by DJYoshaBYD on 2010-07-03
maybe set up a RADIUS server for authentication? that would log who is logging on when and how, usernames, IPs, etc etc etc..

I mean, are you trying to watch actual traffic leaving your network, or do you just want to monitor who is in the server?

---

### Post by burcyril10 on 2010-07-05
Well that's my plan for the wifi clients. I'm pretty sure a RADIUS server can do it all. But...will with work for cabled clients? 

I'm interested in data coming in (mostly the amount) but also what per client.

---

### Post by sil3nt on 2010-07-05
I personally used to use the community version of Astaro firewall, which does a lot of different things like proxy control, network , net usage with nice breakdowns of frequented sites etc.

The community version is limited to a certain number of ip's but should be ok for most typical home users.

If this is a business solution they also offer the same product but you will need to pay for it.

[http://www.astaro.com/solutions/network-security]("http://www.astaro.com/solutions/network-security")

---

