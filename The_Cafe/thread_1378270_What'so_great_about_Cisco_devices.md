---
title: "What'so great about Cisco devices?"
date: 2010-01-11
forum: The Cafe
---

### Post by PryGuy on 2010-01-11
Good day everyone!
I hear many system administrators are so very fond of the Cisco devices. But I've never touched it, so what so special about the Cisco stuff and why it's so great if so many people prefer it to *nix systems? Thank you in advance!

---

### Post by amitabhishek on 2010-01-11
Extreme &  Juniper products are much bette. Cisco brand gets better of the two.

---

### Post by steev182 on 2010-01-11
That's not really a reason why, I think to find out why Cisco as a brand is so well respected, you need to look at their history, even Wikipedia can show you this. But I think the reasons for Cisco being so successful are IOS and the hardware itself. They're well built, have lots of expansion ports and you get really good support (but you do pay for the support contract and you do find that their equipment is damn expensive!) also you will find that most companies over a certain size would be reluctant to entrust their networking or telephony to servers running linux or asterisk, however some companies like to look into Asterisk (which is a project I'd like to try at one point)

Wikipedia is always a nice place to find answers though :D

---

### Post by juancarlospaco on 2010-01-11
What devices?, routers?, Switch?

i think thats the Propietary protocols, like EIGRP,
but theres a OpenSource replacement for Cisco named Vyatta, uses OSPF.
Vyatta can be virtualized, cisco hardware is very expensive.

Quagga, multi-daemon program, can be installed on Ubuntu too, is the same used by Vyatta.

Vyatta CLI is like Cisco's, and Cisco's CLI is like *nix,
the PacketTracer 5.x software is nice for Learning purposes, 
but theres GNS3 (OpenSource) and its nice too.

I think that closed source/propietary things on Cisco sux.
Sometimes open source routing protocols created by people is better than Cisco's one,
in example B.A.T.M.A.N. can be better than original WRT firmware from Cisco.

Cisco have a nice eLearning program for became very skilled expert.

[If you want to use/learn with real Cisco devices for Free click here.]("http://packetlife.net/wiki/packet-life-community-lab/")
:)

---

### Post by PryGuy on 2010-01-11
Thanks for the answers, but comparing Linux and Cisco, can you tell Cisco is far more secure(stable/fast/you name it) or is it just a branding question?

---

### Post by steev182 on 2010-01-11
It depends, I know at the last company we had linux web servers with uptimes of 500+ days and cisco switches with uptimes of 500+ days too, but that is like comparing Apples with Oranges, you can't really.

---

### Post by PryGuy on 2010-01-11
That's what I think exactly. Any device can be hacked if it can be accessed via SSH for instance (correct me if I'm wrong). The question of security is the question of the system administrator's skills (if it's not Windows of course :)).

---

### Post by juancarlospaco on 2010-01-11
Linux--->Software
Cisco--->Software/Hardware*(both closed)*

Cisco software is very limited, but hardware is really nice, but too expensive,
sofware just do their job, thats it, both are *nix and stable, 
but Cisco is designed from scratch for these purpose, 
and can be fast compared to an generic Linux, 
Linux dont handle closed protocols, closed protocols are more smart ATM.

I love it if becomes Open Source and closed hardware, but seems impossible,
i sucessfully installed Linux on a Cisco router, but cant handle Serial lines.

Only Vyatta develop professional routing Linux devices ATM, any Linux can route traffic.
Theres a replacement for smaller Cisco devices named Freesco.

Security, UpTime, and such depends on Administrator skills, 
you can hang a Cisco switch using only Yersinia,
you can gain acces if Telnet is used on old Cisco devices using WireShark,
you can xploit unpatched vulnerability on a Cisco device.
:)

---

### Post by pwnst*r on 2010-01-11
Cisco - super reliable, great support, wide variety of hardware.  Yes it's expensive, but when it comes to your network hardware usually things are not cheap anyway.

---

### Post by juancarlospaco on 2010-01-11
> **pwnst*r said:**
> super reliable, great support, wide variety of hardware.

If you pay the same as the Cisco Support for a Linux Server, you will get great support too,
and you know its reliable and any hardware,
but Cisco its not direct competitor for Linux.

:)

---

### Post by Sef on 2010-01-11
> but Cisco its not direct competitor for Linux.


Linux routers and switches are a direct competitor to Cisco.

---

### Post by juancarlospaco on 2010-01-11
> **Sef said:**
> Linux routers and switches are a direct competitor to Cisco.

I know girl, but i mean... as i said:

Linux--->Software
Cisco--->Software/Hardware*(both closed)*

Linux itself dont build Hardware ATM.

And Linux devices are Layer 3 by default, 
what you mean for "Linux switch"?, 
you know a Linux distro to build a Switch, sounds interesting for me.
thank you in advance

---

### Post by pricetech on 2010-01-11
Nobody was ever fired for recommending Cisco.

---

### Post by Grenage on 2010-01-11
Aye, Cisco are unmatched when it comes to reliability.  Their kit is costly, but it's worth every penny.

---

### Post by Icehuck on 2010-01-11
> **Sef said:**
> Linux routers and switches are a direct competitor to Cisco.

What? Do you mean routers and switches made by other companies? Like HP using linux to make a router? Otherwise, Linux is no way a direct competitor to Cisco in terms of routers and switches.  Don't even try and claim that businesses are using generic linux boxes for their routers and switches.

---

### Post by Grenage on 2010-01-11
> Don't even try and claim that businesses are using generic linux boxes for their routers and switches.

We are...

---

### Post by juancarlospaco on 2010-01-11
[**-Click here to start Routing for Free**]("apt:/quagga")

:)

---

### Post by Icehuck on 2010-01-11
> **Grenage said:**
> We are...

Really? Ok, I have rackspace for a new 48 port switch. Fit me in a generic PC running linux into that space with 48 ports.

---

### Post by pwnst*r on 2010-01-11
> **juancarlospaco said:**
> If you pay the same as the Cisco Support for a Linux Server, you will get great support too,
and you know its reliable and any hardware,
but Cisco its not direct competitor for Linux.

:)

Why are we talking about servers?

---

### Post by juancarlospaco on 2010-01-11
> **Icehuck said:**
> Really? Ok, I have rackspace for a new 48 port switch. Fit me in a generic PC running linux into that space with 48 ports.

**These space is really Huge!**
You only need[ this, ]("http://www.vnetworkstack.com/")and the skills to use it.
*Just need space for a Virtual Network Stack file on an SSD or HD.*

*Virtualization is the future...*
:)

---

### Post by pwnst*r on 2010-01-11
> **Grenage said:**
> We are...

He probably meant big businesses and/or corporations ;D

---

### Post by Icehuck on 2010-01-11
> **juancarlospaco said:**
> **These space is really Huge!**
You only need[ this, ]("http://www.vnetworkstack.com/")and the skills to use it.
*Just need space for a Virtual Network Stack file on an SSD or HD.*

*Virtualization is the future...*
:)

Ok, so a company(not linux) selling hardware/apps is the competitor?

---

### Post by pricetech on 2010-01-11
> **juancarlospaco said:**
> *Virtualization is the future...*
:)

I wonder how quickly virtualization will go from being the "next big thing" to a "flash in the pan"

Or am I the only one who remembers the fuss over Thin Clients ??

---

### Post by Icehuck on 2010-01-11
> **pricetech said:**
> I wonder how quickly virtualization will go from being the "next big thing" to a "flash in the pan"

Or am I the only one who remembers the fuss over Thin Clients ??

Yeah, thin clients were they way to go! OMG we gotta have that setup! We have them in use but we still develop normal apps per usual.

---

### Post by koenn on 2010-01-11
> **juancarlospaco said:**
> **These space is really Huge!**
You only need[ this, ]("http://www.vnetworkstack.com/")and the skills to use it.
*Just need space for a Virtual Network Stack file on an SSD or HD.*

*Virtualization is the future...*
:)
and exactly how does one go about plugging 48 patch cables into this file ?

---

### Post by Icehuck on 2010-01-11
> **koenn said:**
> and exactly how does one go about plugging 48 patch cables into this file ?

You still have a rack in place, it's just apart of this thing. :P

Also want to point out that Vyatta is in part sponsored by Cisco so no it's not a competitor.

Vyatto does not make switches or virtualize switches.

---

### Post by koenn on 2010-01-11
> **pricetech said:**
> I wonder how quickly virtualization will go from being the "next big thing" to a "flash in the pan"

Or am I the only one who remembers the fuss over Thin Clients ??

with virtualisation, you can just rune the same things on less machines, an d you typically start with server virualization, so nothing changes on the user side. That's a transition thats far more gradual, and far more manageable, than having your entire environment switch to thin clients and server-based computing. 
And that's why virtualization is very likely a trend that will continue, while Thin Client was a hype - although it still is a suitable solution in some specific situations.

---

### Post by Grenage on 2010-01-11
> He probably meant big businesses and/or corporations ;D

Oof, belt shot ;)

The majority of our routing is handled by dedicated hardware boxes, but we've started implementing some nix units for handling client VPN's, public access points and other relatively small things.

---

### Post by pwnst*r on 2010-01-11
> **pricetech said:**
> I wonder how quickly virtualization will go from being the "next big thing" to a "flash in the pan"

Or am I the only one who remembers the fuss over Thin Clients ??

Not even close to being the same thing.  Corporations are all over virtualization and for good reason.  It saves money in the long run and it's easier to manage.

---

### Post by pwnst*r on 2010-01-11
> **Grenage said:**
> Oof, belt shot ;)

The majority of our routing is handled by dedicated hardware boxes, but we've started implementing some nix units for handling client VPN's, public access points and other relatively small things.

I didn't mean it that way. If I was a smaller business and/or upstart, I'd do it that way too as long as it was reliable.

---

### Post by juancarlospaco on 2010-01-11
> **pwnst*r said:**
> Corporations are all over virtualization and for good reason.  It saves money in the long run and it's easier to manage.

**This ^**

*Layer 2 to Layer 7 are already Virtualized, Layer 8 is the most problematic :)*

---

### Post by pricetech on 2010-01-11
> **pwnst*r said:**
> Not even close to being the same thing.  Corporations are all over virtualization and for good reason.  It saves money in the long run and it's easier to manage.

I'm not suggesting that virtualization and thin clients are the same.  I'm just saying the fuss over one reminds me of the other.

Only time will tell just how viable, and permanent, virtualization becomes.

---

### Post by KiwiNZ on 2010-01-11
> **pwnst*r said:**
> Cisco - super reliable, great support, wide variety of hardware.  Yes it's expensive, but when it comes to your network hardware usually things are not cheap anyway.

Hit the nail on the head.

---

### Post by PryGuy on 2010-01-12
Anyway, I think it all boils down to the system administrator's skills. I'm pretty sure crappy sysadmin can spoil everything even on Cisco. :)

---

### Post by pwnst*r on 2010-01-12
> **PryGuy said:**
> Anyway, I think it all boils down to the system administrator's skills. I'm pretty sure crappy sysadmin can spoil everything even on Cisco. :)

And the greatest administrator's skillsets won't prevent premature hardware failure and zero to lacking support for said hardware.

---

### Post by Icehuck on 2010-01-12
> **pwnst*r said:**
> And the greatest administrator's skillsets won't prevent premature hardware failure and zero to lacking support for said hardware.


If I tell my Cisco rep that one of my switches died, I have a new switch sent to me, no questions asked.

---

### Post by pwnst*r on 2010-01-12
> **Icehuck said:**
> If I tell my Cisco rep that one of my switches died, I have a new switch sent to me, no questions asked.

Maybe you missed my point. Dunno.

---

### Post by steeleyuk on 2010-01-12
> **Icehuck said:**
> If I tell my Cisco rep that one of my switches died, I have a new switch sent to me, no questions asked.

Which was the source of a criminal lawsuit a few years ago. A guy working for a tech company who used Cisco repeatedly requested parts, which Cisco just sent out. Turns out he was selling them on the side and making lots of money. I know he got a few years in jail...

Another [more recent]("http://www.channelregister.co.uk/2009/10/16/cisco_parts/") story.

---

### Post by PryGuy on 2010-01-12
And I try to sell my Linux servers hard... But that's just the way things are in my country I hope...;)

---

### Post by Icehuck on 2010-01-12
> **steeleyuk said:**
> Which was the source of a criminal lawsuit a few years ago. A guy working for a tech company who used Cisco repeatedly requested parts, which Cisco just sent out. Turns out he was selling them on the side and making lots of money. I know he got a few years in jail...

Another [more recent]("http://www.channelregister.co.uk/2009/10/16/cisco_parts/") story.

Part of your support contract requires that you send the parts back.

> **pwnst*r said:**
> Maybe you missed my point. Dunno.

I was just showing an example of good support.

---

### Post by pwnst*r on 2010-01-12
> **Icehuck said:**
> 

I was just showing an example of good support.

K, I was just making sure you didn't think I was saying they (Cisco) *didn't* have good support.  They'll send something overnight.

---

### Post by pricetech on 2010-01-14
> **Icehuck said:**
> I was just showing an example of good support.

Which is another point to consider.  Not only will it probably not break, but what if it does ??

---

