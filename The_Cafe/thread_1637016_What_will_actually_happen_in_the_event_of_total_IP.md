---
title: "What will actually happen in the event of total IPv4 exhaustion?"
date: 2010-12-03
forum: The Cafe
---

### Post by Dustin2128 on 2010-12-03
I agree with predictions that we'll have total IPv4 exhaustion, workarounds nonwithstanding, around 2011 or 2012. If I understand correctly, this is also an internet problem; not strictly a web problem (e.g. no usenet). Basically my question is this: If all IPv4 addresses have been used, what happens when I try to connect to the net?

---

### Post by MisterGaribaldi on 2010-12-03
You won't be able to read my stunning mess...

[CLICK]

---

### Post by Austin25 on 2010-12-03
I think that address leases will go up in price, and ISPs will convert to network address translation.

---

### Post by Decatf on 2010-12-03
The Internet will close.

---

### Post by Trougedoor122 on 2010-12-03
Or you could convert to IPv6, and hope that company's convert their servers to accommodate IPv6 access.

As for the Network Address Translation, that, like everything else they've tried, is just a workaround.

---

### Post by sandyd on 2010-12-03
> **Dustin2128 said:**
> I agree with predictions that we'll have total IPv4 exhaustion, workarounds nonwithstanding, around 2011 or 2012. If I understand correctly, this is also an internet problem; not strictly a web problem (e.g. no usenet). Basically my question is this: If all IPv4 addresses have been used, what happens when I try to connect to the net?

its just the same scenario as the y2k thingy....
everyone will think the internet will end... cease to exist... while ISPs are already prepared (i.e. the issues are not as great as we think.) Besides, a lot of backbone providers such as Cogent have gotten ipv6 already. Since ISPs go on the backbone, it won't be hard to get ipv6.

In fact, I have it already (dual stack) . (not through a tunnel broker, I have a T1 line (2 bonded together) at home)

---

### Post by Dustin2128 on 2010-12-03
> **sandyd said:**
> its just the same scenario as the y2k thingy....
everyone will think the internet will end... cease to exist... while ISPs are already prepared (i.e. the issues are not as great as we think.) Besides, a lot of backbone providers such as Cogent have gotten ipv6 already. Since ISPs go on the backbone, it won't be hard to get ipv6.

In fact, I have it already. (not through a tunnel broker, I have a T1 line (2 bonded together) at home)
It's great that some are, but plenty of ISPs aren't going IPv6, and aren't planning to any time soon.

---

### Post by FuturePilot on 2010-12-03
> **sandyd said:**
> its just the same scenario as the y2k thingy....
everyone will think the internet will end... cease to exist... while ISPs are already prepared
Not even close. We were aware of Y2K well in advance and people actually did something about it. This time, we've been aware of IPv4 exhaustion for a long time now, but very few people have actually done anything.

> In fact, I have it already. (not through a tunnel broker, I have a T1 line (2 bonded together) at home)
You're in the minority, probably because you have a T1. I personally don't know anyone that has a T1 in their house. Most people are still on IPv4.

---

### Post by Sporkman on 2010-12-04
> **sandyd said:**
> Besides, a lot of backbone providers such as Cogent have gotten ipv6 already. Since ISPs go on the backbone, it won't be hard to get ipv6.

In fact, I have it already.

What does it mean to "get" ipv6, or to "have" it? Does that mean you have an ipv6 IP address? If an ISP "has" ipv6, does that mean you can't visit ipv4 IP addresses?

---

### Post by koenn on 2010-12-04
> **Sporkman said:**
> What does it mean to "get" ipv6, or to "have" it? Does that mean you have an ipv6 IP address? If an ISP "has" ipv6, does that mean you can't visit ipv4 IP addresses?

It means you're on a network (i.e. your isp's network) that uses IPv6 

You can still reach IPv4 networks, since your ISP will provide routing, tunneling and address translation to make the newtwork transparant to you / your computer

---

### Post by chriswyatt on 2010-12-04
Yeah, I was expecting most ISPs to be supporting IPv6 by now, I'm on BT and they did a trial a while back, but it ended ages ago.  So I guess they're prepared, but why haven't they switched it on already?

Oh well, if the ISP doesn't switch it on I'll just set up tunnelling.

Regardless, ISPs are gonna be forced into enabling IPv6 on their servers eventually, if their customers can't access certain sites then their customers aren't gonna be very happy about it.

---

### Post by juancarlospaco on 2010-12-04
I envy sandyd  :)

In the event of total IPv4 exhaustion, Internet will Stop growing, but will not stop working.

At the place i live, ISP are not ready at all, 
IPv6 is great, its the Future to keep the internet growing,
it produce notably more LAG on real-time things* (Games, UDP and such)*
because so lo0o0ong packet to transfer the same data,
IPv6 dont like NAT at all, 
the concept is everything have its own public IP connected to internet directly, 
strange on corporate environtments, where a NAT device suppose to control the traffic.

Ubuntu is IPv6 ready, so no problems, some of propietary OS dont,
anyways Teredo is a life saver*(?)*, the Quick'N'Dirty way, all go as UDP packets but IPv6 Tunneled.

> When the IPv4 space get drained, the **IPcalipsis will come...** *(read with scary voice)*

*...and then, on year 2038, just the similar episode with the 2038Bug, all 32Bit things will die suddendly.*

Im CCNA, some fake-IT-Technician will get a headache, job opportunity for skilled people.

Im reading *"IPv6 In Action"*, nice book.
:)

---

### Post by chriswyatt on 2010-12-04
It won't stop the internet growing.  Stunt its growth?  Yeah, probably.  Web hosts aren't gonna just say, "sorry, we can't host any more sites", obviously they'll have a vested interest to use IPv6 (or some other alternative).

---

### Post by sydbat on 2010-12-04
> **FuturePilot said:**
> We were aware of Y2K well in advance and people actually did something about it.Y2K was a media-induced hysteria that had absolutely nothing to do with reality. Insane amounts of money were spent by the panic-stricken to "save their computers from imminent destruction", when all anyone had to do was change the way the date was read**.

While this situation is not quite the same, the ISP's ARE prepared. They just haven't made a big media deal out of it.

**True story - working in an office in 1999, and the IT guys were scheduled to "fix the Y2K problem". I just went in and changed the Windows time settings. When the IT guy came in and loaded his "special CD that would fix the problem", the pop-up read something like "this computer is already compliant". The company had spent untold amounts of money on the software and training. All because of media hype****.

****Did I mention I am not that fond of the media?

---

### Post by juancarlospaco on 2010-12-04
You can have several webs with only 1 public IP.  :)

---

### Post by Sporkman on 2010-12-04
> **sydbat said:**
> Y2K was a media-induced hysteria that had absolutely nothing to do with reality. Insane amounts of money were spent by the panic-stricken to "save their computers from imminent destruction", when all anyone had to do was change the way the date was read**.

There was a lot of back-end legacy code, though, that encoded only the last two digits of the year. These were not modern windows systems.

---

### Post by chriswyatt on 2010-12-04
I don't know much about it, but are ISPs just playing the waiting game (as opposed to just refusing to support it)?  Maybe use workarounds for the time being and when they finally decide to take the plunge of converting to IPv6 completely most people will have compatible equipment by then, or am I wrong about that?

If so, I can understand where they're coming from, it's obviously not gonna be as bad as the media is/will make it out to be.  As with everything.

Looking forward to the newspapers headlines when the IP addresses actually run out (March 2011 thereabouts I think) :)

---

### Post by sydbat on 2010-12-04
> **Sporkman said:**
> There was a lot of back-end legacy code, though, that encoded only the last two digits of the year. These were not modern windows systems.Well...most of the windows boxen were 95 or NT. Of course, the Apple boxes (there were only a couple) did not need the "Fix".

---

### Post by juancarlospaco on 2010-12-04
On Sovietic Russia you Surf the Internet by the MAC address of the Webserver  :D

---

### Post by fontis on 2010-12-04
I think ISP's have been aware of this problem for a very long time, and they've taken steps to prolong the life of IPv4.

I mean just look at dynamic ip adress' and how isp's use their specific ip's to rotate amongst the subscribers. But the inevitable problem lies within the fact that there will come a time when they can't accommodate ALL connections at once, thus the internet becomes limited access. The question then is, will the prices increase and the services rotate more into a "high-pay-to-use" service? 

I'm not so sure that the transition to IPv6 will come "so easily", considering the problems that will occur in an immediate switch. 
But well, time will tell.

---

### Post by czr114 on 2010-12-04
The Internet will not stop growing.

The IPv4 exhaustion fears are being overplayed. Yes, they're constricting, and they will eventually run out. We need to move to 6.

That being said, there is an enormous amount of public IPv4 allocated but unused or allocated and wasted.

We're not going to wake up one day to find IPv4 gone, the Internet shut down, and dogs and cats living together.

As exhaustion approaches, addresses will first be recycled and scavenged.

---

### Post by alexan on 2010-12-04
[Internet will crash](http://www.youtube.com/watch?v=z4vDClhnJjs)


PS: don't procrastinate your backups!

---

### Post by Dustin2128 on 2010-12-04
> **fontis said:**
> I think ISP's have been aware of this problem for a very long time, and they've taken steps to prolong the life of IPv4.

I mean just look at dynamic ip adress' and how isp's use their specific ip's to rotate amongst the subscribers. But the inevitable problem lies within the fact that there will come a time when they can't accommodate ALL connections at once, thus the internet becomes limited access. The question then is, will the prices increase and the services rotate more into a "high-pay-to-use" service? 

I'm not so sure that the transition to IPv6 will come "so easily", considering the problems that will occur in an immediate switch. 
But well, time will tell.
Something about the way you put that reminds me of this south park episode:[http://www.southparkstudios.com/full-episodes/s12e06-over-logging](http://www.southparkstudios.com/full-episodes/s12e06-over-logging)

---

### Post by juancarlospaco on 2010-12-04
With IPv4 only, if you dont have more address space, you CANT grow up.
*Redistributing addresses is not growing*
:)

---

### Post by czr114 on 2010-12-04
> **juancarlospaco said:**
> With IPv4 only, if you dont have more address space, you CANT grow up.
*Redistributing addresses is not growing*
:)
Redistributing or making better use of addresses frees up more time for a smooth transition to 6. The Internet can grow by better use of what it already has while engineers are busy implementing the next path forward.

---

### Post by fontis on 2010-12-04
> **Dustin2128 said:**
> Something about the way you put that reminds me of this south park episode:[http://www.southparkstudios.com/full-episodes/s12e06-over-logging](http://www.southparkstudios.com/full-episodes/s12e06-over-logging)

Classic!! :D
I hope I don't end up driving towards California for a signal though... will be quite the drive from Europe... :P

---

### Post by lemming465 on 2010-12-04
Y2K was a non-event **from the point of view of the consumer**.  However, speaking as someone who does system administration and in the past application development, in corporate IT shops Y2K **was a very big deal indeed**.  Remember that 90-95% of software is in-house custom application code, most of which was wrong, and had to be fixed.  We were still tripping across occasional Y2K bugs as late as 2004.  The federal government still has some non-compliant systems 11 years later, if you can believe it.

---

### Post by lemming465 on 2010-12-05
IPv4 exhaustion was accurately predicted in 1990, when the internet only had about 100k hosts.  This was one of the main drivers behind creating IPv6.  The first IPv4 crisis was in 1993 when class A/B/C routing ran out of subnets.  All of the routers on the internet were re-engineered for CIDR (variable length subnets), and in '94 we broke the peer-to-peer model the internet was designed on, and introduced private addresses and NAT.  The trio of CIDR, RFC-1918 addresses, and NAT staved off the IPocalypse for another 17 years, which is surprisingly long.

IPv6 abolishes NAT - if the IETF and IAB have their way - and uses 128-bit addresses with a 64:64 split between subnets and hosts.  We write IPv6 addressess as 8 colon-separated parcels of 4 hexadecimal digits, do DNS lookups for AAAA records instead of A, and reverse lookups under ip6.arpa instead of in-addr.arpa.   IPv6 radically overhauls ICMP, merging in ARP and IGMP functionality as *neighbor discovery* and *multicast listener discovery*.  DHCPv6 is controlled by the now-required ICMP *router advertisements*, and often defers to *stateless address autoconfiguration*, where the router advertisement specifies the network prefix and default gateway address, but the host configures it's own host part of the address, either derived from its ethernet address or randomly.  The IPv6 substitute for private IPv4 addresses is the *unique local addresses* (FC::/7).  IPv6 also abolishes broadcast, instead requiring multicast.

End users running web browsers (ISO network model layer 7) can't tell the difference between IPv4 and IPv6 at network layer 3; we're preserving the major architecture of the internet.  We still use HTTP, SMTP, etc; we still use TCP and UDP at layer 4, we still use IEEE 802.whatever (ethernet, wifi, wimax, bluetooth, ...) at layer 2, and so on.  Autonomous systems (routers under the control of a single entity) still peer at internet exchange points using BGP, the *border gateway protocol*.  We just swap out IPv4 at layer 3 and swap in IPv6.   Layer 3 is where IP packet addressing and routing happens.  IPv4 and IPv6 don't interoperate; they coexist just the way IPv4 did with IPX (Netware) or Appletalk or DECNET.

IPv4 exhaustion happens in stages.  First IANA runs out of unallocated /8's.  That may happen any time in the next 3 months. That is the time when the Wall Street Journal, New York Times, Le Monde etc. will run front-page articles and all the CEO's will panic. Second, the 5 regional internet registries (ARIN, RIPE NCC, APNIC, LACNIC, AFRINIC) run out.  APNIC will run out in 2011, the rest in 2012 or 2013.  Third, ISP's run out; this will start happening in Asia in 2012 and be worldwide by 2014.  Fourth, organizations looking for new address space can only get IPv6, because there is no more IPv4.  This already happened if the organization is looking for *big* subnets; e.g. APNIC will only be allocating /22's in 2011.

IPv6 deployment is currently spotty.  100% of the tier-1 internet backbone is dual-stack and has both IPv6 and IPv4.  However, only about 20% of the middle mile (ISP's, major web sites) is v6-enabled, and only about 1% of end-users are on it in 2010.  Some European ISPs such as free.fr or xs4all.nl are fully dual-stacked for all customers already.  We're already on year 2 of a 7-year dual-internet interregnum, where there are separate IPv4 and IPv6 internets that don't talk to each other very well.  Something like 200 Chinese universities and 18 major Chinese cities are IPv6-only already.  China Telecom, the world's largest ISP, will start phasing out IPv4 in 2015. 

IPv4 doesn't stop working just because the address pool is fully depleted.  If you have IPv4 now, you can continue to use it for quite a while longer, probably through 2020.  Expect the price of public IPv4 addresses to rise sharply; we currently have about 5 billion IPv4 devices chasing 4 billion IPv4 addresses, headed by 2020 for around 22 billion devices.  Historically there was no economic incentive to deploy IPv6 prior to IPv4 exhaustion; however, once IPv6 is universal and dominant, probably in 2017, there is a very strong incentive for tier-1 ISP's to ditch IPv4, since IPv6-only is kinder to backbone routers than IPv4+IPv6 by a factor of about 18x.  However, the last IPv4 device probably won't be retired until 2036 or so; its simply that after 2020 legacy IPv4 devices will have to use IPv6 tunnels for transit.  This is already happening for v6-heavy rollouts using *dual-stack-lite*, where you get a public IPv6 address, IPv6-only transport, and a private IPv4 address that tunnels to a so-called carrier-grade NAT device at your ISP.

What IPv4 exhaustion *means* is that new stuff is going to have to support IPv6. Even in the US this includes 4G smartphone rollouts, the electrical smartgrid, etc.  In India and China it's going to include the next 2 billion new internet users. World-wide it's going to include the next 4 billion smartphones; we currently have 5 billion active cellphones, but only 10% IP-enabled so far.  There will be a gradually increasing number of IPv6-only servers and services; eventually you will actually prefer IPv6 to IPv4, perhaps as soon as December 2014.

All current computer operating systems (Windows 7, any recent Linux, Mac OS-X 10.6.5, AIX, Solaris, HP/UX, ...) already support IPv6.  Most current smartphone operating systems (iOS 4, Android, windows phone 7, symbian, blackberry, ...) also already support IPv6.  So on the consumer side, once your ISP offers native IPv6, you can start using it as soon as you upgrade your broadband modem and wifi router to newer models or newer firmware that supports it.  Expect your ISP to start offering IPv6 in 2011 or 2012.  Currently about 85% of our planet's ISP's are working on IPv6 rollouts, including all of the biggest ones.

*Don't buy any new network equipment which doesn't support IPv6*.  For cable modems, this typically means DOCSIS 3.0, although some recent DOCSIS 2 modems can support IPv6.  DSL modems mostly don't support IPv6 yet, though the forthcoming "X" specification is about to change that.  It will probably be 2013 before the last IPv4-only wifi routers disappear from the market; in 2011 you'll have to shop carefully to find IPv6 support.

Businesses should support IPv6 at their border service as soon as possible, preferably by 2012. This is not too hard; it mostly means adapting web applications to cope with IPv6 for sessions, cookies, log files, etc.  They don't have to rip IPv4 out of their backend; if the web server still talks to the app server over IPv4, and the app server to the database tier over IPv4, that's OK for now.

Bleeding edge types can use tunneling technologies such as *6in4*, *6to4*, or *Teredo* to experiment with IPv6 right now, even before their ISP offers it.  Respectively, see e.g. [hurricane electric]("http://www.tunnelbroker.net"), [anyweb's nifty tun6to4 script]("http://www.anyweb.co.nz/tutorial/Linux6to4Host"), or install the *miredo* client.

Examples of content providers in the US who are already IPv6-enabled include Google, Youtube, Facebook, and CNN.

---

### Post by LowSky on 2010-12-05
Good thing i'm backing up the internet onto my backup harddrive.

People worry about way too much. People worried when they ran out of phone numbers.. all they did was add more numbers.

people worried about y2k... nothing happened even when code wasn't fixed, things worked just fine.

How about you worry about real issues like the people who have no food or clothes in your town. Worry that your local school somehow keeps raising taxes and yet the kids are losing programs like music, science and field trips.. how does that equate? 

How about worrying about super volcanoes or fault lines, or metorites or aliens who want to use our planets for resources and kill us all.


Just saying worse things to worry about than not being able to torrent the next big movie release.

---

### Post by Red_Steve on 2010-12-05
Question: If my ISP would offer me "native IPv6" in the near future, having the fact in mind that both protocol versions don't talk to each other, wouldn't that mean I would be barred from ipv4 only services? 

There is this dual stacking which uses both protocols at the same time, whichever the other end of the request offers. Is this part of "native IPv6"?

---

### Post by 3rdalbum on 2010-12-05
> **Red_Steve said:**
> Question: If my ISP would offer me "native IPv6" in the near future, having the fact in mind that both protocol versions don't talk to each other, wouldn't that mean I would be barred from ipv4 only services?

I think the connection would time-out and the request would be re-sent over IPv4.

---

### Post by 3rdalbum on 2010-12-05
> **LowSky said:**
> People worry about way too much. People worried when they ran out of phone numbers.. all they did was add more numbers.

That's the plan for IPv6 as well, but ISPs and device manufacturers are really dragging their feet on it. I hated the whole "Elevators are going to explode" predictions associated with Y2K, but in the end it put the pressure on every software developer to update their code (even custom-written code) to be compliant. We need the same Y2K hysteria to actually force things to be done.

---

### Post by RiceMonster on 2010-12-05
> **sydbat said:**
> **True story - working in an office in 1999, and the IT guys were scheduled to "fix the Y2K problem". I just went in and changed the Windows time settings. When the IT guy came in and loaded his "special CD that would fix the problem", the pop-up read something like "this computer is already compliant". The company had spent untold amounts of money on the software and training. All because of media hype****.

In places running 30 year old COBOL programs, the changes were even more. We're talking thousands of dates in the double digits that needed to be converted to 4 digits.

---

### Post by lemming465 on 2010-12-05
If your ISP offers you native IPv6, your dual-stack ubuntu box will simply do both.  Your next question is, of course, when you try to visit some internet peer using some application protocol like HTTP or FTP or whatever, which network transport will be picked?  The full answer to that is rather complicated (see [RFC 3484]("http://tools.ietf.org/html/rfc3484") for 18 rules on picking source and destination IP addresses in a dual-stack environment, plus [RFC 5220]("http://tools.ietf.org/html/rfc5220") for further analysis of the corner cases).  Today let us go for the short answer:

(1) Your DNS resolver will look for both A (IPv4) and AAAA (IPv6) addresses for a host name.
(2) If you only get one kind of answer, IPv4 or IPv6, you use the corresponding protocol.  What else could you do?
(3) If you get both IPv4 and IPv6 addresses as possible destinations, the OS prefers native sources to tunneled, so even RFC-1918 IPv4 will have priority over 6to4 (2002::/16) or Teredo (2001:0::/32) IPv6 prefixes.
(4) If both you and your destination are dual-stack native, we march bravely into the IETF's future and prefer IPv6.

Naturally, you have two layers of possible overrides to the default policy.  The first is to instantiate different rules in /etc/gai.conf, which controls the address sorting behavior of getaddrinfo(3).  The second is that you can generally force commands like dig, nc, curl, traceroute etc. to use a particular protocol and particular interface.

In general, it will *just work*, and you don't have to do anything special.  Currently between 0.2% and 0.4% of internet clients have broken IPv6 transport, so most major content providers are using different DNS names for v4 and v6, e.g. the [www.google.com](www.google.com) web site is IPv4 only (unless you make special arrangements with them), while ipv6.google.com is IPv6 only.  In the long run, say 2014 and beyond, most internet sites will simply do both.  An example of that future trend is [Hurricane Electric]("http://ipv6.he.net"), the planet's most aggressive IPv6 peering ISP.

FYI, the syntax for embedding an IPv6 address in a URL is to put in in square brackets [].  E.g. if you install the *miredo* package,```
$ host ipv6.he.net
ipv6.he.net has address 66.220.2.75
ipv6.he.net has IPv6 address 2001:470:0:64::2
```will show you two possible IP addresses, one v4 and one v6.  Try visiting > [http://ipv6.he.net](http://ipv6.he.net)
[http://66.220.2.75/](http://66.220.2.75/)
[http://[2001:470:0:64::2]](http://[2001:470:0:64::2])and it will tell you which protocol you used each way.

---

### Post by Red_Steve on 2010-12-05
What about ISPside NATs? would they be able to tunnel a request from a ipv4 user to an ipv6 host thus mitigating the inability to communicate between those two protocolls?

---

### Post by miegiel on 2010-12-05
Excellent posts ([1]("http://ubuntuforums.org/showthread.php?p=10200863#post10200863"), [2]("http://ubuntuforums.org/showthread.php?p=10202842#post10202842")) **lemming465**

I guess this thread can be marked as solved now.

---

### Post by lemming465 on 2010-12-05
NAT has interesting and controversial roles to play in the IPv4 to IPv6 transition.  

There has to be some kind of NAT44 for a while, as (a) we are heavily dependent on it now (b) in the *dual-stack-lite* scenario, a native IPv6 client gets legacy v4 access via a v4-over-v6 tunnel to a carrier-grade NAT44 device at the ISP.  In this case you'd want to run any broadband modem or wifi router/firewall in transparent mode, as NAT444 (two layers of NAT) is horrible, both from a performance point of view and a protocol fixup point of view.

NAT64, where a v6-only client wants to talk to a v4-only server, is marginally possible, at least for simple TCP connections such as HTTP or SMTP.  Multichannel protocols like FTP or streaming multimedia may suffer badly.  The Chinese draft "IVI" protocol (a roman numeral pun on 4 and 6) shows how if you control both the DNS resolver and the 6-4 gateway, it can sort of work.

NAT46, where a v4-only client is trying to access a v6-only server, is hopeless.  There is an entire RFC [deprecating NAT-PT]("http://tools.ietf.org/html/rfc4966"), the most famous NAT46 try, mostly for generic NAT reasons.  The real killer problem is that a v4-only client only makes DNS A queries, while a v6-only server only has AAAA addresses.  This means that the NAT46 gateway has to fake a non-existent A record for the server.  Unfortunately, it turns out to be impossible to do that reliably for large numbers of clients.

The IETF has an agenda to return to the peer-to-peer internet of the 1980's, before IPv4 address shortages led to NAT, and is refusing to even define NAT66. One problem with NAT is that it pretty much prevents any protocol innovation, as the installed base takes about 10 years to turn over.  In the meantime it would lack support for application level fixup for the new protocol.  This creates an insane hurdle for any new protocol to surmount.  It also makes it much more expensive for new applications such as multi-player games or videoconferencing to be deployed, because they have to be designed and implemented to evade the limitations of the existing installed NAT base.

From a consumer point of view in the developed world, most of us are behind NAT44 devices, with one public outside IP address on our broadband modem.  It's not hard for an ISP to add near-native IPv6 support, see e.g. [6rd]("http://tools.ietf.org/html/rfc5569").  So the developed world home users should deploy dual-stack clients such as windows 7 or Linux, expect their ISP to add v6, and run with NAT44 on IPv4 and native IPv6 (no NAT).

Smartphones and BRIC countries are going to have to go with *dual-stack-lite*, where the client has a no-NAT public IPv6 address, IPv6 transport, and NAT44 shared at an ISP gateway.  The problem being that there is a legacy IPv4 network to access, but not enough IPv4 addresses to give each client its own, hence the need for sharing v4 at the ISP.  You can probably put 3000-4000 users behind a single ISP NAT44 address.

So remember, native IPv6, no NAT.  At most one layer of NAT44, either at home (with a dedicated personal public v4 upstream address), or at the ISP (with a shared v4 address).  Dual-stack clients only, to avoid trying to translate between the v4 and v6 IP protocols.

---

### Post by Red_Steve on 2010-12-05
So this means I would be fine with an ipv4 LAN as long as the router is providing a NAT44 and is dual stack enabled (like with 6to4 etc)?

Or in other words : My LAN is currently IPv4 based. I would go buy an IPv6 capable router. Do I have to convert my LAN to IPv6 too or does the NAT and some form of tunneling faciliate on demand connections to IPv6 adresses on WAN? (as long as the ISP wouldn't provide native IPv6.)

Sorry if I abuse ths threat for those personal questions but as the topic is on the table and I don't quite grasp the whole aspects for me as an end user I'm really interested in clearing up any confusions.

---

### Post by lemming465 on 2010-12-05
> **Red_Steve said:**
> So this means I would be fine with an ipv4 LAN as long as the router is providing a NAT44 and is dual stack enabled (like with 6to4 etc)?
If you are only trying to access IPv4 services, and your ISP is still offering you a public IPv4 address, you can keep using IPv4-only from a personal NAT44 device for the next decade or so. You don't have to be in any hurry about IPv6.  It will probably be 2014-2016 before there is enough IPv6-only stuff that you might want to budge off IPv4-only.

Yes, you can tunnel IPv6 over IPv4 through a single personal NAT44 device.  "6to4" happens to require a public IP address, so you couldn't use that, you'd have to use 6in4 (e.g. with a tunnelbroker) or Teredo (not recommended).

> **Red_Steve said:**
>  Or in other words : My LAN is currently IPv4 based. I would go buy an IPv6 capable router. Do I have to convert my LAN to IPv6 too or does the NAT and some form of tunneling faciliate on demand connections to IPv6 adresses on WAN? (as long as the ISP wouldn't provide native IPv6.)
Your LAN devices such as PC's are mostly dual-stack, and can do either IPv4 or IPv6.  Use whichever you like.  One doesn't generally "convert" to IPv6; one "enables" IPv6 as a second available protocol, keeping IPv4 too.  While Ipv4 and IPv6 don't interoperate, they do coexist just fine.

To use native IPv6 directly with an IPv6 peer somewhere on the IPv6 internet the entire path has to be IPv6-enabled.  That means your host, your wifi router, your broadband modem, the DSLAM or CMTS upstream at your ISP, the ISP's routers, and the ISP's BGP peers.  Similarly on the far end.  You can see why there isn't yet a lot of native IPv6 traffic.  

Your ISP is probably 6-18 months away from providing near-native "6rd" IPv6, which is tunneled between your broadband modem and an ISP gateway, but looks native to your clients.  It might take your ISP 30-48 months to provide direct, native IPv6 end-to-end for their entire customer base. 

Most of the tunneling technologies like 6to4, 6in4, or Teredo are optional; you can turn them on or off.  Traffic from your clients would normally take IPv4 unless you were trying to get to an IPv6-only resource, and only if you had the tunnel turned on.  You can arrange to have the tunnels turn on automatically when an Ubuntu PC boots if you want that.

In the short run, while the internet is still mostly IPv4, the people with the painful problem are the ones who only have IPv6, e.g. in the US as of today Verizon "4G" LTE devices. What they actually have is dual-stack-lite, with carrier NAT44 to reach the legacy IPv4 internet.  In the long run, we'll all want IPv6.  When we all have it, around 2015-2017, we'll stop worrying about IPv4.  Transitioning to IPv6 is more like the transition from analog to digital TV than like Y2K.  There is no particular day when IPv4 stops working, at least not anytime soon, and we can take several years to work through it.
Existing IPv4 users are in good shape.  It's the new stuff that is going to be IPv6-only.

> **Red_Steve said:**
> ... I don't quite grasp the whole aspects for me as an end user I'm really interested in clearing up any confusions.
I'm an unofficial IPv6 outreach guy at the University of Wisconsin - Madison; I'm trying to help dispel confusion about a large and complicated topic.  Trying to understand the differences between v4 and v6 is currently puzzling a planet full of professional network engineers, never mind typical computer network users.  So you are quite welcome.

---

### Post by Sporkman on 2010-12-05
128 bit address space (vs the 32 bit for ipv4) should give plenty of breathing room for many years to come, that's for sure.

---

### Post by Windows Nerd on 2010-12-05
Though Lennings covered much of the information earlier, here is a great interview about ipv6 if you have just less than an hour to spare. These guys really know their stuff. The guy interviewing is a sysadmin, and also knows a lot about hacking, in both senses of the word. He sometimes acts a bit weird though, but that's what a geek does, right?

[http://www.youtube.com/watch?v=cl4cEbPayek](http://www.youtube.com/watch?v=cl4cEbPayek)

---

### Post by Red_Steve on 2010-12-05
Thank you, lemming465 for your answers.

I was kinda shocked as I read about the fact that we are running out of free ipv4 adresses to allocate. My router is ipv4-only yet and Ubuntus ConnMan implementation only supports staticIPv6 for 10.10 for now (as of 0.55 AFAIK) so I felt really unprepared for IPv6. But after doing much more research it seems like I will be fine with upgrading my router to be IPv6 capable (around here in germany that would most likely mean bying an AVM Fritz!Box device which is capable of 6to4 and nativeIPv6 additional to "regular" IPv4) and just wait for Ubuntus Connman to be updated for the whole IPv6 fun. If all things fail I will have to deal with staticIPv6 and what it does mean for me, my ubuntu box and my smartphone (not to mention my GF and her gadgets ^^).

Once again I greatly appreciate your efforts, lemming465.

---

### Post by lemming465 on 2010-12-05
> **Sporkman said:**
> 128 bit address space (vs the 32 bit for ipv4) should give plenty of breathing room for many years to come, that's for sure.

Yes, though not quite as much as the more breathless press reports would have you think.  The design goal was 2^40 subnets organizing 2^50 hosts, combined with a desire for 64-bit aligned data structures to accommodate modern CPU's.  Fantasies of 2^128 hosts, the 340 undecillion usually touted, are grossly exaggerated.  The expectations are set out in places like [RFC 3587]("http://tools.ietf.org/html/rfc3587") and [RFC 3177]("http://tools.ietf.org/html/rfc3177").  Roughly speaking, the IETF gets the upper 3 bits for controlling the address family.  Currently they use only 0=mapped addresses, 2=global unicast, and E=special purpose.  The various layers of internet registries and ISP's get the next 29 bits; anyone large enough to be an autonomous system should expect a /32.  Large ISP's can get more; the US DOD nabbed a /13.  Ordinary organizations, say your local sandwich shop, should expect a /48.  Home users, customers of ISP's, might "only" get a /60.  All subnets except perhaps point to point links are expected to be exactly /64 at the (virtual) LAN.  

Note that the FC00::/7 [unique local address]("http://tools.ietf.org/html/rfc4193") for IPv6 which replace the [RFC 1918]("http://tools.ietf.org/html/rfc1918") private addresses of IPv4 preserve this expected 48-bit network prefix + 16-bit local subnet + 64-bit host part structure.  That's why the FEC0::/10 site local addresses got deprecated; those didn't.  Yes, in IPv6 your organizational, internal, private *unique local* addresses will let you preserve the exact same subnet and host allocations you are using with your global public addresses.  Is it any wonder google called engineering IPv6 networks **refreshingly simple**, a sentiment I share.  Compared to the mess that we have with IPv4 fragmentation, it's *so easy* when all your subnets are the same size, none of them are too small for the number of hosts you want to put on them, and it only takes one route to cover entire buildings.

---

### Post by undecim on 2010-12-06
We would have to switch to IPv6.

Some services might keep IPv4 for legacy use

---

### Post by Red_Steve on 2010-12-06
As far as I understand it, not "we" would have to switch then but newer Servers and thus newer webcontent and they need some sort of support to be reachable for the IPv4-Internet. There seems to be some kind of plan to solve this situation by first increasing the size of IPv isles of internet in the ocean of IPv4 then have like seas of ipv4 in ipv6 and finally have isles of ipv4 in an ocean of IPv6 by switching to different routing methods one after another until finally IPv4 would be gone. The estimations say this would btw not sooner happen than 2020, being more conservative in this estimation is advisable. 

Currently with tunneling services you are good to go with the IPv6 internet. That's as far as I could gather information.

---

### Post by cprofitt on 2010-12-06
The single biggest problem I have had is finding an IPv6 capable home router... any suggestions from the knowledgeable folks here?

---

### Post by Paqman on 2010-12-06
Nothing will happen. More widespread use of NAT will skirt around the problem until IPv6 eventually staggers onto the scene in a few hundred years.

---

### Post by juancarlospaco on 2010-12-06
> **cprofitt said:**
> The single biggest problem I have had is finding an IPv6 capable home router... any suggestions from the knowledgeable folks here?

a Linux box.

---

### Post by Red_Steve on 2010-12-06
AVM Fritz!Box is capable as Linksys Routers by Cisco Systems

---

### Post by cprofitt on 2010-12-06
> **Red_Steve said:**
> AVM Fritz!Box is capable as Linksys Routers by Cisco Systems

Do you know which models?

---

### Post by Red_Steve on 2010-12-06
Fritz!Box at least 3270 and bigger with newest firmware

[http://www.sixxs.net/wiki/Routers](http://www.sixxs.net/wiki/Routers) is kinda good ressource

---

### Post by lemming465 on 2010-12-06
> **Paqman said:**
> Nothing will happen.
In the sense that the existing IPv4 internet will keep running, true.
> More widespread use of NAT will skirt around the problem
Reading accounts of the NANOG-50 panel discussion on IPv6 transition held in Atlanta at the beginning of October, 100% of US ISP's were committed to rolling out native IPv6, and 0% were willing to commit to carrier-grade NAT. Since native v6 is better for customers, *and* is cheaper for ISP's, *and* has a shorter deployment timeline than CGN, *and* has lower risks than CGN, *and* is better long-term strategy than CGN, this is hardly surprising.
> until IPv6 eventually staggers onto the scene in a few hundred years.
A certain cynicism is pardonable after watching IPv6 lurk off-stage for 13 years; prior to IPv4 exhaustion the economics were against it.  I think it has now made it from "stagger" to "lurch", and we're only talking hundreds of weeks, not centuries.

---

### Post by Red_Steve on 2010-12-06
I'd say hundreds of weeks is still enough time to relax about this topic and to take your time to tackle this issue with care and good preparation. Nothing to hurry about and roll out some halfhearted hacks like NATs on every corner.

---

### Post by Paqman on 2010-12-06
> **lemming465 said:**
> 100% of US ISP's were committed to rolling out native IPv6, and 0% were willing to commit to carrier-grade NAT.

That's good news. Everybody has been dragging their feet on IPv6 migration for long enough. Let's hope they pick up the pace.

---

### Post by lemming465 on 2010-12-06
> **Red_Steve said:**
>  ... Nothing to hurry about ...
It depends on who you are.  

For *consumers* this is exactly right; their best move is to sit on their hands for two years and wait for the availibility and quality and prices of dual-stack IPv4+IPv6 modems and wifi routers to improve.  Since there are not yet a lot of IPv6-only services out there, business don't have to be in a hurry to roll out IPv6 clients to all their workers, either. In the US our federal government deadline for agencies to v6-enable their intranets is September 2014.  Bleeding edge technology enthusiasts are welcome to move faster, if they wish.

However, there are 3 categories of folks who are, or should be, in a hurry on IPv6.  (1) *ISP's* need to offer it to their business customers immediately.  They shouldn't dawdle too much on their consumer end-users, but we're lower priority at the moment. (2) *Businesses* need to dual-stack enable their outward facing services (web sites, e-mail, DNS, ...) as soon as possible, preferably in 2011 or early 2012.  (3) Large new deployments such as 4G cellphone data plans, electrical smartgrid, etc. can't get enough v4 to deploy, and perforce must use v6.  E.g. for Verizon in the US (97 million customers), IPv6-mostly "dual-stack-lite" LTE laptop dongles started going live **yesterday**.

Businesses with IPv4-only web sites are about to go the way of the buggy-whip manufacturers as automobiles replaced horses a century ago - extinct.  Just like businesses without web sites started losing out to those with network access.  In US video rentals, Netflix streaming is 20% of the peak evening hours downlink bandwidth, while video store mogul Blockbuster is in chapter 11 bankruptcy reorganization.  Netflix is already IPv6 enabled, by the way.  IPv4-luddites beware!

---

### Post by Red_Steve on 2010-12-06
Yeah. My comment related to people like me. end-consumers.

Actually I went today to an ISP office and asked them about their plans on IPv6. The employees answer was like "uhm, we don't know what's in the pipe for us but come back in about two months"

As I told him that they might need to replace their provided ipv4only legacy uplink devices with new ipv6 capable ones he reacted quite shocked and uncertain.

---

