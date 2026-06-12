---
title: "My back hurts"
date: 2013-07-07
forum: Ubuntu, Linux and OS Chat
---

### Post by feardotcom on 2013-07-07
So i had the Netgear N900 wifi usb adapter for my computer. It became to be a pain in the butt to maintain and it was not relibable. I was having to update drivers after every update to the kernel. So finally i got a new wifi adapter, a cheap $15 adpater from newegg. Now, i paid like $70 for my N900 from netgear. About the only difference that i see is that the N900 can use 5ghz band with dual banding as well. But as i have my extender pulling 5ghz and broadcasting 2.4ghz because every device in the house except my desktop uses 2.4ghz. I see absolutly no speed difference between the two. they both download at 1.4MBps at the max i have seen anyway. So why do they sell such expensive cards if the download speeds are no different? Obviously the wifi to lan transfer rates are probably much different. They market the N900 for streaming movies, and gaming. But, if the download speeds are no different then whats the gimmick?

To me, i think theoretically, if the download speeds are the exact same then watching movies on hulu and gaming should be no different from one another?

---

### Post by mips on 2013-07-07
Your download speed is determined by the lowest common denominator which in most cases is your broadband link from your provider. Using a 10Tb/s LAN card is not going to make your broadband link faster.

---

### Post by feardotcom on 2013-07-07
My point exactly, so why charge $70 for a wifi adapter that has a 450mbps speeds when no one has a connection that fast? Then to add dual banding on top of it. Idk, maybe becuase they know people like me are going to buy it because they didn't any better, but now i do. I would just like to know if there is any logical use for 450mbps wifi adapter.

---

### Post by sanderj on 2013-07-07
> **feardotcom said:**
> My point exactly, so why charge $70 for a wifi adapter that has a 450mbps speeds when no one has a connection that fast?

I have a 300 Mbps FttH connection at home, so such a wifi solution would be interesting for me ...

And apart from that: a 450 Mbps wifi connection is handy *within* your LAN. And often LANs are at 1 Gbps nowadays. So a 450 Mbps Wifi connection means fast access to your NAS and other devices.

HTH

---

### Post by feardotcom on 2013-07-07
Yeah, i suppose your right. It will be interesting to see how things run once i get my FreeNAS server up and running. 

Just for curiosity sake, i wonder how much a 450mbps internet connection would cost. lol... im going to have to look that one up.

---

### Post by sanderj on 2013-07-07
> **feardotcom said:**
> 
Just for curiosity sake, i wonder how much a 450mbps internet connection would cost. lol... im going to have to look that one up.

A 300 Mbps FttH 3-play connection costs 60 Euro per month at Caiway (a Dutch provider). See [https://www.caiway.nl/site/nl/pakketten/alles-in-1glaspakketten/alles-in-1glascompleet](https://www.caiway.nl/site/nl/pakketten/alles-in-1glaspakketten/alles-in-1glascompleet)

A 500 Mbps FttH 3-play costs 88 Euro per month at KPN (the biggest Dutch provider): [http://www.kpn.com/prive/pakketten.htm](http://www.kpn.com/prive/pakketten.htm) (click on "glasvezel")

---

### Post by deadflowr on 2013-07-07
Beyond the actual chip advances the more expensive adapter has, it probably has a more durable design and quality.

---

### Post by CharlesA on 2013-07-07
> **feardotcom said:**
> My point exactly, so why charge $70 for a wifi adapter that has a 450mbps speeds when no one has a connection that fast? Then to add dual banding on top of it. Idk, maybe becuase they know people like me are going to buy it because they didn't any better, but now i do. I would just like to know if there is any logical use for 450mbps wifi adapter.

I've heard LAN transfer speeds are all the rage.

> **deadflowr said:**
> Beyond the actual chip advances the more expensive adapter has, it probably has a more durable design and quality.

Indeed, but then again, it also depends on the brand.

---

### Post by uRock on 2013-07-07
I have to ask myself the same question quite often. My Linksys router will not allow LAN transfers any faster than 2MBps.

---

### Post by CharlesA on 2013-07-07
> **uRock said:**
> I have to ask myself the same question quite often. My Linksys router will not allow LAN transfers any faster than 2MBps.

Same with my dlink, but I dunno what the deal with that is. I usually just plug my laptop in if I need to do any large file transfers as the speed blows.

---

### Post by feardotcom on 2013-07-10
> **uRock said:**
> I have to ask myself the same question quite often. My Linksys router will not allow LAN transfers any faster than 2MBps.

You need to upgrade your router if all you get is 2MBps. Sounds to me like you have a 10Base-T router, which is alittle weuird becasue 10Base-T is like 1.25MBps, not 2. Plus, theres nothing, that i'm aware of, between 10Base-T and 100Base-T. It's also more possible you could be running CAT4 cable which would explain the 2MBps because that's all it's rated for is 2MBps. My linksys router is 1000Base-T, but you have to have good quality CAT6 cable or above to take advantage of it. And, my wifi is only rated for 300Mbps So my my expensive paperweight was overkill anyway. 

Can you tell i bought all this crap before i started my networking degree? lol

---

### Post by sanderj on 2013-07-10
> **feardotcom said:**
> You need to upgrade your router if all you get is 2MBps. Sounds to me like you have a 10Base-T router, which is alittle weuird becasue 10Base-T is like 1.25MBps, not 2. Plus, theres nothing, that i'm aware of, between 10Base-T and 100Base-T. It's also more possible you could be running CAT4 cable which would explain the 2MBps because that's all it's rated for is 2MBps. My linksys router is 1000Base-T, but you have to have good quality CAT6 cable or above to take advantage of it. And, my wifi is only rated for 300Mbps So my my expensive paperweight was overkill anyway. 

Can you tell i bought all this crap before i started my networking degree? lol

It might the poster gets 2MBps = 20 Mbps on ... Wifi. Which can be quite normal.

---

### Post by feardotcom on 2013-07-10
Thats is very possible, but he specifically said LAN, not WLAN or wifi.

---

### Post by CharlesA on 2013-07-10
> **feardotcom said:**
> Thats is very possible, but he specifically said LAN, not WLAN or wifi.

Wifi to LAN will always be slower, but it all depends on your router, if there is interference, if there is a direct line or sight, and how strong your signal is.

I gave up transferring large files via Wifi as the transfer speeds blow compared to Gigabit Ethernet.

---

### Post by BigCityCat on 2013-07-10
Try Yoga.

---

### Post by uRock on 2013-07-11
> **feardotcom said:**
> You need to upgrade your router if all you get is 2MBps. Sounds to me like you have a 10Base-T router, which is alittle weuird becasue 10Base-T is like 1.25MBps, not 2. Plus, theres nothing, that i'm aware of, between 10Base-T and 100Base-T. It's also more possible you could be running CAT4 cable which would explain the 2MBps because that's all it's rated for is 2MBps. My linksys router is 1000Base-T, but you have to have good quality CAT6 cable or above to take advantage of it. And, my wifi is only rated for 300Mbps So my my expensive paperweight was overkill anyway. 

Can you tell i bought all this crap before i started my networking degree? lol

Lol, The network is wireless. When connected using CAT5 I get around 10MBps. I haven't seen how fast it can actually go because I can only afford the medium connection from my ISP, which is usually somewhere around 1.2MBps. I have had torrents push 5MBps. Not sure how they got past the ISP QoS settings, but it was nice for the few minutes that it happened.

As for overspending, I have debated buying one of the CCNA kits that come with 2 switches and a router just so I can set up a nice set of ACLs.

---

