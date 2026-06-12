---
title: "Comcast is sniffing for routers on RCA DCM425"
date: 2008-08-21
forum: The Cafe
---

### Post by Dremora on 2008-08-21
I just thought I'd mention this here so it can get Google'd in case anyone else has this problem.

After resetting my RCA DCM425 modem today, I could not get connected to the internet unless I ran a ethernet cable from one of my computers to the modem itself.

I almost thought my router was having trouble, but after resetting everything to default settings, it still wouldn't work, so I tried my older Linksys 802.11b router, and no good either.

So I went into the setup page on my DD-WRT firmware on my WRT54G, and cloned the MAC address of one of my PCs, and pinged the modem at 192.168.100.1 a few dozen times, and it has worked since.

I also noticed a new section on the modem's diagnostic page:

Computers Permitted By Service Provider: 1

Computers Detected: 1

So I believe they have some sort of a way of sniffing for a list of router MAC addresses and shutting them out, so they can upsell you to a router modem, which costs $12.99 a month to rent instead of $3.

---

### Post by SunnyRabbiera on 2008-08-21
Huh, well if you have other computers in the house did you let them know you have a network?
I have the same model of modem myself, no issues here

---

### Post by Lord Xeb on 2008-08-21
Is this illegal?

---

### Post by Dremora on 2008-08-21
It looks like the service agreement has actually been like this for a while.

Still, thats a pretty lousy thing to do to get another $10 out of people every month.

---

### Post by Dremora on 2008-08-21
> **Lord Xeb said:**
> Is this illegal?

Oh probably not...

Good old Comcast, a million and one ways to turn you upside down and shake while seeming to have reasonable prices.

---

### Post by Loaded.len on 2008-08-21
Service agreement or not.  I pay for a certain amount of bandwidth up/down per month.  I should be able to connect as many internal computers as I want. If Shaw pulled that on me, I'd switch providers.

---

### Post by Rubberducky on 2008-08-21
Well to get around it just run the internet through 1 computer and broadcast it to your others.

---

### Post by pparks1 on 2008-08-21
The comcast cable modem is only going to see 1 MAC address when you connect your router.  It will only see the MAC address associated with your WAN interface on the router.   

Sometimes the cable modems will only bind with 1 device after power-on.  You can often solve this by powering both down, bringing up the modem and then the router or computer.

I know of no internet provider which doesn't allow routers.   They will however rent equipment to those who don't know that they can easily do it themselves.  They certainly won't support your router, and will often blame the router for problems....but they will allow them.    Seriously, they are good firewalls since they provide basic NAT translation and stop a would be nefarious user from gaining direct access to a PC.

---

### Post by Dremora on 2008-08-21
> **pparks1 said:**
> The comcast cable modem is only going to see 1 MAC address when you connect your router.  It will only see the MAC address associated with your WAN interface on the router.   

Sometimes the cable modems will only bind with 1 device after power-on.  You can often solve this by powering both down, bringing up the modem and then the router or computer.

I've tried 3 PC's, an XBOX 360, and a PS2, they all were allowed to get on the internet.

I tried 2 routers, and it blocked both of them til I changed the MAC address.

---

### Post by SunnyRabbiera on 2008-08-21
> **Dremora said:**
> Oh probably not...

Good old Comcast, a million and one ways to turn you upside down and shake while seeming to have reasonable prices.

Well for me the options in the area is... well I have none, all the alternative cable comanies are gone and the only other thing in the area is verizon DSL... that I will never use again in a million years.
Big business has no ethics, they dont care as they are in control.
But one day, one day things can change....

---

### Post by pparks1 on 2008-08-21
How would they know the device type from the MAC address.  They will know the vendor based on part of it...but brands like Linksys, netgear and Dlink make both cards and routers.

Seriously, if you hook up a computer with 2 network cards and then configure the machine as a proxy to the internet, you could plug in any number of machines and Comcast would know no better.   I don't see any advantage to them of trying to curb router use.

---

### Post by LookTJ on 2008-08-21
I have Comcast and I too also had to clone one of the PCs MAC address. I think it's stupid that Comcast does this kind of stuff.

---

### Post by SunnyRabbiera on 2008-08-21
> **Taylor said:**
> I have Comcast and I too also had to clone one of the PCs MAC address. I think it's stupid that Comcast does this kind of stuff.

yes but those who have the power can do as they wish... until the bloody revolution comes of course.

---

### Post by pparks1 on 2008-08-21
Well, I'm looking through the forums here and not seeing overwhelming outrage.   
[http://www.dslreports.com/forum/comcast](http://www.dslreports.com/forum/comcast)

Honestly, I wouldn't use the internet without going through my hardware based router/firewall.

---

### Post by mce230 on 2010-01-23
I can verify this behaviour, but only on the new RCA DCM425 modems.  I have an old Motorola modem and I have never had a problem connecting a wireless router.  My sister just signed up w/ Comcast and got the RCA modem.  It will connect to any computer, but we tried three different brands of wireless routers with no luck.  Only after I cloned my PC's MAC onto the router would they work (this worked with two different routers that did not work before the cloning.)  Also, Comcast tech-support is completely clueless on this.  My sister spent hours on the phone with them before I came, and they had no idea what was going on.  They even sent her a new wireless router for free, thinking that it would work (and it does, now that I've cloned the MAC address.)   This is definitely a dirty trick.  :(

---

