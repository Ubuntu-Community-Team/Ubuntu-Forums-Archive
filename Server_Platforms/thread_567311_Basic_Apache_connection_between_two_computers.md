---
title: "Basic Apache connection between two computers"
date: 2007-10-04
forum: Server Platforms
---

### Post by mschersten on 2007-10-04
So, I'm hoping this will get a really simple answer.  I PROMISE I've surfed for an explanation, but everything's quite a bit more complicated than I need.

First: I'm new to networking, and still educating myself on how a lot of this works.  I'm not really looking for that education here, just an easy solution to let me do what I'm trying to do, but hey, wax poetic if you like, and I'll grok what I can.

I'm trying to test some open source retail POS software using my home computer and a spare box.  The software works with a cash register lane on one box, and the backend on another.  Both computers are servers.  The lane is using Feisty, and the backend is running Dapper Xubuntu.  Both have AMP, and both have a single ethernet port.  My main computer is connected to the internet via the single ethernet out on a cable modem, using dhcp.

So... What I would like to do is disconnect the internet, connect the two computers via ethernet, and browse to each other's Apache servers.  It would be nice if I can set this up without having to change everything back when I'm done testing and ready to get back onto the internet.

I think I want to set this up through System > Administration > Network.  It really doesn't matter if I have to browse to an IP or a computer name, either would be cool.

Again, I'm pretty green with networking, so it would be nice if you could be pretty specific about exactly where I should be filling in info.

Thanks!

---

### Post by MJN on 2007-10-04
There are, as always, a few options - here are a few that spring to mind:

1. Connect both machines to a 'home router' - the type you would use to share an Internet connection - these will have a built-in DHCP server hence the whole setup will work out of the box without any reconfiguration and be ready to plug back into the normal configuration without change/delay. Of course, it'll cost you a router...

2. Connect the machines together with a crossover Ethernet cable (this is a particular type that allows a direct connection between two network cards) and configure a static address at each end (I know you said you wanted to minimise reconfiguration but this may be acceptable).

3. Connect the machines together via a hub - on crossover cables required (just standard) however again you'd need to configure static addresses given the presumption that neither machine currently provides a DHCP server.

I'll leave other options (perhaps easier, cheaper, unconventional etc) to others but this might get you started.

I'd personally go for the router option - cheap as chips yet very simple to use and handy to have around (for exactly this type of thing and more besides). Furthermore, you could use it to share your current Internet connection with other machines should this be of use.

Mathew

---

### Post by mschersten on 2007-10-04
Thanks, Mathew.

I'm really not looking to buy anything new.  This is not something critical, really just me playing with software at home.  Regarding the cable, is the ethernet cable hooked up to my cable modem likely not a crossover cable?  I have a few others lying around, is there a way to tell visually if they will work?

I know I'll have to set a static IP, and here's what I'm hoping would work:   If I go to System > Administration > Network, it gives me the option of creating multiple locations.  Can I set one ("home") to dhcp, and create a new one ("lane" and "backend") with the static IP that I switch to just for my testing?  If so, under Wired Connection > Properties, do I need to fill in just IP Address, Subnet Mask, Gateway Address, or all three?

---

### Post by MJN on 2007-10-04
> **mschersten said:**
> Thanks, Mathew.

I'm really not looking to buy anything new.  This is not something critical, really just me playing with software at home.  Regarding the cable, is the ethernet cable hooked up to my cable modem likely not a crossover cable?  I have a few others lying around, is there a way to tell visually if they will work?

It won't be a crossover cable - they are only used when conecting two so-called 'terminal devices' directly together e.g. two computers, as opposed to say a computer and a hub, or a computer and a modem, etc.

> I know I'll have to set a static IP, and here's what I'm hoping would work:   If I go to System > Administration > Network, it gives me the option of creating multiple locations.  Can I set one ("home") to dhcp, and create a new one ("lane" and "backend") with the static IP that I switch to just for my testing?  If so, under Wired Connection > Properties, do I need to fill in just IP Address, Subnet Mask, Gateway Address, or all three?

I'm not familiar with the 'locations' aspect but, yes, it sounds like it would suffice. All you'd need to configure is the IP addresses (say 192.168.0.1 and 192.168.0.2) and subnet (255.255.255.0).

It's worth trying your (standard) cable anyway as you may be lucky and have a network card that can automatically perform the crossover function without the special cable.

Mathew

---

### Post by mschersten on 2007-10-04
Ok, I think I've got it now.  It looks like it's just the cable that's the problem.  Maybe I'll look at a router w/ wireless for when the laptop's ready.  Thanks for all your help!

---

### Post by MJN on 2007-10-04
Have you tried your standard cable? It's worth a shot!

(note that a cheap hub would suffice - check eBay as they cost practically nothing)

Mathew

---

