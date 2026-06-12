---
title: "Firewall question"
date: 2010-01-21
forum: Security
---

### Post by Rayve on 2010-01-21
[LEFT]I've been doing a lot of reading lately (yay!) on security and servers and the like, and I read about Smoothwall Express, the open source option for the Smoothwall Firewall.  I already have a Linksys router (which can't be DD-WRT'd, I checked), so my question is: which is better/more secure?  Should I buy a low-end system and make it into a firewall, or is my current router enough?  Or should I just buy a DD-WRT compatible router and go that route?

As an aside, if I were to create a system solely to be a firewall, where does that go in my setup?  Does my router go behind it, too?

Thanks!
[/LEFT]

---

### Post by ontherooftop on 2010-01-21
A router is good enough you are safe with a router from 
internet attacks. Besides linux has a built in firewall
running, you can turn it off by downloading a program
called firestarter in synaptic, this is not a firewall
but a program that monitors the built in firewall in
linux and also you can open ports for certain things
like torrents or gaming with this program or you can
even just turn it off since you have a router.

---

### Post by zollie on 2010-01-21
a linksys router DOES come with a firewall built in already. Of course it's not as feature rich as Smoothwall and others.

For basic needs, a linksys router should be fine.

For more advanced needs, something like Astaro or Smoothwall (SOHO needs, for example) would be necessary.


> **Rayve said:**
> [LEFT]I've been doing a lot of reading lately (yay!) on security and servers and the like, and I read about Smoothwall Express, the open source option for the Smoothwall Firewall.  I already have a Linksys router (which can't be DD-WRT'd, I checked), so my question is: which is better/more secure?  Should I buy a low-end system and make it into a firewall, or is my current router enough?  Or should I just buy a DD-WRT compatible router and go that route?

As an aside, if I were to create a system solely to be a firewall, where does that go in my setup?  Does my router go behind it, too?

Thanks!
[/LEFT]

---

### Post by pricetech on 2010-01-21
In most cases, the firewall in your router should be sufficient.  There are sites that will test your firewall for you.  You want your router to be invisible to the outside world.  No closed ports, and certainly no open ports.

If your router does happen to have an unwanted closed or open port you can always port forward to a black hole.  (I reserve xxx.xxx.xxx.250 as my black hole address)

---

