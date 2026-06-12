---
title: "Ubuntu as firewall (Smoothwall)"
date: 2007-11-12
forum: Server Platforms
---

### Post by N8MAN1068 on 2007-11-12
Here's what I'm looking to do.
I have an old box that I was going to install Smoothwall on as my primary firewall/router appliance. It doesn't look like, as of yet, that I can use a wireless nic as the main "purple" nic to act as a WAP and serve DHCP requests.

So, my question is....can Ubuntu Server Edition handle being multi homed?
It'll need to handle a nic for the broadband connection, a nic to handle the lan connection, and a pci wireless nic to act as a WAP...the wireless nic will also need to be able to provide DHCP.

Also looking into if openSuSe can do this. Not really caring on what distro I'm using for this purpose, as long as I can get it all to work.

---

### Post by intelligentfool on 2007-11-12
while i've never tried to do what your talking about, i dont see why putting each interface on a seperate subnet would be an issue. just set each address to static, start/setup up your dhcpd and you should be good, no?

---

### Post by HermanAB on 2007-11-12
Abshlooly yes, any Linux (except maybe DSL or Puppy) can do it.

See the Advanced Routing Howto on tldp.org for details.

Cheers,

Herman

---

### Post by Jolly-Swagman on 2007-11-15
Then why not just install Smoothwall Firewall, with RED, GREEN, ORANGE, PURPLE interfaces, much easier.

See sig for link --

---

