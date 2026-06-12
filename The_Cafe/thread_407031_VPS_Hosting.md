---
title: "VPS Hosting"
date: 2007-04-11
forum: The Cafe
---

### Post by v8YKxgHe on 2007-04-11
Hey, 

I'm thinking of switching off shared-hosting and onto VPS hosting, I would go direct to Dedicated but that's a bit expensive for me at the moment. 

I'm wondering what people think about VPS hosting? Is it good to go with? I see plans that are pretty expensive and only offer around 256mb memory ... doesn't seem a lot to me. The whole VPS thing seems really 'messy' to me really, not sure if I should go with it or stick with shared, although I would like to have more freedom with my hosting, which VPS would offer.

So, what do people think of VPS and do you know of any good places to get it from?

Regards,

---

### Post by leona on 2007-05-02
Shame that no one has replied really, did you get any further with your research?

I know someone who went for webfusion vps, but are not happy with they're level of support, takes 3 weeks to just change the system clock for example!

I would like to do this too, I currently have a shared reseller account with 25-30 sites, we're bursting out of our current host and they are expensive, I like the idea of VPS, but what concerns me is what level of support I'd get, who'd be 'patching' the software for example, backup/restores, uptime all those sort of things.

Well if anyone does have any expeience of these (I'd like a UK one if poss) please post it up here, good or bad :)

---

### Post by wcbzero on 2007-05-09
If you guys are still looking give [http://vpslink.com](http://vpslink.com) a try. They are located in Seattle, WA, USA, and I currently have two VPS's with them. They allow you to choose you distro and have great support.

---

### Post by mmxbass on 2007-06-01
> **wcbzero said:**
> If you guys are still looking give [http://vpslink.com](http://vpslink.com) a try. They are located in Seattle, WA, USA, and I currently have two VPS's with them. They allow you to choose you distro and have great support.NO. Their support is GARBAGE. Everything.... EVERYTHING takes hours upon hours for these people. You ask for a simple reboot because the CP isn't working for the 15th time and it's half a day before they get to it.

Byteshack: [http://www.byteshack.net/vps_hosting.html#packages](http://www.byteshack.net/vps_hosting.html#packages) offers more ram and more disk space for your dollar and still let you use Ubuntu server.

---

### Post by scottfinman on 2007-06-14
I'll second VPSLink being awful  - mainly s-l-o-w I/O (on the order of 3-8 seconds for a handful of MySQL reads) even on one of their higher end packages.

Definitely bandwidth issues or them putting too many accounts on each physical server. To be fair, their response to support requests have been quick.

Only VPS I've used that has been worse is Media Temple - even slower I/O and day-long waits for support.

Good experiences with BudgetDedicated.com - near-instant e-mail replies and the guys are available through IRC as well. Fast speeds (tenths of a second for the same PHP application that took multiple seconds above) on even moderate hardware. They are located in Europe, however, which, just due to the length of the lines involved, has to introduce some delay. They have a 7-day free trial that sets itself up in < 5 minutes with no credit card involved - definitely worth a try. It is the best VPS offering I have had experience with so far.

Also looking at Linode.com this very morning - looks like it has potential, but I cannot attest to their actual performance.

If you're looking to go beyond VPS to dedicated, m5hosting.com looks to be good as well - received prompt and thorough e-mail replies from the owner himself. It is a smaller operation, which I'm partial to. Again, however, I cannot attest to the actual performance yet.

---

### Post by scottfinman on 2007-06-14
Alright, can officially attest to Linode.com's performance - nice and fast for PHP scripts involving multiple MySQL read/writes, good support (I made use of IRC), with three datacenter's throughout the US.

From the East Coast of the US, it's about identical in speed to BudgetDedicated.com (based in Amsterdam).

What especially stands out is their advanced disk configuration options from your browser - can set partitions, so one could theoretically have multiple Operating System's on there and switch between them. Not anything I'd ever make use of, but points for fancyness.

I'm also told it's a rarity for VPS's to allow you to host an IRC Server for DOS reasons, which Linode.com does - though, not sure to evaluate this as a good or a bad thing.

At the very least, the basics are there better than any other VPS I've come across that's hosted in the US - it seems that they're not stacking up too many accounts on individual machines.

Anyone else have other VPS solutions worth looking into??

---

### Post by Leftblank on 2007-06-19
> **scottfinman said:**
> 
Anyone else have other VPS solutions worth looking into??

I've had a pretty good experience with [http://primaryvps.com/](http://primaryvps.com/) , it's a company based somewhere in the US, their customer support is outstanding; they've resolved various issues I used to have while being with them. The drawback is though that they don't offer Ubuntu, they do offer Debian 4 and CentOS 5 though, which should do pretty good as well.

One thing is to be remembered though, it's a hosting company for vpses aimed at hosting websites or (when you request approval) irc; their latency to the Netherlands isn't too great, I was unable to host a 2d MMORPG gameserver on it due to that, but for websites it'll do perfectly fine. 

For European fella's I'd recommend Strato, I've been with them for a little now and their performance is pretty good and their support is pretty decent too, the skill isn't always optimal, but they're willing to help and available through the phone nearly all day for free. No Ubuntu there either, but Debian 3.1 and SuSE 10.1 are available, you also get a Plesk account for 10 domains or so with them for free, which also saves some money.

[http://hostineuro.com/](http://hostineuro.com/) has some decent prices too (no experiences with them), which also goes for [http://www.hosteurope.de/produkte/VPS-Linux](http://www.hosteurope.de/produkte/VPS-Linux) (German) and [http://www.tektonic.net/unmanaged.html](http://www.tektonic.net/unmanaged.html) , with the last one being in the US and offering Ubuntu as well.

---

### Post by rvarnam on 2007-08-23
I can second the comments about WebFusion's poor customer service.  They have a great VPS product, at an amazing price.  But I've had 2 problems with their Plesk installation, and each has taken them 3 days to fix.

---

### Post by eukhost.com on 2007-08-24
VPS is an ideal solution if you have outgrown your shared hosting account but are not ready to move to a dedicated server right away. Virtual private servers bridge the gap between shared hosting and dedicated hosting, giving isolation from other customers of the VPS service in software terms but at a  less cost than a physical dedicated server.

---

### Post by senzafine on 2008-10-01
I've had really good luck with vr.org's Xen based vps.  Haven't needed anything from their customer support but the server has been up for 2 months so far (that's as long as I've had them).  I have pingdom checking uptime every 5 minutes.

---

