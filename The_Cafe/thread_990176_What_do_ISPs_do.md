---
title: "What do ISPs do?"
date: 2008-11-22
forum: The Cafe
---

### Post by super breadfish on 2008-11-22
What does an ISP actually do? Sure, they give people internet access, but how does it work? My networking knowledge stops with setting up a LAN party, so when someone asked me this today I couldn't give much of an answer.

Is it possible to get net access without one?

---

### Post by Redache on 2008-11-22
ISPs basically offer Internet Service to users. Not all ISPs OWN anything, some rent off of bigger ISPs and resell to customers. For example in Britain BT own the whole Public Telecoms of the Country(apart from Hull) and resell wholesale to ISPs. 

Although companies like SKY,BE and so on are starting to set up their own equipment in the Exchanges and offer their own complete service to customers.

Basically you have one top tier ISP who owns the Underlying Network and lower Tier ISPs who buy the right to use a certain percentage of that Network and sell it to customers. It's why we now have problems in Britain as BT are refusing to do anything much to upgrade the Front Line Network to improve Broadband Speed (Although they are upgrading exchanges to be able to handle more bandwidth).

---

### Post by kernelhaxor on 2008-11-22
> **Redache said:**
> ISPs basically offer Internet Service to users. Not all ISPs OWN anything, some rent off of bigger ISPs and resell to customers. For example in Britain BT own the whole Public Telecoms of the Country(apart from Hull) and resell wholesale to ISPs. 

Although companies like SKY,BE and so on are starting to set up their own equipment in the Exchanges and offer their own complete service to customers.

Basically you have one top tier ISP who owns the Underlying Network and lower Tier ISPs who buy the right to use a certain percentage of that Network and sell it to customers. It's why we now have problems in Britain as BT are refusing to do anything much to upgrade the Front Line Network to improve Broadband Speed (Although they are upgrading exchanges to be able to handle more bandwidth).

Most of that is right except that there is not just one Tier 1 ISP but like 7 - 10 of them [http://en.wikipedia.org/wiki/Tier_1_carrier#List_of_Tier_1_IPv4_ISPs](http://en.wikipedia.org/wiki/Tier_1_carrier#List_of_Tier_1_IPv4_ISPs)

> From wikipedia: A Tier 2 Network is an Internet service provider who engages in the practice of peering with other networks, but who still purchases IP transit to reach some portion of the Internet.

Tier 2 providers are the most common providers on the Internet as it is much easier to purchase transit from a Tier 1 network than it is to peer with them and then attempt to push into becoming a Tier 1 carrier.

Read wikipedia about Tier 1 ISPs, Tier 2 ISPs, Peering and stuff like that

---

### Post by Yownanymous on 2008-11-22
Using Orange as a base model: Take your money, convince you you're getting a really good deal, supply you with some c**p modem that places an overhead on your CPU (Speedtouch) and have their servers break down ever week.:mad:

---

### Post by Redache on 2008-11-22
> Using Orange as a base model: Take your money, convince you you're getting a really good deal, supply you with some c**p modem that places an overhead on your CPU (Speedtouch) and have their servers break down ever week.  

The Speedtouch modems are pretty much Industry standard with any ISP. Server breakdowns aren't necessarily their fault either, it could be Open Reach's problems. 

Try using a Router instead of the supplied modem as they work a lot better and have more config options.

I've never liked Orange though, "Free" Broadband can never truly exist in a "Free" market.

---

### Post by gn2 on 2008-11-22
> **Yownanymous said:**
> ~ and have their servers break down ever week.:mad:

Under the weight of spam.

Orange UK is probably one of the biggest spam magnets on the planet.

If you have spam protection software you need to test, connect it to an Orange e-mail service.

---

### Post by klange on 2008-11-22
They route TCP/IP packets and map IP addresses.

And if you're not protected by network neutrality laws, they filter content and restrict your access.

**e**: And mine now relays my mail, so people like SBC and my high school don't block it. Wonder why I didn't do that a long time ago...

---

### Post by billgoldberg on 2008-11-22
What does my ISP do?

Charge me around 70 euro a month for medium speeds and a 60gb bandwith limit.

---

### Post by Tom--d on 2008-11-22
Can I make a computer into my own 'ISP'?
Just for my home?

---

### Post by billgoldberg on 2008-11-22
> **Tom--d said:**
> Can I make a computer into my own 'ISP'?
Just for my home?

That doesn't make much sense.

An ISP lets you use their network so you can get on the internet.

You can create an [intranet]("http://en.wikipedia.org/wiki/Intranet") in your home.

---

### Post by klange on 2008-11-22
> **Tom--d said:**
> Can I make a computer into my own 'ISP'?
Just for my home?

Do you have the money to pay for access to other segments of the Internet? Undoubtedly, no. And there are also ICANN fees for reserving IP ranges...

---

### Post by Frak on 2008-11-22
An ISP is a company who has acquired rights and access to the internet backbone through InterNIC and the ICANN. They route into the internet backbone and is required to provide efficient transfers throughout. The ISP builds, extends, or rents out inner-backbones to service their customers through the use of Fibre Optic lines. The ISP takes care into making sure that all lines are in tip-top condition and working order. Some ISPs, such as Comcast, AT&T, Verizon, and Washington Post, have been contracted through the government to condition government owned backbone lines. These companies are predominant along the backbone because part of their costs are paid for through government assistance.

> **Tom--d said:**
> Can I make a computer into my own 'ISP'?
Just for my home?

Yes and No. Yes, if you have the time, effort, and workforce to create, maintain, and market your lines. You would be required to provide the power from the portal hub (a hub set by the government as a point where ISPs may hook into the line) to where you provide your service. No, if you cannot afford or want to do all this ;)

Also, remember, Fibre-optic lines can only transfer up to 54Mbit/s. The excellent high speed transfer is determined through a compression through the ISP. Your modem compresses packets, sends them to the ISP, where then the ISP decompresses the packets and recompresses them again to maintain an efficient line. Fibre, though, is good because it has no latency issues, which is why it is used as the backbone.

---

### Post by lisati on 2008-11-22
The ISP I use here "down under" recently provided me a "free" speedtouch modem as a replacement to the D-link freebie they'd sent me when I first signed up for broadband (they recently upgraded the gear in my area to use ADSL2+)  - one catch is they "forgot" to include a user manual (even though the packaging said there was one). No way was I going to rely on the default settings that the ISP's customized setup CD set up....so a few minutes on Google managed to locate one.

---

### Post by klange on 2008-11-22
As of a few minutes ago, my ISP now relays my out going SMTP, which is good for me because it means my messages won't get blocked because I'm on an ISP-assigned IP, which is then good for my users.

---

### Post by Tom--d on 2008-11-22
What I mean is..

Can I just connect to the internet? By passing the ISP?

---

### Post by Frak on 2008-11-22
> **Tom--d said:**
> What I mean is..

Can I just connect to the internet? By passing the ISP?
No, because you don't have an addressed IP and piggybacking is illegal.

---

### Post by Tom--d on 2008-11-22
> **Frak said:**
> No, because you don't have an addressed IP and piggybacking is illegal.

I see. Thanks.

Piggybacking?

---

### Post by Frak on 2008-11-22
> **Tom--d said:**
> I see. Thanks.

Piggybacking?
Using somebody else's IP but on a different Tier.

---

### Post by ciscosurfer on 2008-11-22
> **Tom--d said:**
> I see. Thanks.

Piggybacking?[Piggybacking]("http://en.wikipedia.org/wiki/Piggybacking_%28internet_access%29")

e: Closed parens weren't working before for some reason. Link should be fixed now.

---

### Post by broadbanduk on 2008-11-27
ISP provide only the internet services ... ..!!

---

### Post by Ozor Mox on 2008-11-27
This thread has been helpful, thanks. I've always wondered how ISPs work.

Another thing though, say net neutrality broke down and all ISPs started allowing access only to websites that paid highly for it, rendering the rest of the internet pretty much useless... Is it feasible for an alternative free, net neutral internet to somehow be created? All the technology is available right, since anyone can create a local network in their home? It's just the logistics of it.

---

### Post by mips on 2008-11-27
> **Ozor Mox said:**
> 
Another thing though, say net neutrality broke down and all ISPs started allowing access only to websites that paid highly for it, rendering the rest of the internet pretty much useless... Is it feasible for an alternative free, net neutral internet to somehow be created? All the technology is available right, since anyone can create a local network in their home? It's just the logistics of it.

It's kinda hard to say as you get different Tiers in ISP's.

There are only [8 Tier 1 ISP's]("http://en.wikipedia.org/wiki/Tier_1_carrier#List_of_Tier_1_IPv4_ISPs") in the world and essentially they control the internet. After that you get [Tier 2]("http://en.wikipedia.org/wiki/Tier_1_carrier#List_of_Tier_1_IPv4_ISPs") & [Tier 3]("http://en.wikipedia.org/wiki/Tier_2_network") ISP's

There is a shiteload of politics and other issues that are also involved.

---

### Post by Frak on 2008-11-27
> **broadbanduk said:**
> ISP provide only the internet services ... ..!!
They can provide private services, such as roadrunner or AT&T's member services.

---

