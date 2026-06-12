---
title: "I want firmware updates for at least 10 years.....Which router should I buy ?"
date: 2021-02-08
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2021-02-08
At the moment I am using a ISP provided 4G router but in future I plan to use cable broadband. I have used cable broadband in the past with a DLINK router. The problem with the Dlink router was the fact that it stopped receiving firmware updates after just 2 years. I tried to flash the router with DD-WRT but failed coz the router was not supported.

I am looking for a router which is (a)supported by DD-WRT & (b)will be supported for at least 10 years.

You guys may say that 10 years is too much expectation but its nothing in comparison to the frustration which occurs when a customer has to throw away a fully functional router just coz of security reasons.

---

### Post by CelticWarrior on 2021-02-08
Have you checked if it's supported by OpenWRT?

---

### Post by linuxyogi on 2021-02-09
> **CelticWarrior said:**
> Have you checked if it's supported by OpenWRT?

I did. It wasn't supported so I sold it at a cheap price.

---

### Post by mikewhatever on 2021-02-09
There is a [public list of supported devices]("https://wiki.dd-wrt.com/wiki/index.php/Supported_Devices"). The link is very easy to find.
Now, guaranteed 10 years of support from a community for free is a bit absurd.

---

### Post by mastablasta on 2021-02-10
here you get modem/wifi/router from ISP for 2 years - which is the period you sign up for. after that you can continue with the old or sign up for a new one. it comes in the price. not very eco friendly if you ask me and just like smartphone industry. anyway i signed up with them first in 2010 and so far i've changed it once as the previous broke. They provide firmware updates and the modem/router is actually made by local company (or at least they brand name it). anyway, i like the interface, and it gets the updates, so i don't plan a change yet. but i might need to change TV box that came with same subscription plan. while it still works (youtube and games don't but i never used those on TV), the remote is not good and they apparently no longer have the remote. you need to sign up to a new contract or use smartphone to change channels.

---

### Post by Shibblet on 2021-02-10
I personally use the Linksys WRT-1200AC.  Bought it about 5 years ago, and it's still running strong.  Firmware can be easily upgraded, or converted to DD-WRT or Gargoyle.  (I prefer DD-WRT)

---

### Post by TheFu on 2021-02-10
The only way I know to ensure long support for any router is to use an amd64 solution with replaceable components. Basically, a low-powered PC with as many NIC ports (get Intel NICs) as you need.  Then you can run the dd-wrt, openwrt, opnsense, pfsense, routing software as you like.  

No company or F/LOSS project is going to commit to any **specific** hardware created by some other vendor.  In 5 yrs, linksys may go out of business (unlikely).  But the future for Intel and AMD seems really solid.

In the consumer space, Asus will probably have the longest support due to an FTC ruling. 
[https://www.ftc.gov/news-events/press-releases/2016/02/asus-settles-ftc-charges-insecure-home-routers-cloud-services-put](https://www.ftc.gov/news-events/press-releases/2016/02/asus-settles-ftc-charges-insecure-home-routers-cloud-services-put)
To my knowledge, the companies that provide just 2 yrs of support (the list is very, very, long) haven't been smacked with FTC orders.

I have an APU2C4 router. There are newer versions available.  It is very DIY - we buy components to put it together.  [https://www.pcengines.ch/apu2.htm](https://www.pcengines.ch/apu2.htm) - to save yourself hassles, get all the hardware at once from the vendor.
* SBC
* Case (part of the thermal/cooling)
* PSU
* SSD/m-sata storage and any cables; do not use an microSD!

The apu4d4 SBC (single-board-computer) is very interesting to me, if I were in the market today.

If you want something less DIY, but with proven companies, I'd say either Ubiquiti or Microtik.
[https://www.youtube.com/watch?v=SianDqAQaR0](https://www.youtube.com/watch?v=SianDqAQaR0) - EdgeRouter X (beginner)
[https://category5.tv/shows/technology/episode/650/](https://category5.tv/shows/technology/episode/650/) multi-part series on Microtik

---

### Post by linuxyogi on 2021-02-11
Thanks everyone for the replies.
@TheFu
In my country a Dlink/Tplick/Netgear router costs about Rs 1500. I searched on Amazon.in using the term "apu4d4 SBC" I found nothing. Also in Indian market these SBC devices costs a whooping 10,000-11,000.
When you have time please help me out by searching for "apu4d4 SBC" on amazon.in (please use .in not .com).

---

### Post by TheFu on 2021-02-11
They aren't sold on Amazon to my knowledge.  I bought directly from PCEngines. It was shipped and arrived at my door 3 days later. 

> Dlink/Tplick/Netgear router costs about Rs 1500
There are reasons for the low-low price. If you have an old PC with 2 NICs, that can be a router.  Be certain to consider the cost of electricity to run it vs getting a new purpose-built router.

Again, make a list of what is important and stuff you do not want then search for things that are either from reputable, long-term patched HW vendors, or that are amd64 computers with multiple NIC ports.  This will get you the longest lifespan hardware. The AMD/Intel 64-bit systems can usually run dd-wrt, openwrt, or you could build a router using Ubuntu Server : [https://arstechnica.com/gadgets/2016/09/the-router-rumble-ars-diy-build-faces-better-tests-tougher-competition/](https://arstechnica.com/gadgets/2016/09/the-router-rumble-ars-diy-build-faces-better-tests-tougher-competition/)

---

### Post by CelticWarrior on 2021-02-11
> [COLOR=#000000]Be certain to consider the cost of electricity to run it vs getting a new purpose-built router.[/COLOR]


Oh yes... The difference can be 10x to 20x more. Old PC = comparatively inefficient.

---

### Post by linuxyogi on 2021-02-12
I have made my desicion. I am going to assemble a new desktop myself for this purpose. I will pay the extra electricity bill.
I am going to use OPNsense. OPNsense was suggested to me by TheFU on a different thread of mine.

@TheFU
One last question. I want to know for how long is a release of OPNsense supported ? How many years ?
I tried Google & found [the WIKI]("https://en.wikipedia.org/wiki/OPNsense") but I cant find that particular information.
If its supported for at least 5 years like Ubuntu LTS I will be more than happy.

---

### Post by TheFu on 2021-02-12
OPNsense is a fork of pfSense. It is actively developed. If you are on x86-64 hardware, then you won't lose support. Moving from release to release isn't hard. It is a F/LOSS project, so there isn't any guaranteed support period, just a target. [https://opnsense.org/about/road-map/](https://opnsense.org/about/road-map/) says they try to have 2 releases a year. It also shows their release history going back to 2015.  

If you need 100% certainty, using F/LOSS isn't what you want.

---

### Post by linuxyogi on 2021-02-12
> **TheFu said:**
> OPNsense is a fork of pfSense. It is actively  developed. If you are on x86-64 hardware, then you won't lose support.  Moving from release to release isn't hard.

That's good enough for me. 

> **TheFu said:**
>  If you need 100% certainty, using F/LOSS isn't what you want.

I always prefer open source software. I don't even use closed source web browsers like Google Chrome or Opera. Using a proprietary firewall solution is absolutely unacceptable.

This thread is Solved.

---

### Post by TheFu on 2021-02-19
Just posted: [https://www.schneier.com/blog/archives/2021/02/router-security.html](https://www.schneier.com/blog/archives/2021/02/router-security.html)
Plenty of warnings about Linux-based routers using very old kernels that have over 233, old, known, attack problems.

---

### Post by kevdog on 2021-02-20
I'd consider pfsense of opnsense.

---

